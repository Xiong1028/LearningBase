# Client Library

- Manage all client side resources(js, css, images etc)
- Keep resources in CRX repository

## How to reference client-side libraries in HTL?

```html
<!DOCTYPE html>
<html data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
  <head>
    <!-- Load css -->
    <sly data-sly-call="${clientlib.css @ categories='myCategory'}" />

    <!-- Load all -->
    <sly data-sly-call="${clientlib.all @ categories='myCategory'}" />
  </head>
  <body>
    <!-- Load JS -->
    <sly data-sly-call="${clientlib.js @ categories='myCategory'}" />
  </body>
</html>
```

> All `client-side libraries` will be included in `clientlib.html`.

## clientlibs structure

![clientlibs structure](/assets/img/aem/clientlibs-structure.png){width=600}

## Useful Properties

```mermaid
flowchart LR
a[Client Library folder] --property-->a1([Categories]) === a2[To identify the respective client library]
a -->|property|b1([Dependency]) === b2[a list of other client library categories]
a -->|property| c1([Embed]) === c2[embed code from other libraries]

```

![clientlibs folder node properties](/assets/img/aem/clientlibs-folder-properties.png){width="800"}

## How to create Client Library?

```mermaid
flowchart TB
a[Step1 - Define a design] --> a1[Step2 - Create client library] --> a2[Step3 - Calling client library] --> a3[Step4 - Assign a design to website]
```

### Step1 - Define a design

> design folder is at _/etc/designs_

#### how to define a desgin?

`AEM pannel` >> `Tools` >>`Operations` >> `Configuration` or `locahost:4502/miscadmin` >> `Designs` >> `new page` >>`page will go to /etc/desgins`

### Step2 - [Create client library](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/clientlibs.html?lang=en#creating-client-library-folders)

```mermaid
flowchart LR
a((Front-end development)) --> a1[clientlib-site] & a2[clientlib-all] -->|moveTo| a3[The design folder in step 1. /etc/designs/pageName]
```

![Create clientLibrary](/assets/img/aem/clientlibarch.png) <br>
<sup>\* Data from [adobe document](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/clientlibs.html?lang=en#creating-client-library-folders)</sup>

### Step3 - Calling client library

```html
<sly
  data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html"
  data-sly-call="${clientlib.all @ categories=['myCategory1', 'myCategory2']}"
/>
```

```mermaid
flowchart LR
a[Create two customheaderlibs.html <br>and customfooter.html] --> a1([Call custom clientLibrary])--> a2[Include custom js libs files <br>into original footer.html] --> a3(head.html in parent built-in page component<br> has already included customheaderlibs.html)
```

### Step4 - Assign a design to a website

`AEM pannel` >> `Sites` >> `Project` >> `View Properties` >> `Advanced` >> `Design` >> `Select design` >> `Back to page` >> `check the result`

## Minify clientlibs files
![Minify js and css](/assets/img/aem/minify-clientlibs.png){width=600}
