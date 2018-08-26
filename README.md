# Style Guide #

SCSS based style guide to be used as base for projects.

# Variables #

Define default colors and fonts for app. 

## App Variables ##

```
$theme: default;
```

## Colors ##
```
//background
$dominant-color: #000;
$complimentory-color: #000;
$ternary-color: #000;

//text and background
$primary-color:
$success-color: 
$danger-color: red;
$warning-color: yellow;
$disabled-color: 

//Text
$text-color-primary: #333333;
$text-color-secondary: 
$link-color-primary: 
$link-color-secondary: 
$header-color:
$menu-item-color
```

## Font Family ##
```
$font-primary: 
$font-secondary: 
$header-font
```

## Breakpoints ##
```
$breakpoint-tiny: 
$breakpoint-small
$breakpoint-medium: 
$breakpoint-large
```

## Size ##
```
$font-size-base:              1rem !default; $font-size-lg:                ($font-size-base * 1.25) !default;
$font-size-sm:                ($font-size-base * .875) !default;
$spacer:                      1rem !default;

$line-height-base:            1.5 !default;

$h1-font-size:                $font-size-base * 2.5 !default;
$h2-font-size:                $font-size-base * 2 !default;
$h3-font-size:                $font-size-base * 1.75 !default;
$h4-font-size:                $font-size-base * 1.5 !default;
$h5-font-size:                $font-size-base * 1.25 !default;
$h6-font-size:                $font-size-base !default;

$headings-margin-bottom:      ($spacer / 2) !default;
```

font-weight

```
$font-weight-lighter:         lighter !default;
$font-weight-light:           300 !default;
$font-weight-normal:          400 !default;
$font-weight-bold:            700 !default;
$font-weight-bolder:          bolder !default;
```

## z-index ##

```
$zindex-dropdown:          1000 !default;
$zindex-sticky:            1020 !default;
$zindex-fixed:             1030 !default;
$zindex-modal-backdrop:    1040 !default;
$zindex-modal:             1050 !default;
$zindex-popover:           1060 !default;
$zindex-tooltip:           1070 !default;
```

# Mixins #

Useful mixins.  

## Screen ##

```
/* 
* @params: 
*   size: tiny|small|medium|large
*   type (optional - default max): max|min
*/

@include screen($size: medium, $type: max)
```

## Centering Elements ##

```
/* 
* @params: 
*   direction: vertical|horizontal|both
*/

@include center-abs($direction: vertical);

@include center-flex($direction: vertical);
```

## Size ##

```
/*
* @params: 
*   $size: size in px to be converted
*   $base (optional - default 16px): base in px to be used for calculation
*/
@include rem($size: 18px, $base: 16px);

@include em($size: 18px, $base: 16px);
```

## Animation ##

```
/*
* @params: 
*   $name: Animation name 
*/

@include keyframes($name: fade-out) {
  0% { opacity: 1; }
  90% { opacity: 0; }
}

/*
* @params: 
*   $value: value for animation property 
*/
@include animation($value: 'fade-out 5s 3');

```

## Clearfix ##

```
@include clearfix;

@mixin clearfix {
  &:after {
    content: "";
    display: table;
    clear: both;
  }
}
```

# Styles #

## Typography ##
```
body{
    font-size: 16px;
    font-family: $font-primary;
}

//h1 - h6 styling
#heading-tags: h1, h2, h3, h4, h5, h6;
@each tag in heading-tags {
    .#{tag}{
        font-size: $#{tag}-font-size;    
        margin-bottom: $headings-margin-bottom;
    }
}

#font-sizes: base, lg, sm;
p{
    font-size: $font-size-base;
    @each size in $font-sizes{
        &.text--#{size}{
            font-size: $font-size-#{size};
        }
    }
    
}
```

## Button ##

# Layout #

## Container ##