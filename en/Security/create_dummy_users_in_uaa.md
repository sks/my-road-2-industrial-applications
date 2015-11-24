## Create Dummy Users in UAA


Now that we have added client in UAA, Its time to add some Resource Owners

## Steps
* Run the following command 
```
uaac user add <my-user> --emails <my_user>@domain.com --password <my_password>
```  
For eg: 
```
uaac user add sks --emails dummyuser@noreply.com --password password
```

* Verify if the credentials work
    * Goto : ` https://<UAA_INSTANCE_ID>.predix-uaa.run.aws-usw02-pr.ice.predix.io/ ` created in [this](./creating_predix_uaa_instance.md) exercise



## References

* [Predix Docs](https://www.predix.io/docs/?r=69728#RulzoBew)
* Try `uaac help` : ` uaac help user add `
