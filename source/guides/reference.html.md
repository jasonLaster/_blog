---
title: Reference
class: guide
side_content: >
  <p class="version">Version <span>1.0.rc.2</span></p>
  <h2><a href="#ref-basic">Basic Usage</a></h2>
  <h3><a href="#ref-basic-settings">Basic Settings</a></h3>
  <ul>
    <li><a href="#ref-total-columns">$total-columns</a></li>
    <li><a href="#ref-column-width">$column-width</a></li>
    <li><a href="#ref-gutter-width">$gutter-width</a></li>
    <li><a href="#ref-grid-padding">$grid-padding</a></li>
  </ul>
  <h3><a href="#ref-basic-mixins">Basic Mixins</a></h3>
  <ul>
    <li><a href="#ref-container">container()</a></li>
    <li><a href="#ref-span-columns">span-columns()</a></li>
    <li><a href="#ref-omega">omega()</a></li>
    <li><a href="#ref-reset-columns">reset-columns()</a></li>
  </ul>
  <h2><a href="#ref-responsive">Responsive Grids</a></h2>
  <ul>
    <li><a href="#ref-media-layouts">$media-layout</a></li>
  </ul>
  <h3><a href="#ref-responsive-mixins">Responsive Mixins</a></h3>
  <ul>
    <li><a href="#ref-at-breakpoint">at-breakpoint()</a></li>
    <li><a href="#ref-layout">layout()</a></li>
    <li><a href="#ref-container-width">set-container-width()</a></li>
  </ul>
  <h2><a href="#ref-helper">Grid Helpers</a></h2>
  <h3><a href="#ref-helper-padding">Padding Mixins</a></h3>
  <ul>
    <li><a href="#ref-prefix">prefix()</a></li>
    <li><a href="#ref-suffix">suffix()</a></li>
    <li><a href="#ref-pad">pad()</a></li>
  </ul>
  <h3><a href="#ref-helper-margin">Margin Mixins</a></h3>
  <ul>
    <li><a href="#ref-pre">pre()</a></li>
    <li><a href="#ref-post">post()</a></li>
    <li><a href="#ref-squish">squish()</a></li>
    <li><a href="#ref-push">push()</a></li>
    <li><a href="#ref-pull">pull()</a></li>
  </ul>
  <h3><a href="#ref-helper-other">Other Mixins</a></h3>
  <ul>
    <li><a href="#ref-grid-background">susy-grid-background()</a></li>
  </ul>
  <h3><a href="#ref-helper-functions">Functions</a></h3>
  <ul>
    <li><a href="#ref-columns">columns()</a></li>
    <li><a href="#ref-gutter">gutter()</a></li>
    <li><a href="#ref-space">space()</a></li>
  </ul>
  <h3><a href="#ref-container-override">Container Override Settings</a></h3>
  <ul>
    <li><a href="#ref-container-width">$container-width</a></li>
    <li><a href="#ref-container-style">$container-style</a></li>
  </ul>
  <h3><a href="#ref-direction-override">Direction Override Settings</a></h3>
  <ul>
    <li><a href="#ref-from-direction">$from-direction</a></li>
    <li><a href="#ref-omega-float">$omega-float</a></li>
  </ul>
  <h3><a href="#ref-compass-options">Compass Options</a></h3>
  <ul>
    <li><a href="#ref-base-font-size">$base-font-size</a></li>
    <li><a href="#ref-browser-support">$legacy-support-for-...</a></li>
  </ul>
---

## <a href="#ref-basic" id="ref-basic">Basic Usage</a>

    :::scss
    @import 'susy';

- **Container**: The root element of a _Grid_.
- **Layout**: The total number of _Columns_ in a grid.
- **Grid Padding**: Padding on the sides of the _Grid_.
- **Context**: The number of _Columns_ spanned by the parent element.
- **Omega**: Any _Grid Element_ spanning the last _Column_ in its _Context_.

### <a href="#ref-basic-settings" id="ref-basic-settings">Basic Settings</a>

#### <a href="#ref-total-columns" id="ref-total-columns">Total Columns</a>
The number of Columns in your default Grid Layout.

    :::scss
    // $total-columns: <number>;
    $total-columns: 12;

- `<number>`: Unitless number.

#### <a href="#ref-column-width" id="ref-column-width">Column Width</a>
The width of a single Column in your Grid.

    :::scss
    // $column-width: <length>;
    $column-width: 4em;

