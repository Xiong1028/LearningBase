# OSGI Service

> 
- How to write OSGI serice and Service concepts.
- How to call serice in Sling Model and other Services/Components

## Writing Service

### Service Annotations
![service annotation](/assets/img/aem/osgi-service-2.png){width=800}

### How does a service work 
![How does a service work](/assets/img/aem/osgi-service-3.png){width=800}


<details>
<summary>Demo</summary>
```java

@Component(service = GetTitleService.class, immediate = true)
public class GetTitleServiceImpl implements GetTitleService {

	private static final Logger LOG = LoggerFactory.getLogger(GetTitleServiceImpl.class);

	private ResourceResolverFactory resourceResolverFactory;

	//When Reference annotation is disallowed on fields, the solution is following
	@Reference
	public void bindResourceResolverFactory(ResourceResolverFactory resourceResolverFactory) {
		this.resourceResolverFactory = resourceResolverFactory;
	}

	@Reference
	public void unbindResourceResolverFactory(ResourceResolverFactory resourceResolverFactory) {
		this.resourceResolverFactory = resourceResolverFactory;
	}

	@Override
	public String getTitle() {
		try {
			//get ResourceResolver
			@SuppressWarnings("deprecation")
			ResourceResolver resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
	   // get Resource
			Resource resource = resourceResolver.getResource("/content/htlblog/author");

			// get property  using adaptTo(), can also using getValueMap();
			ValueMap valueMap = resource.adaptTo(ValueMap.class);
			String title = valueMap.get("title", String.class);

			return title;
		} catch (Exception e) {
			LOG.info("\n Login Exception {} ", e.getMessage());
			return "error";
		}
	}
}

```
</details>


## Multiple Service Implementation
![Multiple service](/assets/img/aem/multi-service-call.png){width=800}

![Multiple service](/assets/img/aem/multi-service-call-2.png){width=800}

<details>
<summary>demo</summary>
```java
//service
@Component(service = MultiService.class,immediate = true,name = "serviceA")
@ServiceRanking(1000)
public class MultiServiceAImpl implements MultiService{
    private static final Logger LOG= LoggerFactory.getLogger(MultiServiceAImpl.class);


    @Override
    public String getName() {
        return "MultiServiceAImpl";
    }
}

```
```java
//model 
@Model(adaptables = SlingHttpServletRequest.class,
adapters = ServiceDemo.class,
defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL)
public class ServiceDemoImpl  implements ServiceDemo {
		...
    @OSGiService(filter = "(component.name=serviceA)")
    MultiService multiService;

    @OSGiService(filter = "(component.name=com.aem.geeks.core.services.impl.MultiServiceBImpl)")
    MultiService multiServiceB;

    @Override
    public String getNameFromService() {
        return multiService.getName();
    }

    @Override
    public String getNameFromServiceB() {
        return multiServiceB.getName();
    }

		...
}
```
</details>
