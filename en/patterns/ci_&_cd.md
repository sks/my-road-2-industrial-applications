## Continous Integration & Continous Deployment

Though its fairly easy to push your applications to Cloudfoundry, No one would wants to do it manually every time a change has been pushed to ` develop ` or ` master ` branch. No one likes a broken build


![
](http://s.quickmeme.com/img/e3/e3cff629826455f00a5f94e29d00aa0725e1a1266e83db81b0aebcef03a61eff.jpg)

## Problem Statement
How do I push my code to CloudFoundry on every commit to specific branch ?

## Choices
We have a lot of readily available solutions over Internet. I'm looking at [Jenkins](https://jenkins-ci.org/), [Cloudbees](https://www.cloudbees.com/), [Codeship](https://codeship.com) etc..

Of these , I loved [Codeship](https://codeship.com) very much , Offering more flexible [plans & pricing](https://codeship.com/pricing) that  fits my budget. 

Its free build for public repo's , So huge money saver.

##Steps
* Checkout [this commit](https://github.com/sks/predix-sample/commit/e8701d7644161f120782b4d54aa71edee1a1b1cc)
* Copy over the [` ci-deploy.sh `](https://gist.githubusercontent.com/sks/c500328d3a0710543182/raw/5888f0f22c25f3904ee15abf1ce710f51a674cb0/ci-deploy.sh)  from [this gist](https://gist.github.com/sks/c500328d3a0710543182) and replace `<APP_NAME>` with your applications name

* [Optional] Create an account in [Codeship](https://codeship.com) and add test configuration and deployment configuration

* Checkout ` ci-deploy.sh`. usage example `./ci-deploy.sh -b <BUILD_NUMBER> `
* If setting up deployment, The script that I've in place for predix-sample is
    ```
    cf login -a https://api.system.aws-usw02-pr.ice.predix.io -u ******@****.com -p <YOUR_PASSWORD> -o <YOUR_ORG> -s predix-sample
    cd static-file-app;
    ./ci-deploy.sh  -b $CI_BUILD_NUMBER
    cd -;
    cd java-backend/todo-service/;
    ./ci-deploy.sh -b $CI_BUILD_NUMBER
    ```
This makes sure that on any commit to master branch, both the static-content and  java-backend is pushed to Cloudfoundry
##Tips
* Check if you already have a CI tool available in your company
* `ci-deploy.sh ` use [Blue Green Deployment](https://docs.pivotal.io/pivotalcf/devguide/deploy-apps/blue-green.html)

## References
* [Blue Green Deployment](https://docs.pivotal.io/pivotalcf/devguide/deploy-apps/blue-green.html)