# CSS / SCSS coding standards
> Part of [Coding](/Coding/Index.md) / [Languages](/Coding/Languages/Index.md)

The following standards outline the requirements for production of CSS or SCSS code. Any environment specific advice will be noted.

## Languages & frameworks used
All CSS should be produced in SCSS (SASS), and only in plain CSS if otherwise agreed with the technical lead.

## BEM
In house produced CSS should directly follow the BEM methodology standard for naming schemes. The full standards are detailed at the [official BEM website](http://getbem.com/naming/).

## Filenames
All CSS files should either use either the `.css` or `.scss` extensions, depending on whether pure CSS or SCSS is being used.

## Style
```
@media only (arguments) {
	.selector,
	.selector.chained {
		property: value;
		anotherproperty: value;
	}

	element['property="value"'] {
		property: value;
	}
}
```

### Numbers
When the value of a property is a numeric non-integer and the decimal portion is zero, it **must** be excluded. E.g:

```
// Correct
width: .725em;

// Incorrect
width: 0.725em;
```

Numbers also **must not** contain trailing zeros. E.g:

```
// Correct
width: 1.01px;

// Incorrect
width: 1.0100px;
```

If the sum total of a property value equates to zero, a unit **must not** be used. E.g:

```
// Correct
padding: 0;

// Incorrect
padding: 0px;
```

### Ordering of rules
Rules **must** be ordered consistently within a project. There are two options to choose from:

 1. Alphabetically, based on the first letter of the property name
 2. By group, defined below

#### CSS Property groups
Broadly, the CSS property groups are ordered as follows

| Order | Group                    | Example properties |
| ---   | ---                      | --- |
| 1     | Vendor specific & misc   | `zoom`, `widows`, `-webkit-*`, `-ms-*` |
| 2     | Animation/Transitions    | `transition`, `animation`, `perspective` |
| 3     | Box agnostic metrics     | `transform`, `stroke`, `outline`, `visibility`, `opacity` |
| 4     | Positioning metrics      | `display`, `top/right/bottom/left`, `column-*`, `grid/flex` |
| 5     | Box model metrics        | In order: `margin`, `border`, `width/height`, `padding` |
| 6     | Line model properties    | `line-height`, `text-*`, `word-*` |
| 7     | Font properties          | `font-*` |
| 8     | Color                    | `color` |
| 9     | Background properties    | `background-*` |

## Use of IDs
Wherever possible, the use of selectors based on element IDs **should** be avoided. The use of BEM precludes the necessity for such selectors but it is acceptable to use them in the following circumstances:

 1. When there is no control over the resulting HTML markup.
 2. When there is a necessity for ID based styling due to an existing specificity clash.

## Splitting of files
CSS/SCSS files **should** be split into logical components. Usually these components directly reflect their HTML counterparts but can also be split by other concerns, such as:

 - Reset CSS
 - Layout / Grid system
 - Typography
 - Theme based augmentations

## Response points
Unless a prior agreement to the contrary has been reached, all media-based CSS **must** adhere to the currently approved response points. The response points define at which point layout metrics may be redefined in a range of viewport sizes. They do not define other attributes such as rotation, DPI or device specific features.

![Responsive guidlines](https://docs.google.com/drawings/d/e/2PACX-1vS6xDjg-qg2IKIq9D22RcYmFF_n3QbIngPidWtgvYc95KNw7JONDwRz3qigmzPsm6_3PBJSsvt_RLSN/pub?w=962&h=637)

The above diagram is also in table form:

| Response point | Name               |
| ---:           | ---                |
| 300            | `small`/`x-small`  |
| (440)          | `small`            |
| 600            | `medium`           |
| 900            | `large`            |
| 1200           | `x-large`          |

The `440` pixel response point is optionally provided point which can be used in the case that the visual distance between `300` and `600` is too jarring for a particular design. In the case that this is implemented, the `300` respose point should be renamed to `x-small`.

## Media queries
Media queries, where applicable, **must** be defined in their own files organised by response point. The response points are detailed above. Components may **optionally** be further sub-divided within the response point organisation so as to keep them modularised. An example ideal file structure would be as follows:

```
├── ./
├── layout.scss
├── grid.scss
├── typography.scss
├── variables.scss
├── mixins.scss
├── media.scss [1]
├── components/ [2]
│   ├── component-1.scss
│   ├── component-2.scss
│   ├── component-3.scss
├── 300/ [3]
│   ├── typography.scss
│   ├── variables.scss
│   ├── components/
│   |   ├── component-1.scss
│   |   ├── component-2.scss
├── 600/
│   ├── typography.scss
│   ├── components/
│   |   ├── component-3.scss
├── 900/
│   ├── grid.scss
│   ├── components/
|   |   ├── component-1.scss
|   |   ├── component-3.scss
```

 1. General media response CSS that doesn't fit within the standard response points.
 2. Component based CSS, organised by component name.
 3. Standard response point based CSS, subdivided identically to top level.

## Linting
All SASS/CSS should be linted using [Stylelint](https://stylelint.io). The configuration file can be found within the [IDE Toolkit](https://github.com/dentsucreativeuk/ide-toolkit) repository, and the following main rules are enforced:

| Rule | Enforcement |
| ---  | --- |
| `color-hex-case` | Colours defined in hexadecimal format must be in lower-case. |
| `color-no-invalid-hex` | Disallows hexadecimal colour definitions that are non computable. |
| `font-family-name-quotes` | Ensures that fonts defined with `font-family` are quoted unless they are keywords (`serif`, `monospace` etc). |
| `font-family-no-duplicate-names` | Disallows duplicate names within a font stack. |
| `number-leading-zero` | Enforces the leading zero rule above. |
| `number-no-trailing-zeros` | Enforces the trailing zero rule above. |
| `number-max-precision` | Prevents numbers from being expressed with a precision greater than **10**. |
| `string-no-newline` | Prevents the use of unescaped newlines within string literals. |
| `string-quotes` | Enforces the use of single quotes only within strings. |
| `length-zero-no-unit` | Enforces the non-unit zero rule above. |
| `unit-whitelist` | Allows the following units to be used: 'em', 'rem', '%', 's', 'px', 'vh', 'vw', 'deg'. |
| `shorthand-property-no-redundant-values` | Prevents redundant values from being expressed within shorthand properties. |
| `property-case` | Ensures that all property names are expressed in lower case. |
| `indentation` | Enforces single **tab** indentation, except for subsequent values on new lines in the same property. |
| `block-closing-brace-empty-line-before` | Ensures no empty lines are created before the closing brace of a single rule. |
| `block-no-empty` | Disallows empty rule blocks. |
| `max-empty-lines` | Enforces a maximum of **2** empty lines between rules and blocks. |
| `no-eol-whitespace` | Disallows white space at the end of lines. |
| `no-extra-semicolons` | Disallows multiple semicolons at the end of properties. |

The rules above can be found in greater detail on the [Stylelint website](https://stylelint.io/user-guide/rules/).
