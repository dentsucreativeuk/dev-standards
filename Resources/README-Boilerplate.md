# [Website Name]

[A short description of what the website is and broadly, the technology stack used to create it...]

## Details

* **Primary developer**			[Author name](email@whitespacers.com)
* **CMS used**						[CMS]
* **DB used**						[DB provider]
* **CCN url**						[[ccn.domain.tld]]([ccn.domain.tld])
* **Live domain**					[[live.domain.tld]]([live.domain.tld])
* **Pattern library**			[[http://pattern-library-url.tld/path]]([pattern-library-url.tld/path])

## Servers

|          | Development              | Live                    |
| --		  | --							  | --							 |
| **CCN**  | [domain]                 | [domain]                |
| **Host** | [internal hostname]      | [internal hostname]     |
| **User** | [user]                   | [user]                  |
| **Path** | [root path]              | [root path]             |

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

## Build process

The following build process is used.

* [Grunt/Gulp]
* [SCSS/LESS]
* [JS Build tool, if any]
* NPM `npm install` required: [Y\N]

[Details of build process not covered above...]

### Available build tasks

The following tasks are available for building files into distribution folders.
[Please ensure at least one non-watching build task is available]

| Command         | Description                          | Watch? |
| --				   | --											   | --	   |
| [build command] | [description of what the build does] | [Y\N]  |

## CMS plugins used

[List available/installed plugins and their purpose - DO NOT add version numbers as these will rarely be accurate.]

| Name                      | Purpose |
| --								 | --	     |
| **[Plugin name]**         | Purpose |
| **[Another plugin name]** | Purpose |

## Javascript libraries used

The following JS libraries have been used for the front-end of the site:

### Internal

* [JS Library list]

### External

* [JS Library list, with links to lesser known libs]

## Fonts used

[Detail whether or not the fonts are hosted locally.]

* [font name ([font variant])] - [Provider]([provider.url])

## Automated tasks (Cron, task scheduler)

| Command       | Frequency | Purpose             |
| --				 | --			 | --						  |
| [command]     | * * * * * | [detail of purpose] |

## Any other concerns?

[Please detail anything else the developer should be aware of that is not covered above. Delete this if you have no extra information to give]
