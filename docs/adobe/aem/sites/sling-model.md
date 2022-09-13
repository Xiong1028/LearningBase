# Sling Model

Sling Models are "pure" POJOs which maps Sling objects (resources, request objects etc.). Since Sling Models are annotation-driven Plain Old Java Objects (POJOs), annotations are used a lot. They allow you to map resource properties, assign default values, inject OSGi services and much more.

```mermaid
 flowchart LR
 a[POJO Java Class] --> b[Sling API] --> |annotation model| c(Sling Model) --> |UseClass| HTL

```

## Sling model in AEM
![sling model in AEM](/assets/img/aem/component-with-sling-model.png){width=800}
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>

## Component implementation
![Component implementation](/assets/img/aem/model-implementation.png){width=800}
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>


## @Model() annotation
```java
@Model(
	adaptables = Resource.class
	adapters = InterfaceName.class
)


# `adaptables` defines which resource object can be adapted to and how the sling mode behave
# `adapters` - defined interface

```

### adaptables
```mermaid
flowchart LR
a[adaptables] --> a1[Resource.class] & a2[SlingHttpServletRequest.class] 

```


### Annotations in Sling Model
```mermaid
flowchart LR
a[Annotations in Sling Model] --> a1(["@Inject"]) --- a11[javax.inject.Inject] --- a111["Data can be specific by \n @Via" ]
a --> a2(["@Default"]) --- a21["Setup default value"]
a --> a3(["@Required"]) --- a31["The property is mandate"]
a --> a4(["@Via"]) --- a41["Setup the source of data"]
a --> a5(["@ScriptVariable"]) --- a51["Access to the global context defined in script. \n e.g. Page, Resource, Style Node"]
a --> a6(["@ValueMapValue"]) --- a61["Access to properties of JCR Node"] --- a6111["= @Inject +  @Via(resource)"]
a --> a7(["@SlingObject"]) --- a71["Access to ResourseResolver, request, \n response, slingScriptHelper"]
a --> a8(["@Self"]) --- a81["Access to adaptables object"] 
a7 --- |Also| a81
a --> a9(["@RequestAttribute"]) --- a91["Pass value into Sling model"] 
a --> a10["@ResourcePath"] --- a101["Access to jcr resource"]  --- a1011["also can be accessed by ResourceResolver \n with @SlingObject "]
a --> b11["@OSGIService <em>\n IMPORTANT!!</em>"] --- b111["Access any OSGI service \n e.g.QueryBuilder"]  --- b1111["= @Via + @source('osgi-servie')"]
a --> b12["@named"] --- b121["rename complicated properties name in model"]  --- b1211["e.g. Rename 'jcr:lastMdodifiedBy' to 'lastmodefiedBy'"]
```
