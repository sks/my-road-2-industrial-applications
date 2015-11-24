# Talking to UAA Instace


*  Install [uaac-client](https://github.com/cloudfoundry/cf-uaac) using command ` gem install cf-uaac `
*  If you don't have `gem`  installed on your machine, Please do so. If you run into issues, Please try reading about [rvm](https://rvm.io).
*  bind the ` todo-server ` with the uaa instance created. `cf bs todo-server uaa `. Don't restart the ` todo-server ` yet.
*  do a ` cf env todo-server` and search for ` predix-uaa `. You should be able to see something like
```
    "predix-uaa": [
        {
            "credentials": {
            "issuerId": "https://<UAA_INSTANCE_ID>.predix-uaa.run.aws-usw02-pr.ice.predix.io/oauth/token",
            "uri": "https://<UAA_INSTANCE_ID>.predix-uaa.run.aws-usw02-pr.ice.predix.io",
            "zone": {
                "http-header-name": "X-Identity-Zone-Id",
                "http-header-value": "<UAA_INSTANCE_ID>"
                }
            },
            "label": "predix-uaa",
            "name": "uaa",
            "plan": "beta",
            "tags": []
        }
  ]
```
* Target ` uaac  ` to UAA Instance. `uaac target https://<UAA_INSTANCE_ID>.predix-uaa.run.aws-usw02-pr.ice.predix.io `
* Create a context with uaac ` uaac token client get admin -s <CLIENT_SECRET> ` where ` CLIENT_SECRET ` is the secret that was created [here](./creating_predix_uaa_instance.md)
    
## Tips
* Installing any managing ruby versions and gems is easier if you have [ruby-version-manager](https://rvm.io/) installed


## References
* [UAAC User Management](https://docs.pivotal.io/pivotalcf/adminguide/uaa-user-management.html) 
* [Targeting UAA Instance](https://www.predix.io/docs/?r=69728#png4X1SX)

