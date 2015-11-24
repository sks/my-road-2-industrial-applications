## Securing Server side.

* Checkout [this commit](https://github.com/sks/predix-sample/commit/4f5e5e304fb73d7d16cdfd55e8dbca113b7abca5) to get an idea on what was done.
* Changes in application.yml
```
security:
    oauth2:
        client:
            client-id: todolist-server
            client-secret: todo_server_secret
        resource:
            id: service
            userInfoUri: https://<UAA_INSTANCE_ID>.predix-uaa.run.aws-usw02-pr.ice.predix.io/userinfo
            token-info-uri: https://<UAA_INSTANCE_ID>.predix-uaa.run.aws-usw02-pr.ice.predix.io/check_token
```    
* Since [Spring Data Rest](http://projects.spring.io/spring-data-rest/) project could not protect the [PUT](http://docs.spring.io/spring-data/commons/docs/current/api/org/springframework/data/repository/CrudRepository.html#save-S-) Operation (Which meant another user could possibly update another user's resource. I ended up writing the whole Controller -> Service -> Repository Layer. Please check [this  commit ](https://github.com/sks/predix-sample/commit/4912abbab0624340797a5f4491e0d522440503a4) for details


Check [this](https://github.com/sks/predix-sample/pull/12) Pull Request For this Feature.

### References
* [Spring Boot Security Docs](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-security.html)
* [YAML Configuration in Spring](https://docs.spring.io/spring-boot/docs/current/reference/html/howto-properties-and-configuration.html#howto-use-yaml-for-external-properties)
* [Spring Hateoas Documentation](http://docs.spring.io/spring-hateoas/docs/current/reference/html/#client)
* [Richardson Maturity Model](http://martinfowler.com/articles/richardsonMaturityModel.html)
* [Spring Hateoas Sample](http://spring.io/guides/gs/rest-hateoas/)