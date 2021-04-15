# Readings: React 3

## Nextjs

> Next.js can serve static assets, like images, under the top-level public directory. Files inside public can be referenced from the root of the application similar to pages.

> The public directory is also useful for robots.txt, Google Site Verification, and any other static assets.

> To get a picture:
1. Download your picture in .jpg format
2. Create an images directory inside of the public directory.
3. Save the picture as profile.jpg in the public/images directory.
4. The image size can be around 400px by 400px.
5. You may remove the unused SVG logo file directly under the public directory.

> next/image is an extension of the HTML <img> element, evolved for the modern web

> Instead of optimizing images at build time, Next.js optimizes images on-demand, as users request them

> Images are lazy loaded by default. That means your page speed isn't penalized for images outside the viewport. Images load as they are scrolled into viewport

> Notice that <Head> is used instead of the lowercase <head>. <Head> is a React Component that is built into Next.js. It allows you to modify the <head> of a page.

> open the file you want to import into and  and add an import for Head from next/head at the beginning of the file:

``` javascript
import Head from 'next/head'
```

> update the imported component to include something like Head:

``` javascript
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </>
  )
}
```

> Next.js has built-in support for CSS and Sass which allows you to import .css and .scss files.

> Let’s create a Layout component which will be shared across all pages!

> Create a top-level directory called components.
Inside components, create a file called layout.js with the following content

``` javascript
export default function Layout({ children }) {
  return <div>{children}</div>
}
```

> Then, open pages/posts/first-post.js, add an import for the Layout component, and make it the outermost component:

``` javascript
import Head from 'next/head'
import Link from 'next/link'
import Layout from '../../components/layout'

export default function FirstPost() {
  return (
    <Layout>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </Layout>
  )
}
```

> Create a file called components/layout.module.css with the following content

``` javascript
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}
```

> Important: To use CSS Modules, the CSS file name must end with .module.css.

> To use this container class inside components/layout.js, you need to:

1. Import the CSS file and assign a name to it, like styles
2. Use styles.container as the className

``` javascript
import styles from './layout.module.css'

export default function Layout({ children }) {
  return <div className={styles.container}>{children}</div>
}
```

> This is what CSS Modules does: It automatically generates unique class names. As long as you use CSS Modules, you don’t have to worry about class name collisions

> CSS Modules are extracted from the JavaScript bundles at build time and generate .css files that are loaded automatically by Next.js.

> To load global CSS files, create a file called pages/_app.js with the following content:

``` javascript
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```

> This App component is the top-level component which will be common across all the different pages.

> In Next.js, you can add global CSS files by importing them from pages/_app.js. You cannot import global CSS anywhere else

> Where can you import global CSS files? Only inside pages/_app.js!

> create a set of utility CSS classes for typography and others that will be useful across multiple components.

> add a new CSS file called styles/utils.module.css with the following content:

``` javascript
.heading2Xl {
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingXl {
  font-size: 2rem;
  line-height: 1.3;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingLg {
  font-size: 1.5rem;
  line-height: 1.4;
  margin: 1rem 0;
}

.headingMd {
  font-size: 1.2rem;
  line-height: 1.5;
}

.borderCircle {
  border-radius: 9999px;
}

.colorInherit {
  color: inherit;
}

.padding1px {
  padding-top: 1px;
}

.list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.listItem {
  margin: 0 0 1.25rem;
}

.lightText {
  color: #666;
}
```

> Third, open components/layout.js and replace its content with the following code

``` javascript
import Head from 'next/head'
import Image from 'next/image'
import styles from './layout.module.css'
import utilStyles from '../styles/utils.module.css'
import Link from 'next/link'

const name = 'Your Name'
export const siteTitle = 'Next.js Sample Website'

export default function Layout({ children, home }) {
  return (
    <div className={styles.container}>
      <Head>
        <link rel="icon" href="/favicon.ico" />
        <meta
          name="description"
          content="Learn how to build a personal website using Next.js"
        />
        <meta
          property="og:image"
          content={`https://og-image.vercel.app/${encodeURI(
            siteTitle
          )}.png?theme=light&md=0&fontSize=75px&images=https%3A%2F%2Fassets.vercel.com%2Fimage%2Fupload%2Ffront%2Fassets%2Fdesign%2Fnextjs-black-logo.svg`}
        />
        <meta name="og:title" content={siteTitle} />
        <meta name="twitter:card" content="summary_large_image" />
      </Head>
      <header className={styles.header}>
        {home ? (
          <>
            <Image
              priority
              src="/images/profile.jpg"
              className={utilStyles.borderCircle}
              height={144}
              width={144}
              alt={name}
            />
            <h1 className={utilStyles.heading2Xl}>{name}</h1>
          </>
        ) : (
          <>
            <Link href="/">
              <a>
                <Image
                  priority
                  src="/images/profile.jpg"
                  className={utilStyles.borderCircle}
                  height={108}
                  width={108}
                  alt={name}
                />
              </a>
            </Link>
            <h2 className={utilStyles.headingLg}>
              <Link href="/">
                <a className={utilStyles.colorInherit}>{name}</a>
              </Link>
            </h2>
          </>
        )}
      </header>
      <main>{children}</main>
      {!home && (
        <div className={styles.backToHome}>
          <Link href="/">
            <a>← Back to home</a>
          </Link>
        </div>
      )}
    </div>
  )
}
```

> Finally, let's update the homepage.

``` javascript
import Head from 'next/head'
import Layout, { siteTitle } from '../components/layout'
import utilStyles from '../styles/utils.module.css'

export default function Home() {
  return (
    <Layout home>
      <Head>
        <title>{siteTitle}</title>
      </Head>
      <section className={utilStyles.headingMd}>
        <p>[Your Self Introduction]</p>
        <p>
          (This is a sample website - you’ll be building a site like this on{' '}
          <a href="https://nextjs.org/learn">our Next.js tutorial</a>.)
        </p>
      </section>
    </Layout>
  )
}
```
