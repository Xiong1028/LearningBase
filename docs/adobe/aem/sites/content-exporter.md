# AEM Content Exporter Service

*Sling Model Exporter*
> since 6.3, AEM provides content exporter service to export json or xml to headless application. <br>
AEM provides an OTTB content exporter - jackson


```mermaid
flowchart LR

a[AEM Author] -->|json or xml| b(Android) & c(iOS) & d(Third Party)

```

## How to make a sling model as an Exporter?
![content exporter](/assets/img/aem/content-exporter-1.png)
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>

> If the selector is not provided, AEM'll provide a default selector called "model". selector property is optional.



