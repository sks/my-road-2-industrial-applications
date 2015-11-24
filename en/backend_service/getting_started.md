## Creating & Pushing a Java MicroService

What would it take to create a Java backend service hosted on Predix ?

## Answer

Its just a couple of clicks away, without even having to right any code.

## Steps

* Go to [start.spring.io](http://start.spring.io/)
* Enter ` Group ` information , For me I entered ` com.sks.predix.sample `
* Enter ` artifact ` info , I entered ` todo-service ` as I'll be writing a backed to store the to-do frontend developed in [the other chapter](https://sks.gitbooks.io/my-road-2-industrial-applications/content/static-file-app/step3.html)
* Select the required dependencies , For me I am interested in [Web](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/html/howto-embedded-servlet-containers.html) , [Actuator](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/html/production-ready.html), [JPA](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/html/boot-features-sql.html) and [h2](http://www.h2database.com/html/main.html) for now
* Click on Generate Project to start downloding the zip
* Open the zip and the resulting folder is your application
* Checkout [this commit](https://github.com/sks/predix-sample/commit/4eef5dd859eb19f8b43603b512987d10dc0ca9e5) for details on how the project looks like
* Try running ` mvn  spring-boot:run ` and goto http://localhost:8080/env
* This  should open up the [Spring Actuator](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/html/production-ready.html) which is really helpful in checking out the application container properties and couple of other parameters which will be covered later
* Time to add [manifest.yml](https://sks.gitbooks.io/my-road-2-industrial-applications/content/static-file-app/step2.html) to set properties for the project. checkout [this commit](https://github.com/sks/predix-sample/commit/a95ff1e6337d451e895ec6128b3d4b2a17e22f88)
* Its time to ` cf push `
* Once pushed, checkout the app in Cloud , by going to https://todo-server.run.aws-usw02-pr.ice.predix.io/env, Change ` todoservice ` with whatever entry you have given for your hostname in the manifest.yml


## Tips

* At any time if you want to see what your application is doing, just type ` cf logs <APP_NAME> ` , for eg: ` cf logs todo-service `

## References

* [Spring Boot Maven Plugin](http://docs.spring.io/spring-boot/docs/current/maven-plugin/index.html)
* [Spring Actuator](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/html/production-ready.html)
* [Documentation on Manifest.yml file ](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html)
* [Log Management](https://docs.cloudfoundry.org/devguide/services/log-management.html)