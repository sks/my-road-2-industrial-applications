# Create  Predix UAA Instance

* Create a ` predix-uaa ` instance using the command ` cf cs `
*  ` cf cs predix-uaa beta uaa -c '{"adminClientSecret":"<CLIENT_SECRET"}' `
*  Never ever forget this ` <CLIENT_SECRET> `. This is your password to talk to the UAA instance that has been created



## References
* [Getting Started with Predix UAA Instance](https://www.predix.io/docs/?r=69728#Q0CoIStl)
* [cf cs arbitary parameters](https://docs.cloudfoundry.org/devguide/services/managing-services.html#arbitrary-params-create)
