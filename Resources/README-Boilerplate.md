# Posterscope

This website is showing the information about posterscope organisation  there projects , articles , team members there technology stack and other details.

website is created from different blocks which can be reusable in any page of website and can be control through the CMS.
every block has its own structure(which is called "content model" in CMS term). from that content model we can create any number of content  (like creating instace of class). content model works like bluprint for creating content. if you made any changes in content model then you need to update code.(content model is for developer only. not for content creater).

* **Technology stack used.**
* Front-end : Blade templates , CSS (Bootstrap) , Javascript.
* Back-end  : PHP 8.1.10
* Framework : Laravel 9.34.0 


## Details

* **CMS used** Kontent.ai [https://kontent.ai/]
* **Production domain** [[live.domain.tld]]([live.domain.tld])
* **Pattern library** [[http://pattern-library-url.tld/path]]([pattern-library-url.tld/path])

## Servers

| | Development
| -- | --
| **Host** | [domain]
| **Name** | [server name (not an IP!)]
| **User** | [user]
| **Path** | [root path]

| | Staging
| -- | --
| **Host** | [domain]
| **Name** | [server name (not an IP!)]
| **User** | [user]
| **Path** | [root path]

| | Production
| -- | --
| **Host** | [domain]
| **Name** | [server name (not an IP!)]
| **User** | [user]
| **Path** | [root path]

## File structure

[Detail which paths contain which primary assets for the website. E.g, templates, JS files, CSS files, font files etc. Do not add the entire path structure - just the relevant paths.]

```
├── ./
├── app/
|   ├── Base
|   |   ├── Http
|   |       ├── Controllers [1]
|   |
|   ├── Http
|       ├── Controllers [2]
|
├── resources
|   ├── assets [3]
|   ├── js [4]
|   ├── scss [5]
|   ├── views [6]
|
├── routes [7]
```

* [1] This folder contains common cotroller for delivery client api and queries for fetching common data.
* [2] This contains all other controllers for fetching data from CMS.
* [3] Assets folder contains favicon, fonts and images files.
* [4] This contains Javascripts.
* [5] This contains sass files.
* [6] This contains all blade templates for showing data on front end.
* [7] This contains all routes.

## Development process
 
 1. Clone the repository at [https://bitbucket.org/whitespacers/dentsu_posterscope_website/src/79ffe9f4065e109ff3e2e0e267308578cea70e47/?at=WIRGL0034%2Fposterscope)]
 2. make sure that php installed on your system. [https://www.php.net/manual/en/install.php]
 4. "npm install"
 5. "composer install"
 6. "php artisan serve"
 7. "npm run dev" ---> for buiding front-end assets.

* add ".env" file in same  directory where ".env.example" file exist. 
* you can copy it from ".env.example".
* add project id (which you get in CMS) in new ".env".

####  **step to get project ID from CMS**

1. go to project settings.
2. click on API keys .
3. copy project ID from there.
 
 

### Available build tasks

The following tasks are available for building files into distribution folders.
[Please ensure at least one non-watching build task is available]

| Command | Description | Watches?
| :-- | :-- | :--
| php artisan serve | this will run the application on development server | any changes in php files.
| npm run dev | this build the front-end assets(css, js, images etc.)  | any changes in blade templates, css, js and assets.( need to reload  browser window).
| npm run watch | this build the front-end assets(css, js, images etc.)  | any changes in blade templates, css, js and assets ( without reloading browser window).
| npm run prod | this will build production files | [N]

### Deployment tasks

| Command | Server | Branch (or tag?)
| :-- | :-- | :--
| `cap deploy [stage]` | [server name] | [branch/tag spec]


## Notable CMS plugins used

The following notable or bespoke CMS plugins have been used on the site:
[List any non-standard or bespoke CMS plugins and their purpose - DO NOT add version numbers as these will rarely be accurate.]

| Name | Purpose
| :-- | :--
| **[Plugin name]** | Purpose
| **[Another plugin name]** | Purpose

## Notable JS libraries used

The following notable or bespoke JS libraries have been used on the site:

| Name | NPM? | Purpose
| :-- | -- | :--
| **laravel-mix** | [npm i laravel-mix] | for keeping watch at front-end assests and files without reloading browser window.

## External Fonts used
| **Font** | **Varient** | **Link**
| -- | -- | --
| Avenir Next | avenir-next-medium | https://www.fonts.com/


## Scheduled tasks (Cron, task scheduler)

| Command | Server | Purpose
| -- | -- | --
| [command] | [server name] | [detail of purpose]

## Other concerns
* **some URL are kept static.**

1. get-in-touch page URL are added in "Get in touch button" statically in Navigation bar. so if you change it in CMS then please change it in button as well.
2. "what we think" page URL(what-we-think) is added statically in code for filtering operation and pagination.
3. "Our work" page URL(our-work) is added statically in code for filtering operation and pagination.

## you can  change above url in code here 

| **Page** | **Path**
| :-- | :--
| get-in-touch | resource/views/layouts/header-nav.blade
| what we think | app/http/controllers/homepageController.php <br/> app/http/controllers/filterController.php
| Our work | app/http/controllers/homepageController.php <br/> app/http/controllers/filterController.php

