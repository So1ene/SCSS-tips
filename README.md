# SCSS Breakpoint Mixin

Please read the "SCSS Naming Convention" section first.
<br />

-   **mobile-S:** 0 - 374px (Most common devices view at **320px**)
-   **mobile-M:** 374px - 424px (Most common devices view at **375px**)
-   **mobile-L:** 424px - 600px (Most common devices view at **480px**)
-   **tablet:** 600px - 1020px (Most common devices view at **720px** & **768px**)
-   **laptop-S:** 1020 - 1300px (Most common devices view at **1024px** &** 1280px**)
-   **laptop-M:** 1300 - 1500px (Most common devices view at **1366px** & **1440px**)
-   **laptop-L:** 1500px + (Most common devices view at** 1600px** & **1920px**)
<br />
-   **mobile-all:** 0 - 600px
-   **mobile-tablet:** 0 - 1020px
<br />
-   **laptop-tablet:** 600px +
-   **laptop-all:** 1020px +

Make sure to check every 'common device views' to be sure they all look good

```css
    // Breakpoints mixin (SCSS)

@mixin breakpoint($breakpoint) {

    @if $breakpoint == mobile-S {
        @media only screen and (max-width: 374px) { @content }; // mobile-S: 0 - 374px (commonly 320px)
    }
    @if $breakpoint == mobile-M {
        @media only screen and (min-width: 374px) and (max-width: 424px) { @content }; // mobile-M: 374px - 424px (commonly 375px)
    }
    @if $breakpoint == mobile-L {
        @media only screen and (min-width: 424px) and (max-width: 600px) { @content }; // mobile-L:   424px - 600px (commonly 480px)
    }
    @if $breakpoint == tablet {
        @media only screen and (min-width: 600px)and (max-width: 1020px) { @content }; // tablet: 600px - 1020px (commonly 720px & 768px)
    }
    @if $breakpoint == laptop-S {
        @media only screen and (min-width: 1020px) and (max-width: 1300px) { @content }; // laptop-S: 1020 - 1300px (commonly 1024px & 1280px)
    }
    @if $breakpoint == laptop-M {
        @media only screen and (min-width: 1300px) and (max-width: 1500px) { @content }; // laptop-M: 1300 - 1500px (commonly 1366px & 1440px)
    }
    @if $breakpoint == laptop-L {
        @media only screen and (min-width: 1500px) { @content }; // laptop-L: 1500px + (commonly 1600px & 1920px)
    }

    @if $breakpoint == mobile-all {
	@media only screen and (max-width: 600px) { @content }; // All mobile breakpoints
	}
    @if $breakpoint == mobile-tablet {
	@media only screen and (max-width: 1020px) { @content }; // All mobile breakpoints + tablet
    }
    @if $breakpoint == laptop-all {
	@media only screen and (min-width: 1020px) { @content }; // All laptop breakpoints
    }
    @if $breakpoint == laptop-tablet {
    	@media only screen and (min-width: 600px) { @content }; // All laptop breakpoints + tablet
    }
```

!! **Note: **
!! This is just a guide/starting point, you can add more breakpoints on a project by project basis. For example:

```css
@if $breakpoint == mobile-landscape {
  @media only screen and (max-height: 482px) and (max-width: 1020px) {
    @content;
  } // Landscape phone
}

@if $breakpoint == mobile-XL {
  @media only screen and (min-width: 500px) and (max-width: 700px) {
    @content;
  } // Extremely large phone or small tablet
}
```

## Example usage of the mixin:

```css
.block {
  width: 600px;
  display: none;

  @include breakpoint(mobile-all) {
    display: block;
  }

  &__image {
    width: 500px;

    @include breakpoint(mobile-M) {
      width: 400px;
    }

    @include breakpoint(mobile-S) {
      width: 300px;
    }
  }
}
```

Keep the "@include breakpoint()" texts at the bottom of each element after their styling for the sake of legibility

          
