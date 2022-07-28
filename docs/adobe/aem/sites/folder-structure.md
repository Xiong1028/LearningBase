# Folder Structure

## CRX Folder Structure
- *app/your project/* - custom templates, components, OSGI bundles, static files.
- *content* - pages, related data. all content of your website.
- *conf* - all configuration of site.
- *libs* - out of the box components.
- *etc* - client library, design dialog info.
- *tmp* - temporary working area.
- *var* - contains files that change and are updated by system.
- *home* - information about users and group.
- *oak:index* - jackrabbit oak index definition.

## Create Project in CRX

```bash
├──apps
│	├──project name
│		├──components
│			├──content
│			└──structure
│		└──templates 
|──content
```

## Create website sturcture  in AEM

```bash
├──Apple *
│	├──English *
│		├──About US *
|		├──Products *
│			├──Iphone *
|			├──Mac	  *
│			└──Ipad 	*
│		└──Services *
|	|──French	*
```
*\* means page type. Creating page under parent node*