### SCSS Config, CSS Variables & Gorko
Using these tool the codebase support customisation from a single configuration file ``_config.scss``
SCSS varibles are used for media queries and CSS varible cannot be used in a media query and they don't need to be changed often
```scss
$large: 1300px;
$medium-large: 1100px;
$medium: 1000px;
$largeTablet: 920px;
$tablet: 767px;
$phablet: 575px;
$mobile: 480px;
$smallmobile: 375px;
```
Global CSS variables are used to set/store all the values for `margins`, `max-width`,`grid-gap` & `padding` etc....

These values can be set globally & adjusted for local elements.
### Colours
Colours set in CSS Variables
```css
:root {
/* Values can be overridden in admin */
  --primary: #223c6d;
  --primary-shade: #566d98;
  --primary-invert: #a5a5a5;
  --secondary: #0E3B93;
  --secondary-shade: #2374ab;
  --secondary-invert: #f3f3f3;
  --tertiary: #FFB800;
  --quaternary: #121C52;
  --body-colour: #223c6d;
  --heading-colour: #223c6d;
  --light: #f3f3f3;
  --grey: #767676;
  --dark: #1a1a1a;
  --background-colour: #f3f3f3;
}
```
### Sizes
Sizes set in CSS Variables
```css
:root {
  --ratio: 1.5; /* Adjust all other values */
  --s-5: calc(var(--s-4) / var(--ratio)); /* Smallest Value */
  --s-4: calc(var(--s-3) / var(--ratio));
  --s-3: calc(var(--s-2) / var(--ratio));
  --s-2: calc(var(--s-1) / var(--ratio));
  --s-1: calc(var(--s0) / var(--ratio));
  --zero: 0rem;
  --s0: 1rem;
  --s1: calc(var(--s0) * var(--ratio));
  --s2: calc(var(--s1) * var(--ratio));
  --s3: calc(var(--s2) * var(--ratio));
  --s4: calc(var(--s3) * var(--ratio));
  --s5: calc(var(--s4) * var(--ratio));
  --s6: calc(var(--s5) * var(--ratio)); /* Largest Value */
  /* Negative values */
  --s-neg5: calc(-1 * var(--s5));
  --s-neg4: calc(-1 * var(--s4));
  --s-neg3: calc(-1 * var(--s3));
  --s-neg2: calc(-1 * var(--s2));
  --s-neg1: calc(-1 * var(--s1)); /* Largest Negative Value */

  --measure: 90ch;
  --grid-gap: var(--s2);
  --flow-space: var(--s2);
}
```
Multiplications of these base values are used to set  widths proportionally all over the site
```scss
.grid-row {
    margin: 0 auto var(--grid-gap) auto;
    max-width: calc(var(--measure) * 5);
}
```
---
### Gorko
CSS variables are passed to Gorko to create utility classes, this allows the values to be updated easily without re-compiling.
```scss
$gorko-colors: (
  'primary': var(--primary),
  'primary-shade': var(--primary-shade),
  'secondary': var(--secondary),
  'secondary-shade': var(--secondary-shade),
  'tertiary': var(--tertiary),
  'quaternary': var(--quaternary),
  'green': var(--green),
  'orange': var(--orange),
  'red': var(--red),
  'dark': var(--dark),
  'grey': var(--grey),
  'light': var(--light)
);
```
```scss
$gorko-size-scale: (
  '-500': var(--s-5),
  '-400': var(--s-4),
  '-300': var(--s-3),
  '-200': var(--s-2),
  '-100': var(--s-1),
  '100': var(--s0),
  '200': var(--s1),
  '300': var(--s2),
  '400': var(--s3),
  '500': var(--s4),
  '600': var(--s5),
  '700': var(--s6),
  'neg-600': var(--s-neg5),
  'neg-500': var(--s-neg4),
  'neg-400': var(--s-neg3),
  'neg-300': var(--s-neg2),
  'neg-200': var(--s-neg1),
  '000': 0,
);
```
Utility classes dynamically generated by Goko from these values, can be used to adjust elements
```scss
.grid-gap-000 / .grid-gap-300 / .grid-gap-400 / .grid-gap-500 / .grid-gap-600 
```
```scss
.pad-000 / .pad-300 / .pad-400 / .pad-500 / .pad-600 
```
```scss
.bg-primary / .bg-primary-shade / .bg-secondary / .bg-secondary-shade / .bg-tertiary 
```
The generated classes use CSS variables as values:
```scss
.gap-top--500 {
  margin-top: var(--s-5); 
}
```
```scss
.bg-quaternary {
  background: var(--quaternary); 
}
```
---
### Example
This set up below makes a full width row with three columns & no gap between the elements
```html
<article class="grid-row">
    <section class="grid align-full grid-gap-000">
        <figure><!-- --></figure> 
        <figure><!-- --></figure> 
        <figure><!-- --></figure>
    </section>
</article>
```
A wide row with padding all around
```html
<article class="grid-row">
    <section class="grid align-wide pad-500">
        <div><!-- --></div>
    </section>
</article>
```