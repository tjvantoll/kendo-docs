---
title: Troubleshooting
slug: mvc-troubleshooting
publish: true
---

# Troubleshooting

This page provides solutions for common problems you may encounter while working with Kendo UI Complete for ASP.NET MVC. In addition you could check the general [Kendo UI troubleshooting help topic](/getting-started/troubleshooting).

## JavaScript error that jQuery is unavailable or undefined

If jQuery is not included (or is included after the Kendo JavaScript files) the Kendo UI widgets will not function as expected.
Check the [Kendo UI troubleshooting help topic](/getting-started/troubleshooting#javascript-error-that-jquery-is-unavailable-or-undefined) for more symptoms.

Make sure that jQuery is included **before** the Kendo JavaScript files. If using ASP.NET bundles move the `Scripts.Render("~/bundles/jquery")` block **before** the Kendo JavaScript files.

## JavaScript error that Kendo widgets are unavailable or undefined

If jQuery is included more than once in the page all existing jQuery plugins (including Kendo UI) will be wiped out. Will also occur
if the [required Kendo JavaScript files](/getting-started/javascript-dependencies) are not included.

Check the [Kendo UI troubleshooting help topic](/getting-started/troubleshooting#javascript-error-that-kendo-widgets-are-unavailable-or-undefined) for more symptoms.

Make sure jQuery is not included more than once in your page. Remove any duplicate `script` references to jQuery. Include all [required Kendo JavaScript files](/getting-started/javascript-dependencies).

If the application is also using Telerik Extensions for ASP.NET MVC tell the `ScriptRegistrar` not to include jQuery:

    Html.Telerik().ScriptRegistrar().jQuery(false)

If using ASP.NET bundles make sure the `Scripts.Render("~/bundles/jquery")` block appears **before** the Kendo JavaScript files. In that case you should not include jQuery as a `script` element.

## Visual Studio IntelliSense does not show the Kendo HtmlHelper extension method

### Solution

1. Make sure the `Kendo.Mvc.UI` namespace is imported in `web.config`.
    * If you are using the WebForms view engine open the **web.config** file in the root folder of your application. Add
     `<add namespace="Kendo.Mvc.UI" />` before the closing `namespaces` tag:

             <namespaces>
                 <add namespace="System.Web.Mvc" />
                 <add namespace="System.Web.Mvc.Ajax" />
                 <add namespace="System.Web.Mvc.Html" />
                 <add namespace="System.Web.Routing" />
                 <add namespace="System.Linq" />
                 <add namespace="System.Collections.Generic" />
                 <add namespace="Kendo.Mvc.UI" />
             </namespaces>
    * If you are using the Razor view engine open the **web.config** file which is in the **Views** folder
     of your application.Add `<add namespace="Kendo.Mvc.UI" />` before the closing `namespaces` tag:

             <system.web.webPages.razor>
                 <pages pageBaseType="System.Web.Mvc.WebViewPage">
                     <namespaces>
                         <add namespace="System.Web.Mvc" />
                         <add namespace="System.Web.Mvc.Ajax" />
                         <add namespace="System.Web.Mvc.Html" />
                         <add namespace="System.Web.Routing" />
                         <add namespace="Kendo.Mvc.UI" />
                     </namespaces>
                 </pages>
             </system.web.webPages.razor>
2. Rebuild your solution.
3. Close and open again the view you were editing. Intellisense should be working now.