- `<length>`: Length in any unit of measurement (em, px, %, etc).

#### <a href="#ref-gutter-width"id="ref-gutter-width">Gutter Width</a>
The space between Columns.

    :::scss
    // $gutter-width: <length>;
    $gutter-width: 1em;

- `<length>`: Units must match `$column-width`.

#### <a href="#ref-grid-padding" id="ref-grid-padding">Grid Padding</a>
Padding on the left and right of a Grid Container.

    :::scss
    // $grid-padding: <length>;
    $grid-padding: $gutter-width;  // 1em

- `<length>`: Units must match `$column-width`.

### <a href="#ref-basic-mixins" id="ref-basic-mixins">Basic Mixins</a>

#### <a href="#ref-container" id="ref-container">Container</a>
Establish the outer grid-containing element.

    :::scss
    // container([$<media-layout>]*)
    .page { @include container; }

- `<$media-layout>`: Optional media-layout shortcuts
  (see '[Responsive Grids][responsive]' below).
  Default: `$total-columns`.

[responsive]: #ref-responsive

#### <a href="#ref-span-columns" id="ref-span-columns">Span Columns</a>
Align an element to the Susy Grid.

    :::scss
    // span-columns(<$columns> [<omega> , <$context>, <$from>])
    nav { @include span-columns(3,12); }
    article { @include span-columns(9 omega,12); }

- `<$columns>`: The number of _Columns_ to span.
  - `<omega>`: Optional flag to signal the last element in a row.
- `<$context>`: Current nesting _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-omega" id="ref-omega">Omega</a>
Apply to any omega element as an override.

    :::scss
    // omega([<$from>])
    .gallery-image {
      @include span-columns(3,9); // each gallery-image is 3 of 9 cols.
      &:nth-child(3n) { @include omega; } // every third image completes a row.
    }

- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-reset-columns" id="ref-reset-columns">Reset Columns</a>
Resets an element to default block behaviour.

    :::scss
    // reset-columns([<$from>])
    article { @include span-columns(6); }     // articles are 6 cols wide
    #news article { @include reset-columns; } // but news span the full width
                                              // of their container

- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

## <a href="#ref-responsive" id="ref-responsive">Responsive Grids</a>

- **Breakpoint**: A min- or max- viewport width at which to change _Layouts_.
- **Media-Layout**: Shortcut for declaring _Breakpoints_ and _Layouts_ in Susy.

### <a href="#ref-media-layouts" id="ref-media-layouts">Media-Layouts</a>

    :::scss
    // $media-layout: <min-width> <layout> <max-width> <ie-fallback>;
    // - You must supply either <min> or <layout>.
    $media-layout: 12;          // Use 12-col layout at matching min-width.
    $media-layout: 30em;        // At min 30em, use closest fitting layout.
    $media-layout: 30em 12;     // At min 30em, use 12-col layout.
    $media-layout: 12 60em;     // Use 12 cols up to max 60em.
    $media-layout: 30em 60em;   // Between min 30em & max 60em, use closest layout.
    $media-layout: 30em 12 60em;// Use 12 cols between min 30em & max 60em.
    $media-layout: 60em 12 30em;// Same. Larger length will always be max-width.
    $media-layout : 12 lt-ie9;  // Output is included under `.lt-ie9` class,
                                // for use with IE conditional comments
                                // on the <html> tag.

**Note:**
The IE-fallback class does not include a leading "`.`" signifier,
but is simply the class name:
"`lt-ie9`", not "`.lt-ie9`".

### <a href="#ref-responsive-mixins" id="ref-responsive-mixins">Responsive Mixins</a>

#### <a href="#ref-at-breakpoint" id="ref-at-breakpoint">At-Breakpoint</a>
At a given min- or max-width Breakpoint, use a given Layout.

    :::scss
    // at-breakpoint(<$media-layout> [, <$font-size>]) { <@content> }
    @include at-breakpoint(30em 12) {
      .page { @include container; }
    }

- `<$media-layout>`: The _Breakpoint/Layout_ combo to use (see above).
- `<$font-size>`: When using EMs for your grid, the font size is important.
  Default: `$base-font-size`.
- `<@content>`: Nested `@content` block will use the given _Layout_.

