# Reading

## Next.js - Dynamic Routes

> each page path depends on external data

>  create dynamic routes for blog posts:

1. We want each post to have the path /posts/<id>, where <id> is the name of the markdown file under the top-level posts directory.
2. Since we have ssg-ssr.md and pre-rendering.md, we’d like the paths to be /posts/ssg-ssr and /posts/pre-rendering.

> First, we’ll create a page called [id].js under pages/posts. Pages that begin with [ and end with ] are dynamic routes in Next.js.

> In pages/posts/[id].js, we’ll write code that will render a post page — just like other pages we’ve created.

``` javascript
import Layout from '../../components/layout'

export default function Post() {
  return <Layout>...</Layout>
}
```

> We’ll export an async function called getStaticPaths from this page. In this function, we need to return a list of possible values for id

``` javascript
import Layout from '../../components/layout'

export default function Post() {
  return <Layout>...</Layout>
}

export async function getStaticPaths() {
  // Return a list of possible value for id
}
```

> we need to implement getStaticProps again - this time, to fetch necessary data for the blog post with a given id. getStaticProps is given params, which contains id (because the file name is [id].js).

``` javascript
import Layout from '../../components/layout'

export default function Post() {
  return <Layout>...</Layout>
}

export async function getStaticPaths() {
  // Return a list of possible value for id
}

export async function getStaticProps({ params }) {
  // Fetch necessary data for the blog post using params.id
}
```

> Implement getStaticPaths

1. Create a file called [id].js inside the pages/posts directory.
2. Also, remove first-post.js inside the pages/posts directory — we’ll no longer use this.
3. open pages/posts/[id].js and do this code:

``` javascript
import Layout from '../../components/layout'

export default function Post() {
  return <Layout>...</Layout>
}
```

4. in lib/posts.js and add the following getAllPostIds function at the bottom

``` javascript
export function getAllPostIds() {
  const fileNames = fs.readdirSync(postsDirectory)

  // Returns an array that looks like this:
  // [
  //   {
  //     params: {
  //       id: 'ssg-ssr'
  //     }
  //   },
  //   {
  //     params: {
  //       id: 'pre-rendering'
  //     }
  //   }
  // ]
  return fileNames.map(fileName => {
    return {
      params: {
        id: fileName.replace(/\.md$/, '')
      }
    }
  })
}
```

5. import the getAllPostIds function and use it inside getStaticPaths. Open pages/posts/[id].js 

``` javascript
import { getAllPostIds } from '../../lib/posts'

export async function getStaticPaths() {
  const paths = getAllPostIds()
  return {
    paths,
    fallback: false
  }
}
```

6. paths contains the array of known paths returned by getAllPostIds(), which include the params defined by pages/posts/[id].js. Learn more in the paths key documentation

> We need to fetch necessary data to render the post with the given id.

To do so, open lib/posts.js again and add the following getPostData function at the bottom. It will return the post data based on id:

``` javascript
export function getPostData(id) {
  const fullPath = path.join(postsDirectory, `${id}.md`)
  const fileContents = fs.readFileSync(fullPath, 'utf8')

  // Use gray-matter to parse the post metadata section
  const matterResult = matter(fileContents)

  // Combine the data with the id
  return {
    id,
    ...matterResult.data
  }
}
```

> pages/posts/[id].js and replace this line:

``` javascript
import { getAllPostIds } from '../../lib/posts'
```

> with this:

``` javascript
import { getAllPostIds, getPostData } from '../../lib/posts'

export async function getStaticProps({ params }) {
  const postData = getPostData(params.id)
  return {
    props: {
      postData
    }
  }
}
```

> update the Post component to use postData. In pages/posts/[id].js replace the exported Post component with the following code:

``` javascript
export default function Post({ postData }) {
  return (
    <Layout>
      {postData.title}
      <br />
      {postData.id}
      <br />
      {postData.date}
    </Layout>
  )
}
```


## Next.js - Deployment

> go to https://vercel.com/signup to create a Vercel account. Choose Continue with GitHub and go through the sign up process.

> Import your nextjs-blog repository

> When it’s done, you’ll get deployment URLs. Click on one of the URLs and you should see the Next.js starter page live

> Vercel is made by the creators of Next.js and has first-class support for Next.js.

> Next.js can be deployed to any hosting provider that supports Node.js.

> your package.json file should have this:

``` javascript
{
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start"
  }
}
```

> In your own hosting provider, run the build script once, which builds the production application in the .next folder.

> npm run build

> After building, the start script starts a Node.js server that supports hybrid pages, serving both statically generated and server-side rendered pages, and API Routes.

> npm run start