# Reading

## Django Forms

- how to work with HTML Forms in Django, and, in particular, the easiest way to write forms to create, update, and delete model instances.

- Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site request forgery protection.

- Developers need to write HTML for the form, validate and properly sanitize entered data on the server (and possibly also in the browser), repost the form with error messages to inform users of any invalid fields, handle the data when it has successfully been submitted, and finally respond to the user in some way to indicate success

- The form is defined in HTML as a collection of elements inside <form>...</form> tags, containing at least one input element of type="submit

``` python
<form action="/team_name_url/" method="post">
    <label for="team_name">Enter name: </label>
    <input id="team_name" type="text" name="name_field" value="Default name for team.">
    <input type="submit" value="OK">
</form>
```

- The field's type attribute defines what sort of widget will be displayed
- The name and id of the field are used to identify the field in JavaScript/CSS/HTML
- value defines the initial value for the field when it is first displayed
- matching team label is specified using the label tag, with a for field containing the id value of the associated input.
- action: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
- method: The HTTP method used to send the data: post or get
- POST method should always be used if the data is going to result in a change to the server's database because this can be made more resistant to cross-site forgery request attacks.
- GET method should only be used for forms that don't change user data (e.g. a search form). It is recommended for when you want to be able to bookmark or share the URL.

![process flowchart of how Django handles form requests](../assets/form_handling_-_standard.png)

### Bookmark/Skim

[x] [Review/Skim: Django Templates](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Home_page)
[x] [Review/Skim: Django Views](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Generic_views)