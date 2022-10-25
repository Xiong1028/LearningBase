# Service User

*since 6.1, it allows developer or content authors to create system user from CRX explorer*

Two API to get session
```java
Session session = SlingRepository.loginAdministrative();

ResourceResolver rr = ResourceResolverFactory.getAdministrativeResourceResolver();
```

## Create and Map System User
![create system user](/assets/img/aem/osgi-service-1.png){width=600}
