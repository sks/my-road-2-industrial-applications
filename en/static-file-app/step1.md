## Creating Simple Static Content

This documentation tries to cover on strategies on pushing your static content to the cloud. This could be compared to a Hello-World sample for Cloud application.

## Problem Statement

I want to push a simple web page on to Predix.

## Solution
The code sample with the changes made can be found in [this Pull Request](https://github.com/sks/predix-sample/pull/1/files).

All you wanted was just one liner to get that whole thing working from a empty directory

```
    echo '<h1>It Works</h1>' > index.html && cf push MY_APP -b staticfile_buildpack --random-route;
```

This command should have yielded the output, ``` my-static-content ``` was the name of my application.

```

App my-static-content was started using this command `sh boot.sh`

Showing health and status for app my-static-content in org *****@**.com / space predix-sample as *******@**.com...
OK

requested state: started
instances: 1/1
usage: 1G x 1 instances
urls: my-static-content.run.aws-usw02-pr.ice.predix.io
last uploaded: Sat Nov 21 05:22:11 UTC 2015
stack: cflinuxfs2

     state     since                    cpu    memory       disk         details   
#0   running   2015-11-20 09:22:24 PM   0.0%   3.5M of 1G   5.2M of 1G      

```

If you ran into some trouble, please check [Troubleshoot](#TroubleShooting) guide below


That's it.

![Its Magic](http://m.memegen.com/q0vdjb.jpg)

## What Just happened


1. You created a index.html page with the content
2. You told CF CLI to push the content of current working directory
3. cf cli took all the content from the current directory and transferred to cloudfoundry
4. Cloudfoundry took the code that was given and used the buildpack specified with the option ` -b `, in this case, staticfile_buildpack
5. Remember this formulae, ``` code + buildpack = droplet ```
6. Cloudfoundry takes this droplet and passed on to the Droplet Execution agent (DAE)
7. DAE takes these droplet and starts running them

#TroubleShooting

* I got the following error
```
The route <APP_NAME>.run.aws-usw02-pr.ice.predix.io is already in use.
TIP: Change the hostname with -n HOSTNAME or use --random-route to generate a new route and then push again.
```
Don't worry, Its not your fault, Someone already took that hostname and now you have to live with a different one. Please read the technical note [here](http://support.run.pivotal.io/entries/79703355-Route-is-Already-in-Use).

# Refernces
* [Cloudfoundry Deploying apps](https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html)
* [CF Glossary](https://docs.cloudfoundry.org/concepts/glossary.html)