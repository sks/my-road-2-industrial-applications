## What it Means to have a Manifest file

That was not a real application , yeah I cheated. :-)

Lets dig into more functionality.

## Problem Statement.

Almost every CF application has a manifest.yml, What is this ?

What is the  deal with manifest.yml ?

## Answer

Just agree, You don't build one HTML file  and ship anything, We build  micro-services talking to each other over HTTP. Each service would have dependencies, routes, memory, stacks, hostname, buildpacks, environment variables etc.. 

So where do we store them ? The answer is simple -- manifest.yml

Checkout [this pull request](https://github.com/sks/predix-sample/pull/2/files) for changes. This is a minimal manifest entry. 

No more ` cf push <APP_NAME> -b staticfile_buildpack `, just ` cf push `

If you check the [documentation](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html), there are lot of things that you can enter into your manifest.yml file.

Why don't you try changing the memory, hostname attributes, I'll leave that to you.

##### Tip: How to do it

* Edit the manifest.yml
* ` cf push `



## References

* [Cloudfoundry docs](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html)