#### <a href="#ref-layout" id="ref-layout">Layout</a>
Set an arbitrary Layout to use with any block of content.

    :::scss
    // layout(<$layout-cols>) { <@content> }
    @include layout(6) {
      .narrow-page { @include container; }
    }

- `<$layout-cols>`: The number of _Columns_ to use in the _Layout_.
- `<@content>`: Nested `@content` block will use the given _Layout_.

#### <a href="#ref-container-width" id="ref-container-width">Set Container Width</a>
Reset the width of a Container for a new Layout context.
Can be used when `container()` has already been applied to an element,
for DRYer output than simply using `container` again.

    :::scss
    // set-container-width([<$columns>])
    @include container;
    @include at-breakpoint(8) {
      @include set-container-width;
    }

- `<$columns>`: The number of _Columns_ to be contained.
  Default: Current value of `$total-columns` depending on _Layout_.

## <a href="#ref-helper" id="ref-helper">Grid Helpers</a>

### <a href="#ref-helper-padding" id="ref-helper-padding">Padding Mixins</a>

#### <a href="#ref-prefix" id="ref-prefix">Prefix</a>
Add Columns of empty space as `padding` before an element.

    :::scss
    // prefix(<$columns> [, <$context>, <$from>])
    .box { @include prefix(3); }

- `<$columns>`: The number of _Columns_ to be added as `padding` before.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-suffix" id="ref-suffix">Suffix</a>
Add columns of empty space as padding after an element.

    :::scss
    // suffix(<$columns> [, <$context>, <$from>])
    .box { @include suffix(2); }

- `<$columns>`: The number of _Columns_ to be added as `padding` after.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-pad" id="ref-pad">Pad</a>
Shortcut for adding both Prefix and Suffix `padding`.

    :::scss
    // pad([<$prefix>, <$suffix>, <$context>, <$from>])
    .box { @include pad(3,2); }

- `<$prefix>`: The number of _Columns_ to be added as `padding` before.
- `<$suffix>`: The number of _Columns_ to be added as `padding` after.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

### <a href="#ref-helper-margin" id="ref-helper-margin">Margin Mixins</a>

#### <a href="#ref-pre" id="ref-pre">Pre</a>
Add columns of empty space as margin before an element.

    :::scss
    // pre(<$columns> [, <$context>, <$from>])
    .box { @include pre(2); }

- `<$columns>`: The number of _Columns_ to be added as `margin` before.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-post" id="ref-post">Post</a>
Add columns of empty space as margin after an element.

    :::scss
    // post(<$columns> [, <$context>, <$from>])
    .box { @include post(3); }

- `<$columns>`: The number of _Columns_ to be added as `margin` after.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-squish" id="ref-squish">Squish</a>
Shortcut to add empty space as margin before and after an element.

    :::scss
    // squish([<$pre>, <$post>, <$context>, <$from>])
    .box { @include squish(2,3); }

- `<$pre>`: The number of _Columns_ to be added as `margin` before.
- `<$post>`: The number of _Columns_ to be added as `margin` after.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

