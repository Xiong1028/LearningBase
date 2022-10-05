# MSM - Multi Sites Management

<p class="call-out-1">
Set -DsingleCountry=n in maven-archetype <br>
Note:  All screenshots in this page are from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a>
</p>

## Create a language master

> - which contains all language copy
> - can be renamed anything,
> - official recommended.

1. Create a default language site (typically English)
   ![English site](/assets/img/aem/msm-site-1.png){width=600}
2. Make a language copy for other languages.
   ![Language copy](/assets/img/aem/msm-site-2.png){width=600}
   <br>
   Select `Create Multi-language Translation Project` 
   ![Language copy](/assets/img/aem/msm-site-3.png){width=600}

3. Create sites for specific country.
   ![Live copy](/assets/img/aem/msm-site-4.png){width=800}


## AEM sites translation
> For more details, please see [aem geeks tutorial](https://www.youtube.com/watch?v=MMtS8ag6OUE&list=PLEaEQSM_Y4tmJjQICTFDm2lU5mNmd_Oar&index=25&ab_channel=AEMGEEKS)

```mermaid
flowchart TB
a[Create language copy] --> b([Create Multi-language Translation Project?])
b --> |Yes| c[OK]
c --> |go to projects in panel| d(Choose translation porject) --> d1["choose start >> translate sites"]
b --> |No| e[End]
```
