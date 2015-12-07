## Registering Client in UAA

Now that we have configured UAA, Its time to create Client so that the client can get access to Resources

##Steps
* Create 2 clients with the following command

```
uaac client add todolist-client \
    --authorities "uaa.resource" \
    --scope "openid"  \
    --autoapprove "openid" \
    --authorized_grant_types implicit \
    --redirect_uri https://todo-client.run.aws-usw02-pr.ice.predix.io/callback
 ```
 
 ```
uaac client add todolist-server \
    --authorities "uaa.resource" \
    --scope "openid"  \
    --autoapprove "openid" \
    --authorized_grant_types implicit \
    --redirect_uri https://todo-client.run.aws-usw02-pr.ice.predix.io/callback
 ```
 
 
 Don't give any client secret when prompted. Just press enter.
 
 You should be seeing an output similar to the one below
 ```
  New client secret:
  Verify new client secret:
  scope: openid
  client_id: todolist-client
  resource_ids: none
  authorized_grant_types: authorization_code refresh_token
  redirect_uri: https://todo-client.run.aws-usw02-pr.ice.predix.io/callback
  autoapprove: openid
  action: none
  authorities: uaa.resource
  lastmodified: 1448133847312
  id: todolist-client
```

##Explanation
* ` --authorities ` [Documentation](https://github.com/cloudfoundry/uaa/blob/master/docs/UAA-Security.md#security-metadata). Tells what all the client has access to on. Here we have told ` uaa.resource ` which means basic User information
* ` --scope ` [Documentation](https://github.com/cloudfoundry/uaa/blob/master/docs/UAA-Security.md#token-scope-rules). Tells What are the things that the Client can do on behalf of the user.
* ` --autoapprove `. Tells the UAA that these scope should not require user approval. Hence user won't be prompted on a new screen whether the client should be given access to these scopes
* ` --authorized_grant_types ` : This is something that we should read upon. For now lets stick to implicit
* ` --redirect_uri `: Where  to redirect once successfully logged in
* Why 2 clients ?
    *  In a micro-service world, you don't want to use one client's credentials in another one. In this case ` todo-client ` and ` todo-server `. Keep them separate

##References

* ` uaac help client add `
* [Cloudfoundry UAA Features](https://www.cloudfoundry.org/high-level-features-of-the-uaa/)
* [OAuth2 Authorization](http://tutorials.jenkov.com/oauth2/authorization.html#authorization-grant)