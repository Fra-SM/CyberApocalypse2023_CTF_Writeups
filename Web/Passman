# Passman

This challenge contained an IDOR (Insecure Direct Object Reference) vulnerability due to missing checks before allowing users to update their passwords. The following GraphQL API method allows us to update other users password:

```js
UpdatePassword: {
            type: ResponseType,
            args: {
                username: { type: new GraphQLNonNull(GraphQLString) },
                password: { type: new GraphQLNonNull(GraphQLString) }
            },
            resolve: async (root, args, request) => {
                return new Promise((resolve, reject) => {
                    if (!request.user) return reject(new GraphQLError('Authentication required!'));

                    db.updatePassword(args.username, args.password)
                        .then(() => resolve(response("Password updated successfully!")))
                        .catch(err => reject(new GraphQLError(err)));
                });
```

Intercepting and modifying the requests in Burp as below allows us to choose the new password for the admin user and login to get the flag:

![Drobots](/Screenshots/WEB_4.png)

## HTB{1d0r5_4r3_s1mpl3_4nd_1mp4ctful!!}
