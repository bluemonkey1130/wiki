# Upgrade program
### This repository is being used to develop the theme for the upgrade program.
- The upgrade program is primarily a plan for upgrading outdated sites quickly
- Each website will have different styling based on themes (corporate, services)
- A new website should aim to be completed in 3 days
- The different themes are intended to support the perceived use cases of clients.
- The idea of the theme is to be able to easily add new components and update features as needed in the future

## [Component Functional Scoping >](https://docs.google.com/document/d/1BbPL5hwn4lK5fKR4nvVt-kzgaPqVN-wXULat_n5yq4A/edit?usp=sharing)
This is the initial document used to plan the site structure and themes based on the figma visuals

## [Template Wireframes >](https://www.figma.com/file/i34Ebt572MBLUuw1klRdgn/Upgrade-Program---Structure?node-id=0%3A1)
These visuals are used to document the options and variations between themes, also used to generally document design changes to help support further development

## [Upgrade Program >](https://docs.google.com/document/d/1hUc3iErqDk1KnxuXJdlN39i7MTz7X-MugNStVzPBPfg/edit?usp=sharing)
General Status update, outlining some implemented solutions and tools developed for the site.

---
### Introduction
- This is a Craft 3 codebase,
- The main customisation is done in the **web**, **template** & **config** folders
- [Gulp](https://gulpjs.com/) is a preprocessor used to manage Scripts & Stylesheets. Includes a watch task.
    - [Gulp 4](https://codeburst.io/switching-to-gulp-4-0-271ae63530c0) syntax
- **3rd party** scripts are managed as npm dependencies where possible, scripts are bundled by Gulp, & styles are handled in SCSS using ``@import``
    - [jQuery](https://jquery.com/) scripts are included using gulp via node_modules 
    - [Gorko](https://developer.aliyun.com/mirror/npm/package/gorko) Styles are used to create utility classes it is included in the global.scss
    - [Slick Slider](https://kenwheeler.github.io/slick/) scripts are included using gulp & styles using global.scss, via node_modules
    - [Plyr.io](https://plyr.io/) is used to enhance iframe embeds & local videos
    - [Ihavecookies](https://github.com/ketanmistry/ihavecookies) is used to allow users to control cookie policy inline with GDPR regulation
    - [Modal-video](https://appleple.github.io/modal-video/) A lightweight jQuery plugin that displays a cookie consent message as required by EU regulation.
    - [Google Tag](https://tagmanager.google.com/#/home) / [Google Analytics](https://analytics.google.com/analytics/web/#/p258171687/reports/defaulthome) are used to manage tags added to the site, logic is applied on GTM admin to respect cookie policy choices
- **Craft Plugins** are used to support certain functionality such as maps & Video embeds
    - [Maps](https://plugins.craftcms.com/simplemap) allows google map locations to be selected in admin
    - [Embedded Assets](https://plugins.craftcms.com/embeddedassets) allows videos from youtube & vimeo to be managed as assets
    - [SuperTable](https://plugins.craftcms.com/super-table) used to enhance the fields within craft
    - [FeedMe](https://plugins.craftcms.com/feed-me) used to pull in rss feed as entries.
    - [XML Sitemap](https://plugins.craftcms.com/sitemap) used to control site maps from the control panel
    - [Sprig](https://plugins.craftcms.com/sprig) used to query entries with ajax
    - [SEOMate](https://plugins.craftcms.com/seomate) used to support metadata and schema
    - [Redactor](https://plugins.craftcms.com/redactor) provides a rich WYSIWYG editor
    - [Redactor Custom Styles](https://plugins.craftcms.com/redactor-custom-styles) applies predefined custom styles to selected text in Redactor fields.
    - [Contact Form](https://plugins.craftcms.com/contact-form) add an email contact form

---