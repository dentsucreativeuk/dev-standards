# Minimum performance standards
> Part of [Production](/Production/Index.md)

## Google pagespeed

### Minimum scores
Every project developed by Whitespace for web consumption should be tested against the [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/) tool and unless otherwise agreed, **must** score _at least_ **85** for desktop and **75** for mobile.

In addition to that, the following issues **must not** appear on a PageSpeed report:

 - Minify CSS
 - Leverage browser caching
 - Reduce server response time
 - Optimise images
 - Configure the Viewport
 - Avoid Landing Page Redirects
 - Enable Compression
 - Use Legible Font Sizes

## Image compression

### Within CMSes
Images uploaded into a CMS based project should create compressed copies either during the editing process or by using a cached solution for front-end compression. Images **must not** be displayed as uploaded without some form of control over their file size and quality.

If required, the ability to either cropping or otherwise manipulate images **should** also be created for content authors to use throughout population and the life of the web property or application.

### On static templates
When inserting images into static, non-cms driven code or basic HTML templates, it is the developer's responsibility to ensure all images supplied are suitibly compressed. The following formats can be compressed:

| Format | Compression Techniques | Tools |
| ---    | ---                    | ---   |
| JPEG   | Lossy, Progressive, Blurring, Matting | Photoshop, Imageoptim, Pixelmator, Meta removal |
| GIF    | Lossless, Pallet reduction, Dithering, Transparency, Interlacing, Meta removal | Photoshop, Imageoptim, Pixelmator |
| PNG    | Lossless, Lossy, Pallet reduction, Bit depth reduction, Interlacing, Meta removal | Photoshop, Imageoptim, ImageAlpha, pngquant, TinyPNG |

### TTFB
When browsing any Whitespace web property on a broadband connection, the Time To First Byte (TTFB) for any CMS powered web property **must** be at minimum **500ms**, and **should** be **200ms** or lower.
