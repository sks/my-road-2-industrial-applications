# Advanced Nginx Configuration

Its time that we start configuring our nginx application to talk to the backend service and do some real data manipulation.

## Steps
* Copy over the default nginx.conf provided by the buildpack from [here](https://github.com/cloudfoundry/staticfile-buildpack/blob/master/conf/nginx.conf),  [commit](https://github.com/sks/predix-sample/commit/598bf6ca840abcefb57a709345f6137a74b72945) 
* remove unwanted lines:  [commit ](https://github.com/sks/predix-sample/commit/b5cb81e3c4f8d1d6410e47aa27c77c848c14cf55)
* Hardcod the server URL as the proxy [commit](https://github.com/sks/predix-sample/commit/712db7ae60a2af6d33d2ac0b53b30b60b28b3040)
* But Hard code won't work, the server URL may change with environment, like DEV/production/QA, So we have to externalize the configuration. [commit](https://github.com/sks/predix-sample/commit/ff88d343c745c573621fb58590d3503f8f709f41)
    * Explanation: The Static buildpack uses something called [ERB](http://www.stuartellis.eu/articles/erb/) to template the nginx.conf
    * [Reference to Buildpack code that does the erb ](https://github.com/cloudfoundry/staticfile-buildpack/blob/master/bin/boot.sh#L25)
    * So basically ` <%= ENV["TODO_SERVER_URL"] %> ` entry gets replaced into ` https://todo-server.run.aws-usw02-pr.ice.predix.io ` which happens to be the env in ` manifest.yml `
    * So now any request to ` todo-client.run.aws-usw02-pr.ice.predix.io/todo ` will be redirected to ` todo-server ` succefully
* Complete list of changes can be found in [Pull Request](https://github.com/sks/predix-sample/pull/7)


## References
* [ERB Templating](http://ruby-doc.org/stdlib-1.9.3/libdoc/erb/rdoc/ERB.html)
* [Static build pack](https://github.com/cloudfoundry/staticfile-buildpack/)
* [CF Buildpack folder structure](http://docs.cloudfoundry.org/buildpacks/custom.html)