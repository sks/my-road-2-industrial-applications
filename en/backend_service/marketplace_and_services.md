## Marketplace & Service Instances

We never run production code against H2 Database, We need some NoSql/RDBMS Solutions like Cassndra/MongoDB/Oracle/Mysql/Postgres etc...


## The Problem Statement

How do I provision a service to my space.


## Steps

1. On the terminal , type in ` cf m ` 
2. You will get the listing of all the services that you would be able to create. 
3.  I'm interested in a postgres instance
    ```
    postgres                   shared, shared-nr   Reliable PostgrSQL Service   

    ```
4. To get more details about a service type in `cf marketplace -s <SERVICE_NAME>`, For example ` cf marketplace -s postgres `
    ```
    Getting service plan information for service postgres as *******@**.com...
    OK

    service plan   description                                                     free or paid   
    shared         A Reliable PostgreSQL database on a shared server.              free   
    shared-nr      A PostgreSQL database with no replication on a shared server.   free   

    ```

5. So how do I go about creating an Postgres instance
    ```
        cf cs postgres shared-nr database
    ```
6. Time to bind the Postgres instance to our ` todo-service ` service.
    * There are 2 ways this can be done
        * Using cf-cli : ` cf bs <APP_NAME> <SERVICE_INSTANCE_NAME> `, For eg: ` cf bs todo-service database`
        * Using manifest.yml [services block](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#services-block)
    * I prefer the second method. Checkout [this commit](https://github.com/sks/predix-sample/commit/c3b6226713fbd74ee0e626b01686e45c9b32b27c) for details
7. Create some entity and RestResource, Check [this commit](https://github.com/sks/predix-sample/commit/055662c7f3e6500a5e44e3cd5879dcae92e70d1f) for details
8. So as to follow the [12factor Admin process](http://12factor.net/admin-processes), I'm using [flyway](http://flywaydb.org/) to make migrations easier, [Check this commit](https://github.com/sks/predix-sample/commit/db9431ed4d8eb2a38433f438ffc41de544beeb90) for details
9. Time for ` mvn clean install && cf push  `


## Tips

* For help on any command in cf-cli, type in ` cf help <COMMAND>`, for eg: ` cf help cs ` , `cf help m`
* If a service is bound to an application, you need to restage the application using ` cf restage <APP_NAME> ` command
* Flyway is not database agnostic
* Make sure that you turn off any ddl operation by [hibenate](http://hibernate.org/)  by setting ` spring.jpa.generate-ddl=false `
* Checkout [Hibernate Licensing](http://hibernate.org/community/license/) to make sure you don't get into trouble later.


## References
* [Managing Services](http://docs.cloudfoundry.org/devguide/services/managing-services.html)
* [Flyway configuration](https://docs.spring.io/spring-boot/docs/current/reference/html/howto-database-initialization.html#howto-execute-flyway-database-migrations-on-startup)
* [Spring RestResource](http://docs.spring.io/spring-data/rest/docs/current/api/org/springframework/data/rest/core/annotation/RestResource.html)
* [REST Hateoas](https://spring.io/guides/gs/rest-hateoas/)