#### <a href="#ref-push" id="ref-push">Push</a>
Identical to [pre](#ref-pre).

    :::scss
    // push(<$columns> [, <$context>, <$from>])
    .box { @include push(3); }

#### <a href="#ref-pull" id="ref-pull">Pull</a>
Add negative margins before an element, to pull it against the flow.

    :::scss
    // pull(<$columns> [, <$context>, <$from>])
    .box { @include pull(2); }

- `<$columns>`: The number of _Columns_ to be subtracted as `margin` before.
- `<$context>`: The _Context_.
  Default: `$total-columns`.
- `<$from>`: The origin direction of your document flow.
  Default: `$from-direction`.

### <a href="#ref-helper-other" id="ref-helper-other">Other Mixins</a>

#### <a href="#ref-grid-background" id="ref-grid-background">Susy Grid Background</a>
Show the Susy Grid as a background-image on any container.

    :::scss
    // susy-grid-background();
    .page { @include susy-grid-background; }

- If you are using the `<body>` element as your _Container_,
  you need to apply a background to the `<html>` element
  in order for this grid-background to size properly.
- Some browsers have trouble with sub-pixel rounding on background images.
  Use this for checking general spacing, not pixel-exact alignment.
  Susy columns tend to be more accurate than gradient grid-backgrounds.

### <a href="#ref-helper-functions" id="ref-helper-functions">Functions</a>

Where a mixin returns property/value pairs, functions return simple values
that you can put where you want, and use for advanced math.

#### <a href="#ref-columns" id="ref-columns">Columns</a>
Similar to [span-columns](#ref-span-columns) mixin,
but returns the math-ready `%` multiplier.

    :::scss
    // columns(<$columns> [, <$context>])
    .item { width: columns(3,6); }

- `<$columns>`: The number of _Columns_ to span,
- `<$context>`: The _Context_.
  Default: `$total-columns`.

#### <a href="#ref-gutter" id="ref-gutter">Gutter</a>
The `%` width of one gutter in any given context.

    :::scss
    // gutter([<$context>])
    .item { margin-right: gutter(6) + columns(3,6); }

- `<$context>`: The _Context_.
  Default: `$total-columns`.

#### <a href="#ref-space" id="ref-space">Space</a>
Total `%` space taken by Columns, including internal AND external gutters.

    :::scss
    // space(<$columns> [, <$context>])
    .item { margin-right: space(3,6); }

- `<$columns>`: The number of _Columns_ to span,
- `<$context>`: The _Context_.
  Default: `$total-columns`.

### <a href="#ref-container-override" id="ref-container-override">Container Override Settings</a>

#### <a href="#ref-container-width" id="ref-container-width">Container Width</a>
Override the total width of your grid with an arbitrary length.

    :::scss
    // $container-width: <length> | <boolean>;
    $container-width: false;

- `<length>`: Length in em, px, %, etc.
- `<boolean>`: True or false.

#### <a href="#ref-container-style" id="ref-container-style">Container Style</a>
Override the type of shell containing your grid.

    :::scss
    // $container-style: <style>;
    $container-style: magic;

- `<style>`: `magic` | `static` | `fluid`.
  - `magic`: Susy's magic grid has a set width,
    but becomes fluid rather than overflowing the viewport at small sizes.
  - `static`: Susy's static grid will retain the width defined in your settings
    at all times.
  - `fluid`: Susy's fluid grid will always be based on the viewport width.
    The percentage will be determined by your grid settings,
    or by `$container-width`, if either is set using `%` units.
    Otherwise it will default to `auto` (100%).

### <a href="#ref-direction-override" id="ref-direction-override">Direction Override Settings</a>

#### <a href="#ref-from-direction" id="ref-from-direction">From Direction</a>
The side of the Susy Grid from which the flow starts.
For ltr documents, this is the left.

    :::scss
    // $from-direction: <direction>;
    $from-direction: left;

- `<direction>`: `left` | `right`

#### <a href="#ref-omega-float" id="ref-omega-float">Omega Float</a>
The direction that Omega elements should be floated.

    :::scss
    // $omega-float: <direction>;
    $omega-float: opposite-position($from-direction);

- `<direction>`: `left` | `right`

### <a href="#ref-compass-options" id="ref-compass-options">Compass Options</a>

#### <a href="#ref-base-font-size" id="ref-base-font-size">Base Font Size</a>
From the [Compass Vertical Rhythm][rhythm] module,
Susy uses your base font size to help manage
em-based media-queries.

    :::scss
    // $base-font-size: <px-size>;
    $base-font-size: 16px;

- `<px-size>`: Any length in `px`.
  This will not actually effect your font size
  unless you use other Vertical Rhythm tools,
  we just need to know.
  See [Compass Docs][base-font-size] for further usage details.

[rhythm]: http://compass-style.org/reference/compass/typography/vertical_rhythm/
[base-font-size]: http://compass-style.org/reference/compass/typography/vertical_rhythm/#const-base-font-size

#### <a href="#ref-browser-support" id="ref-browser-support">Browser Support</a>
Susy recognizes all the [Compass Browser Support][support] variables,
although only IE6 and IE7 have special cases attached to them currently.

    :::scss
    // $legacy-support-for-ie  : <boolean>;
    // $legacy-support-for-ie6 : <boolean>;
    // $legacy-support-for-ie7 : <boolean>;
    $legacy-support-for-ie  : true;
    $legacy-support-for-ie6 : $legacy-support-for-ie;
    $legacy-support-for-ie7 : $legacy-support-for-ie;

- `<boolean>`: `true` | `false`

[support]: http://compass-style.org/reference/compass/support/
