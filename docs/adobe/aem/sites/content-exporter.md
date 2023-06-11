# AEM Content Exporter Service

_Sling Model Exporter_

- since 6.3, AEM provides content exporter service to export json or xml to headless application.
- AEM provides an OTTB content exporter - jackson
- By default, AEM outputs all properties in json format by NodeName.json

```mermaid
flowchart LR

a[AEM Author] -->|json or xml| b(Android) & c(iOS) & d(Third Party)

```

![sling model content exporter flow](/assets/img/aem/sling-model-exporter-request-flow.png){width=500}

<p><sup>- image from <a href="https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-sling-model-exporter.html?lang=en" target="_blank">adobe</a></sup></p>

## How to make a sling model as an Exporter?

![content exporter](/assets/img/aem/content-exporter-1.png)

<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>

> - If the selector is not provided, AEM'll provide a default selector called "model". selector property is optional.

- resourceType should be the same as resourceType of the content node.

## Content Exporter Annotations

```mermaid
flowchart LR

a[Content Exporter Annotations] --> a1("@Exporter") --- a11("Make a sling mode to content exporter service")
a --> a2("@JsonProperty(value='xxx')") --- a21("Rename the key in outputed json")
a --> a3("@JsonIgnore") --- a31("Skip content in outputed json")
a --> a4("@JsonRootName('xxx')") --- a41("wrap outputed object in a root")
```

## Custom Sling Model Exporter

```mermaid
classDiagram
direction LR
ModelExporter <|-- CustomExporter : implements
class ModelExporter{
  +isSupported()
  +export()
  +getName()
}

class CustomExporter{
  +isSupported()
  +export()
  +getName()
}
```

### How to create a custom Exporter?

<details>
<summary>Step 1 - Create a new Exporter service implements ModelExporter</summary>

<p class="call-out-2"><a href="https://www.javatpoint.com/jaxb-tutorial" target="_blank">JAXB</a> is used for XML</p>

```java
@Component(service = ModelExporter.class)
public class XmlExporter implements ModelExporter {
  @Override
  public boolean isSupported(Class<?> clazz) {
    return true;
  }

  @Override
  public <T> T export(Object model, Class<T> clazz, Map<String, String> options) throws ExportException {
    ....
  }

  @Override
  public String getName() {
    return "customExporterName";
  }
}
```

</details>

<details>
<summary>Step 2 - Convert a sling mode to Exporter using custom Exporter service</summary>

```java
@Model(
        adaptables = Resource.class,
        adapters = IAdminXML.class,
        resourceType = "htlblog/admin/list",
        defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL
)
@Exporter(name = "customExporterName", extensions = "xml", selector = "geeks",
        options = {
                @ExporterOption(name = "SerializationFeature.WRAP_ROOT_VALUE", value = "true")
        }
)
@XmlRootElement(name = "admin")
public class IAdminXML {
  @ValueMapValue
  @XmlElement
  String title;

  @ValueMapValue
  @XmlElement
  String description;

  public String getTitle() { return title; }

  public String getDescription() { return description; }
}

```

</details>

## Multiple Sling Exporters

```mermaid
flowchart LR

a["@Exporters({})"] -->|1st Exporter| a1(["@Exporter(...)"])
a --> |2nd Exporter| a2(["@Exporter(...)"])
```

<details>
<summary>Multi Exporters Demo</summary>
```java
@Exporters({
        @Exporter(name = "jackson", extensions = "json", selector = "geeksjson"),
        @Exporter(name = "geeksxml", extensions = "xml", selector = "geeksxml")
})
```
</details>
