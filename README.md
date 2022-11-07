# Ananke, A theme for [Hugo](https://gohugo.io/), a framework for building websites.

This is my fork of the Ananke theme, used to build my [personal website](www.scheuclu.com).

![screenshot](https://awesomescreenshot.s3.amazonaws.com/image/3871678/34137298-2508cb4522cf23690a925d7067020b10.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJSCJQ2NM3XLFPVKA%2F20221107%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20221107T121411Z&X-Amz-Expires=28800&X-Amz-SignedHeaders=host&X-Amz-Signature=6b9d44aa826640454dd8f8868974731bee4c968f6a8e923f2210a4b8c4ce4e60)


<p float="left">
  <img src="https://awesomescreenshot.s3.amazonaws.com/image/3871678/34137461-115807cfc2edb455c4003601c3b01d2d.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJSCJQ2NM3XLFPVKA%2F20221107%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20221107T122250Z&X-Amz-Expires=28800&X-Amz-SignedHeaders=host&X-Amz-Signature=170e0ecc990611e706f0bb13589428da7c8ebcdece5fe8c0a4f1970f73160bbd" width="49.5%" />
  <img src="https://awesomescreenshot.s3.amazonaws.com/image/3871678/34137492-b8da8e1a34ec91fb5f81bbae30334158.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJSCJQ2NM3XLFPVKA%2F20221107%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20221107T122403Z&X-Amz-Expires=28800&X-Amz-SignedHeaders=host&X-Amz-Signature=82ff8cff0e66177315d1a2ed26dd00b2a03bab0a36c3b7a41722ce1da23d6dd5" width="49.5%" /> 
</p>

## Installation

### As a Hugo Module (recommended)

> ⚠️ If you installed a [Hugo binary](https://gohugo.io/getting-started/installing/#binary-cross-platform), you may not have Go installed on your machine. To check if Go is installed:
> ```
> $ go version
> ```
>  Go modules were considered production ready in v1.14. [Download Go](https://golang.org/dl/). 

1. From your project's root directory, initiate the hugo module system if you haven't already:

   ```
   $ hugo mod init github.com/<your_user>/<your_project>
   ```

2. Add the theme's repo to your `config.toml`:

   ```toml
   theme = ["github.com/scheuclu/gohugo-theme-ananke"]
   ```

### As Git Submodule

Inside the folder of your Hugo site run:

```
$ git submodule add https://github.com/scheuclu/gohugo-theme-ananke.git themes/ananke
```
For more information read the official [setup guide](//gohugo.io/overview/installing/) of Hugo.



## Getting started

After installing the theme successfully it requires a just a few more steps to get your site running.


### The config file

Take a look inside the [`exampleSite`](https://github.com/scheuclu/gohugo-theme-ananke/tree/master/exampleSite) folder of this theme. You'll find a file called [`config.toml`](https://github.com/scheuclu/gohugo-theme-ananke/blob/master/exampleSite/config.toml). To use it, copy the [`config.toml`](https://github.com/scheuclu/gohugo-theme-ananke/blob/master/exampleSite/config.toml) in the root folder of your Hugo site. Feel free to change the strings in this theme.

You may need to delete the line: `themesDir = "../.."`


### Add comments

To enable comments, add following to your config file:

- DISQUS: `disqusShortname = YOURSHORTNAME`
- COMMENTO:
  ```
  [params]
    commentoEnable = true
  ```

### Change the hero background

For any page or post you can add a featured image by including the local path in front matter (see content in the `exampleSite/content/_readme.md` file for examples): `featured_image: '/images/gohugo-default-sample-hero-image.jpg'`

#### Featured image as Page Resources
If user is using [Page Resources](https://gohugo.io/content-management/page-resources/), the theme will try and match the `featured_image` from with a page resource of type `image` and use its relative permalink. If no `featured_image` is set, the theme will look for a Page Resource of type `image` whose filepath incudes either `cover` or `feature` 

#### Other hero settings
If you would like to hide the header text on the featured image on a page, set `omit_header_text` to `true`. See `exampleSite/content/contact.md` for an example.

You don't need an image though. The default background color is black, but you can change the color, by changing the default color class in the config.toml file. Choose a background color from any on the [Tachyons](https://tachyons.io/docs/themes/skins/) library site, and preface it with "bg-"

example: `background_color_class = "bg-blue"` or `background_color_class = "bg-gray"`



### Activate the contact form

This theme includes a shortcode for a contact form that you can add to any page (there is an example on the contact page in the exampleSite folder). One option is to use [formspree.io](//formspree.io/) as proxy to send the actual email. Each month, visitors can send you up to one thousand emails without incurring extra charges. Visit the Formspree site to get the "action" link and add it to your shortcode like this:

```
{{< form-contact action="https://formspree.io/your@email.com" >}}
```

### Social Follow + Share

The theme automatically adds "Follow" link icons to the header and footer and "Share" link icons to pages unless `disable_share` parameter is set to true either on the site level (site params) or page level (front matter). Each built-in services sports a label, an icon and a color.

In order to register a service to be used, user must add an `ananke_socials` parameter to its project configuration file and list them through it in the desired order. Each entry must bear a 
- name*: It matches the built-in service reference (Ex: twitter, github)
- url*: The url of the handle's profile on the service (Ex: https://twitter.com/theNewDynamic, https://github.com/
theNewDynamic)

```yaml
params:
  ananke_socials:
  - name: twitter
    url: https://twitter.com/theNewDynamic
  - name: github
    url: https://github.com/theNewDynamic
```

If user needs to overwrite default `color` and `label` of the service, they simply need to append the following to the entry:
- label: The displayed name of the service to be used to popuplate `[title]` attributes and read-only. (Ex: Twitter, GitHub)
- color: Used for styling purposes. (Ex: '#1da1f2', '#6cc644')

```yaml
params:
  ananke_socials:
  - name: twitter
    url: https://twitter.com/theNewDynamic
    label: TND Twitter
  - name: github
    url: https://github.com/theNewDynamic
    label: TND GitHub Account
    color: '#ff6800'
```

#### Limit Follow or Share

If a user needs to control Share and Follow of a service, for example enabling "Share on Facebook" without having a Facebook Page to "follow", they can set `follow: false` one the registered service.

```yaml
params:
  ananke_socials:
  - name: facebook
    label: Facebook
    follow: false
  - name: twitter
    url: https://twitter.com/theNewDynamic
    label: TND Twitter
```

#### Social Icons Customization

On top of easily customizing the built-in services' label and color, user can overwrite their icon by adding an svg file at `/assets/ananke/socials` with a filename matching the service's name.
For example, in order to use your own GitHub icon, simply add an svg file at `/assets/ananke/socials/github.svg`

#### Built-in Services
Here is the list of built-in services. Those marked with an `*` are also part of the "Share" module.

- twitter*
- instagram
- youtube
- github
- gitlab
- keybase
- linkedin*
- medium
- mastodon
- slack
- stackoverflow
- facebook*
- rss

#### Complement

In order to add an unkown service (absent from the list above), you simply need to add all three settings to `ananke_socials`: name, url, label, color, and optionally add an icon file matching the `name` to the `assets/ananke/socials` directory. In the absence of an icon, the theme will print the service's label.

### Content indexing

If the theme is ran in [production](#production), pages will be indexed by search engines. To prevent indexing on some given pages, add `private: true` to its Front Matter.

### Update font or body classes

The theme is set, by default, to use a near-white background color and the "Avenir" or serif typeface. You can change these in your config file with the `body_classes` parameter, like this:

```
[params]
  body_classes = "avenir bg-near-white"
```

which will give you a body class like this:

```
<body class="avenir bg-near-white">
```

note: The `body_classes` parameter will not change the font used in post content. To do this, you must use the `post_content_classes` parameter.

You can find a list of available typefaces [here](https://github.com/tachyons-css/tachyons/blob/v4.7.0/src/_font-family.css).

And a list of background colors [here](https://github.com/tachyons-css/tachyons/blob/v4.7.0/src/_skins.css#L96).


_n.b. in future versions we will likely separate the typeface and other body classes._


### CSS

Ananke stylesheet is built with Hugo Pipes's [Asset Bundling](https://gohugo.io/hugo-pipes/bundling/#readout) alone to maximize compatibiliy. The theme simply bundles its several files into one minified and fingerprinted (in production) CSS file.

Ananke uses [Tachyon.io](https://tachyons.io/) utility class library.

#### Custom CSS

WARNING: Pending resolution of this [discussion](https://github.com/theNewDynamic/gohugo-theme-ananke/discussions/452#discussioncomment-1865301), Custom CSS only works with Hugo Extended

In order to complement the default CSS with your own, you can add custom css files to the project. 

1. Just add a `assets/ananke/css` directory to your project and add the file(s) in it.
2. Register the files using the `custom_css` key in your site's parameter. The path referenced in the parameter should be relative to the `assets/ananke/css` folder. 

The css files will be added in their registered order to final `main.css` file.

For example, if your css files are `assets/ananke/css/custom.css` and `assets/ananke/special.css` then add the following to the config file:

```
  [params]
    custom_css = ["custom.css","special.css"]
```
__IMPORTANT__: Files registered through the `custom_css` array, while unlimited in number, must be of the same type (Ex: all `scss` or all `css`)

__Note on retrocompatibiliy for custom css__: If the files registered through the `custom_css` setting are not found in `assets/ananke/css` the theme will expect them to live at the given path relative to the static directory and load them as <link> requests.

### Show Reading Time and Word Count

If you add a key of `show_reading_time` true to either the Config Params, a page or section's front matter, articles will show the reading time and word count.


### Adding Scripts to the Page Head

Some scripts need to be added within the page head. To add your own scripts to the page head, simply insert them into the `head-additions.html` partial located in the `layouts/partials` folder.


### Logo

You can replace the title of your site in the top left corner of each page with your own logo. To do that put your own logo into the `static` directory of your website, and add the `site_logo` parameter to the site params in your config file. For example:

```
[params]
  site_logo = "img/logo.svg"
```

### Set Content Font Color

You can set the font color of the main content both globally and on individual pages:

Globally:
Set the `text_color` param in the `config.toml` file.
```
[params]
  text_color = "green"
```

Individual Page (prioritized over global):
Set the `text_color` param in a page's markdown file front matter.

note: The value of `text_color` must be a valid tachyons color class. A list can be found [here](https://tachyons.io/docs/themes/skins/).


### Localize date format

Dates of blog posts and single pages are rendered with the default date format commonly used in the USA and Canada. It is possible to specify a different format.

```
[params]
  date_format = "2. January 2006"
```

With hugo 0.87.0 and above, you can also use predefined layout, like `:date_full`, and it will output localized dates or times. 
See hugo's documentation of the [`time.Format` function](https://gohugo.io/functions/dateformat/) for more details.


### Nearly finished

In order to see your site in action, run Hugo's built-in local server.

`$ hugo server`

Now enter [`localhost:1313`](http://localhost:1313/) in the address bar of your browser.

## Production

To run in production (e.g. to have Google Analytics show up), run `HUGO_ENV=production` before your build command. For example:

```
HUGO_ENV=production hugo
```

Note: The above command will not work on Windows. If you are running a Windows OS, use the below command:

```
set HUGO_ENV=production
hugo
```

## Contributing

If you find a bug or have an idea for a feature, feel free to use the [issue tracker](https://github.com/theNewDynamic/gohugo-theme-ananke/issues) to let me know.




TODO:

- fix hard-coded link to [section](https://github.com/theNewDynamic/gohugo-theme-ananke/blob/master/layouts/index.html#L32)
