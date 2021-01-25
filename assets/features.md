## Features
Features and functions that support the site.

---
### Slick Slider - [JS Library](https://github.com/kenwheeler/slick)
Slick slider is used to control the various carousels on the site, slick is imported as a NPM dependency, and configured in ``sliders.js``.

---
### Plyr - [JS Library](https://github.com/sampotts/plyr)
Plyr is used alongside modal video to support video on the site. Iframes are used to embed content from Youtube & Vimeo, these are enhanced by Plyr to allow for autoplay / muting etc. Local Videos are also supported by Plyr using HTML5 ``<video>``

--- 
### Modal-Video - [JS Library](https://github.com/appleple/modal-video)
Modal video is used to support inline video, it allows the video to be opened in a modal window. Only supports Vimeo & Youtube.

---

### I Have Cookies - [JS Library](https://github.com/ketanmistry/ihavecookies)
This library supports the cookie policy of the site. It is a small library that creates a cookie to control a users preferences. The result of these preferences is leveraged to set a opt-out cookie. This cookie is monitored by GTM and conditionally triggers the analytics tag. When a preference is set the page forces the page to refresh so the change can take effect.

---
### Sprig - [Craft Plugin](https://putyourlightson.com/plugins/sprig)
Sprig is used to create reactive components involving ajax queries. This is used on the archive templates to filter entries **support search / load more**
**Usage:** In Template,

Usually in self-contained sprig components included on pages
````html
<div class="grid-layout has-three-columns">
  {{ sprig('channels/_components/_filter-load-more',{
      'section': section,
      'limit':limit,
      'search':search,
      'categoryId':categoryId
  }) }}
</div>
```` 
or as custom directives
````html  
<div s-replace="#archive-entries"></div>
````
[Further Documentation...](https://putyourlightson.com/plugins/sprig)

---
### Maps - [Craft Plugin](https://github.com/ethercreative/simplemap)
This craft plugin is used to allow admins to choose precise locations on a map in the control panel. This requires API credentials provided by google (Maps JavaScript API & Places API ). The information from these map locations is used to populate the location layout in the page builder & address information in the footer. The location information is also used for meta/schema data on the site. We are using the lite version of the plugin, which supports all the admin functionality but not the front end output. The free version allows the field to be used, generating detailed location information from a map picker. I am then using this information with some custom script to output the maps.

**Usage:** In Control Panel, Use map field to allow locations to be picked. Currently used inside a matrix field to output multiple maps

---
### FeedMe - [Craft Plugin](https://docs.craftcms.com/feed-me/v4/)
This is used to map ``XML``, ``RSS``, ``ATOM``, ``CSV`` or ``JSON`` feeds to craft entries.

**Usage:**  In Control Panel, Use the UI to map data to fields in entries

---
### Embedded Assets - [Craft Plugin](https://github.com/spicywebau/craft-embedded-assets)
This is used to add YouTube/Vimeo videos to Craft's asset manager. This allows the Oembed parameters to be exposed, like query string, thumbnail etc.

**Usage:**  In Template ``{% set vid = craft.embeddedAssets.get(video) %}``
- ``getVideoUrl()``
- ``getVideoId()``
- ``providerName()``

---
### SEOMate - [Craft Plugin](https://github.com/vaersaagod/seomate)
This plugin is used to add meta data to the site. Page titles are automatically set on the entry name and description taken from the body. SEOMate generates meta and OG tags in the head. The global title and description can be set and overridden on a page level. The structured data/schema is generated from SEO mate supported by [spatie/schema-org](https://github.com/spatie/schema-org). Which allows access to all the different schemas in the spatie/schema-org package ``craft.schema``.

**Usage**: Custom configuration file``config/seomate.php``