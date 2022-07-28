# Client Library

- Manage all client side resources(js, css, images etc)
- Keep resources in CRX repository

## How to reference client-side libraries in HTL?
```html
<!doctype html>
<html data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
    <head>
        <!-- Load css -->
        <sly data-sly-call="${clientlib.css @ categories='myCategory'}"/>

        <!-- Load all -->
        <sly data-sly-call="${clientlib.all @ categories='myCategory'}"/>
        
    </head>
    <body>
        <!-- Load JS -->
        <sly data-sly-call="${clientlib.js @ categories='myCategory'}"/>
    </body>
</html>

```
> All `client-side libraries` will be included in `clientlib.html`.

## Useful Properties
```mermaid
flowchart LR
a[Client Library folder] --property-->a1([Categories]) === a2[To identify the respective client library]
a -->|property|b1([Dependency]) === b2[a list of other client library categories]
a -->|property| c1([Embed]) === c2[embed code from other libraries]

```

## How to create Client Library?
```mermaid
flowchart TB
a[Step1 - Define a design] --> a1[Step2 - Create client library] --> a2[Step3 - Calling client library] --> a3[Step4 - Assign a design to website]
```

### Step1 - Define a design

> design folder is at */etc/designs*

#### how to define a desgin?
`AEM pannel` >> `Tools` >>`Operations` >> `Configuration` or `locahost:4502/miscadmin` >> `Designs` >> `new page` >>`page will go to /etc/desgins`

