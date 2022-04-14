# [Website Name]

[A short description of what the website is and broadly, the technology stack used to create it...]

## Details

* **CMS used** [CMS]
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
├── privatefolder/ [1]
├── public_html/ [2]
│   ├── pathname/
│   │   ├── subpathname/ [3]
```

* [1] [Description of private path contents.]
* [2] [Description of public path contents.]
* [3] [Description of another public path contents.]

## Development process

[Detail the steps required to allow working on the site locally, and any gotchas which might need to be thought about, such as remotely hosted media, thirdy party services, etc.]

[Include steps such as `npm install` (including the version of node required), `composer install`, any bespoke requirements etc.]

 1. Clone the repository at [https://repo-url.com/](https://repo-url.com/)
 2. [Step 2...]

### Available build tasks

The following tasks are available for building files into distribution folders.
[Please ensure at least one non-watching build task is available]

| Command | Description | Watches?
| -- | -- | --
| [build command] | [describe what the task does] | [Y\N]

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
| **[Library name]** | [Y/N] | Purpose
| **[Another library name]** | [Y/N] | Purpose

## External Fonts used

[Detail any externally provided fonts and which provider they come from]

* [font name ([font variant])] - [Provider]([provider.url])

## Scheduled tasks (Cron, task scheduler)

| Command | Server | Purpose
| -- | -- | --
| [command] | [server name] | [detail of purpose]

## Other concerns

[Please detail anything else the developer should be aware of that is not covered above. Delete this if you have no extra information to give]
