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
$dominant-color:                 #F2ECE6 !default;
$complimentory-color:            #222222 !default;
$ternary-color:                  #C19C7A !default;
$white-color:                    #ffffff !default;
$black-color:                    #000000 !default;
$blackish-color:                 #333333 !default;

//text and background
$primary-color:                  #CDE5FE !default;
$success-color:                  #D5EDDB !default;
$danger-color:                   #D5EDDB !default;
$warning-color:                  #FFF2CF !default;
$disabled-color:                 #E2E3E5 !default; 

//Text
$text-color-primary:             #333333 !default;
$text-color-secondary:           #888888 !default;
$link-color-primary:             #5CA7DA !default;
$link-color-secondary:           #EBA559 !default;
$header-color:                   #C19C7A !default;
$menu-item-color:                $primary-color;

//Buttons
$button-bg-color-default:        $white-color;
$button-border-color-default:    $blackish-color;
```

## Font Family ##
```
//Font family
//Font family
$font-primary:                   'Proxima Nova Soft', 'Helvetica Neue', sans-serif;
$font-secondary:                 "Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
$header-font:                    'Proxima Nova Soft', 'Helvetica Neue', sans-serif;
```

## Breakpoints ##
```
$breakpoint-tiny:               400px;
$breakpoint-small:              576px;
$breakpoint-medium:             768px;
$breakpoint-large:              992px;
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

$button-padding:              .75 rem .5rem;
$button-border-radius-size:   .3125rem;
```

## font-weight ##

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

## Media Queries ##

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

## Loading Themes ##
Loads variables for new theme.
```
/*
* @params: 
*   $name: name of the theme. This name will be applied to $theme variable. 
*   @baseUrl (optional. Default to ../variables): prefix for url to load theme from.
*/
@include loadTheme($name: dark, $baseUrl);
```


# Functions #

## Size ##
```
/*
* @params: 
*   $size: size in px to be converted
*   $base (optional - default 16px): base in px to be used for calculation
*/
rem($size: 18px, $base: 16px);

em($size: 18px, $base: 16px);
```

## Increase z-index ##
Increases z-index of passed z-index variable;
```
/*
* @params:
*   $name: name of the z-index variable. ($zindex-dropdown|$zindex-sticky|$zindex-fixed|$zindex-modal-backdrop|$zindex-modal|$zindex-popover|
$zindex-tooltip)
*/
incrementZIndex($name);
```

# Styles #

## Typography ##
```
//h1 - h6 styling

@for $i from 1 through 6 {
    h#{$i}{
        font-size: $h#{$i}-font-size;    
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

```
$button-class-postfix: primary, success, danger, warning; 
button{
    background-color: $button-bg-color-default;
    padding: $button-padding;
    border: 1px solid $button-border-color-default;
    border-radius: $button-border-radius-size;
    $color: $text-color-primary;
    &:disabled{
        background-color: $disabled-color;
        border-color: darken($disabled-color, 15%);
    }
    &:hover{
        background-color: darken($disabled-color, 15%);
        background-color: darken($disabled-color, 30%)
    }
    @each $postfix in $button-classes{
        &.btn-#{$postfix}{
            background-color: #{$postfix}-color;
            border-color: darken(#{$postfix}-color, 15%);
            color: $white-color;
            &:hover{
                background-color: darken(#{$postfix}-color, 15%);
                background-color: darken(#{$postfix}-color, 30%)
            }
        }
    }   
}
```
# Layout #

## Container ##