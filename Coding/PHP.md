# PHP coding standards
The following standards outline the requirements for production of PHP scripts based on the PHP 7 environment. Some guidance will be applicable for PHP 5.x. Any environment specific advice will be noted.

## PSR
Broadly, the following PSR guideline indices from the PHP Framework Interop Group are being enforced:

| Num | Title                                                            | Description |
| --- | ---                                                              | --- |
| 1   | [Basic Coding Standard](http://www.php-fig.org/psr/psr-1/)       | Outlines the standards to which developers will adhere to for all PHP documents regardless of PHP version |
| 2   | [Coding Style Guide](http://www.php-fig.org/psr/psr-2/)          | Outlines the standards to which all PHP script will be styled, regardless of PHP version |
| 3   | [Autoloading standard](http://www.php-fig.org/psr/psr-4/)        | Outlines the standards for auto-loading other PHP files |

### Differences between PHP and the General guidance

#### Spacing and indentation
The PSR 2 Coding Style Guide outlines that indentation of 4 spaces **must** be used, instead of tabs. This overrides the Whitespace [General coding standards](/Coding/General.md) on this aspect.

### Exceptions
The following exceptions from the PSR guidance are applicable:

1. When working within environments or code older than PHP 7, the PSR 4 Autoloading standard will be considered **optional** only. A pseudo namespacing alternative for PHP 5.3 and older is detailed in PSR 1 under "Namespace and Class Names".
2. The soft limit on line length in PSR 2 should be considered overidden by the Whitespace [General coding standards](/Coding/General.md), in which the 120 character limit **must not** be exceeded.
