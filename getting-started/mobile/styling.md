---
title: Styling
meta_title: User guide to styling Kendo UI Mobile applications
meta_description: How to style Kendo UI Mobile applications with CSS.
slug: mobile-styling
publish: true
---

# Styling Kendo UI Mobile

<br/>
## Kendo UI Mobile CSS Files

<br/>
By default Kendo UI Mobile is shipped with several separate CSS files:

* **kendo.mobile.all.min.css** - is the default one and includes all supported themes, along with the Flat skin, common and icon CSSes.
* **kendo.mobile.\*.min.css** - separate CSS files for every supported platform, which (every one) are self-sufficient - they include the needed common and icon CSS.
* **kendo.mobile.common.min.css** - common and icon CSS needed for the Kendo UI Mobile theme skeleton - use this one if you want to start a skin from scratch.
* **kendo.icenium.min.css** - Separate CSS build for Icenium - it includes only the iOS and Android themes.

All themes and skins ***require*** the **images** subfolder, which contains a mask for the iOS back button, icon fonts and the WP8 PhoneGap icon workaround images.

## Kendo UI Mobile ThemeBuilder

<br/>
Kendo UI Mobile's themes are designed to be easily customizable with different colors and backgrounds.
To further ease the task, we also provide a special tool called [Kendo UI Mobile ThemeBuilder](http://demos.kendoui.com/mobilethemebuilder/index.html).
It is very simple to use - just drag and drop your chosen colors, gradients, patterns and font styles onto the platform theme you need restyled and finally click the export button to get
the needed CSS stylesheet.

## Changing Flat skin active color

<br/>
The Flat skin shipped with Kendo UI Mobile Q2 2013, was created to provide maximum performance. Also the active color of the skin can be easily changed with several CSS rules.

### Change the Flat skin active background to blue

    .km-flat .km-switch-handle,
    .km-flat .k-slider-selection,
    .km-flat .km-switch-background
    {
        color: #369;
    }

    .km-flat .km-loader,
    .km-flat .km-rowinsert,
    .km-flat .km-state-active,
    .km-flat .km-scroller-pull,
    .km-flat .k-slider-selection,
    .km-flat .km-touch-scrollbar,
    .km-flat .km-pages .km-current-page,
    .km-flat .k-slider .k-draghandle,
    .km-flat .k-slider .k-draghandle:hover,
    .km-flat .km-tabstrip .km-state-active,
    .km-flat .km-scroller-refresh.km-load-more,
    .km-flat .km-popup .k-state-hover,
    .km-flat .km-popup .k-state-focused,
    .km-flat .km-popup .k-state-selected,
    .km-flat .km-actionsheet > li > a:active,
    .km-flat .km-actionsheet > li > a:hover,
    .km-flat li.km-state-active .km-listview-link,
    .km-flat li.km-state-active .km-listview-label,
    .km-flat .km-listview-label input[type=radio]:checked,
    .km-flat .km-listview-label input[type=checkbox]:checked
    {
        background: #369;
    }

    .km-flat .km-filter-wrap > input:focus
    {
        border-color: #369;
    }

### Change the Flat skin active background to red and the color to beige

    .km-flat .km-badge,
    .km-flat .km-rowinsert,
    .km-flat .km-rowdelete,
    .km-flat .km-state-active,
    .km-flat .km-switch-label-on,
    .km-flat .km-switch-label-off,
    .km-flat .km-tabstrip .km-button,
    .km-flat .km-popup .k-item,
    .km-flat .km-actionsheet > li > a,
    .km-flat .km-tabstrip .km-state-active,
    .km-flat .k-slider .k-draghandle,
    .km-flat .k-slider .k-draghandle:hover,
    .km-flat .km-scroller-pull .km-icon,
    .km-flat .km-popup.km-pane .km-navbar,
    .km-flat .km-popup.km-pane .km-toolbar,
    .km-flat .km-popup.km-pane .km-tabstrip,
    .km-flat .km-popup .k-state-hover,
    .km-flat .km-popup .k-state-focused,
    .km-flat .km-popup .k-state-selected,
    .km-flat .km-actionsheet > li > a:active,
    .km-flat .km-actionsheet > li > a:hover,
    .km-flat li.km-state-active .km-listview-link,
    .km-flat li.km-state-active .km-listview-label,
    .km-flat .km-state-active .km-listview-link:after
    {
        color: #fff3c9;
    }

    .km-flat .km-loader > *:not(h1),
    .km-flat .km-filter-wrap > input,
    .km-flat .km-switch-handle.km-state-active,
    .km-root .km-flat .km-scroller-refresh span:not(.km-template),
    .km-flat .km-listview-label input[type=checkbox]:checked:after
    {
        background: #fff3c9;
    }

    .km-flat .km-switch-handle,
    .km-flat .k-slider-selection,
    .km-flat .km-switch-background
    {
        color: #ff6363;
    }

    .km-flat .km-loader,
    .km-flat .km-rowinsert,
    .km-flat .km-state-active,
    .km-flat .km-scroller-pull,
    .km-flat .k-slider-selection,
    .km-flat .km-touch-scrollbar,
    .km-flat .km-pages .km-current-page,
    .km-flat .k-slider .k-draghandle,
    .km-flat .k-slider .k-draghandle:hover,
    .km-flat .km-tabstrip .km-state-active,
    .km-flat .km-scroller-refresh.km-load-more,
    .km-flat .km-popup .k-state-hover,
    .km-flat .km-popup .k-state-focused,
    .km-flat .km-popup .k-state-selected,
    .km-flat .km-actionsheet > li > a:active,
    .km-flat .km-actionsheet > li > a:hover,
    .km-flat li.km-state-active .km-listview-link,
    .km-flat li.km-state-active .km-listview-label,
    .km-flat .km-listview-label input[type=radio]:checked,
    .km-flat .km-listview-label input[type=checkbox]:checked
    {
        background: #ff6363;
    }

    .km-flat .km-filter-wrap > input:focus
    {
        border-color: #ff6363;
    }
