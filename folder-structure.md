### Folder Structure
```text
root/
  config/ 
  src/
  storage/
  templates/
  web/
  - .env
  - .gitignore
  - composer.json
  - craft
  - gulpfile.js
  - package.json
  - readme.md
```
---
### Templates
All the Twig templates that make up the site are stored in here.
```text
templates
  _base-layouts/
  _boilerplate/
  _inline-css/
  _layouts/
  channels/
  - index.twig
  - sprig.twig
```
---
### Twig Templates Using Inheritance
Extending in Twig is a method by which one template can inherit content from another template, while still being able to override parts of that content.

``global-variables.twig`` > ``base-web-layout.twig`` > ``base-html-layout.twig`` > ``generic-page-layout.twig`` > ( ``index.twig``, ``archive.twig``, etc.. )

```text
_base-layouts/
    - error-page-layout.twig
    - generic-page-layout.twig
    - global-varibles.twig
_boilerplate/
    _layouts/
        - base-html-layout.twig
        - base-web-layout.twig
    _partials/
        - critical-css.twig
        - head-js.twig
        - head-meta.twig
        - structured-data.twig
        - tab-handler.twig
        - theme-handler.twig
_inline-css/
    - site-fonts.css
_layouts/
    _block-partials/
        _block-atoms/
            - _button.twig
            - _hero-image.twig
            - _image.twig
            - _social.twig
            - _testimonials.twig
            - _text.twig
            - _video.twig
        - _block-card.twig
        - _block-entry-slider.twig
        - _block-form.twig
        - _block-text.twig
        - _testimonials-video.twig
    - _footer.twig
    - _header.twig
    - _hero.twig
    - _location.twig
    - _navigation.twig
    - _page-content.twig
    - _tabs.twig
channels/
    _components/
        - _filter-component.twig
        - _filter-load-more.twig
        - _load-more.twig
        - _sprig-test.twig
        - _testimonials-load-more.twig
    entires
        - _entry.twig
    - archive.twig
    - archive-blog.twig
    - archive-testimonials.twig
- index.twig
- sprig.twig
```
**index.twig** - New base templates should extend **generic-page-layout.twig** which in turn include the other templates
````html
{% extends "_base-layouts/generic-page-layout.twig" %}
{% block content %}
    <article>
        {% include "_layouts/_hero.twig" %}
        {% include "_layouts/_page-content.twig" %}
    </article>
{% endblock %}
````
Where it makes sense template code is broken up and included on multiple templates, sometimes in multiple places.
```html
<article>
    {% include '_layouts/_block-partials/_block-atoms/image.twig' %}
</article>
```
This sometimes involves passing parameters along with the include, which is useful when standardising data inputs for these components. For example, information from an image field  may be accessible at``entry.image`` in one place & ``block.image`` in another, which may be inside a loop.
```html
with { block: testimonial } // This passes the variable 'testimonial' as 'block'
```
```html
{% for testimonial in testimonials %}
    <article>
      {% include "_layouts/_block-partials/_block-atoms/_testimonial.twig" with {block:testimonial} %}
    </article>  
{% endfor %}
```
In the example below the navigation is being included, and the parameters are controlling the length and starting position for the items in the navigation. This has been used to split the navigation into two halves when necessary
```html
<header>
<nav>
    {% include '_layouts/_navigation.twig' with {length: halfLength, offset: 0} %}
</nav>
<img src="logo"/>
<nav>
    {% include '_layouts/_navigation.twig' with {length: halfLength, offset: halfLength} %}
</nav>
</header>
```