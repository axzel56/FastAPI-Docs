Oauth2 specifies that when using the "password flow" that we are using the client must send a `username` and `password` fields as form data.

## Scope 

The spec also says that the client can send another form field `"scope"`.

The form field is a long string with scopes separated by spaces.
They are normally used to declare specific security permissions for example:
- `users:read `or `users:write `

In OAuth2 a scope is just a string that declares a specific permission required.

It does not matter if it has other characters like `:` or if its a URL.


## Code to get the `username` and `password`

Now let's use the utilities provided by **FastAPI** to handle this.

