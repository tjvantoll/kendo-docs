---
title: Troubleshooting
slug: mvc-troubleshooting
publish: true
---

# Troubleshooting

This help topic lists some common problems that may occur while working with Kendo UI Complete for ASP.NET MVC and their solutions. In addition you can check
the general [Kendo UI troubleshooting help topic](/getting-started/troubleshooting).

## JavaScript error telling that the kendo widgets are unavailable or undefined

If jQuery is included twice in the page all existing jQuery plugins (such as Kendo UI) will be wiped out. In this case the following JavaScript errors will be thrown (depending on the browser):

* TypeError: Object #<Object> has no method 'kendoGrid' (in Google Chrome)
* TypeError: jQuery("#Grid").kendoGrid is not a function (in FireFox)
* Object doesn't support property or method 'kendoGrid' (in Internet Explorer 9+)
* Object doesn't support this property or method (in older versions of Internet Explorer)

> **Note**: All Kendo widgets will be affected by this problem, not just the Kendo Grid. Just the error message will be different e.g. "kendoChart is not a function" or "Object has no method kendoEditor".

### Solution

Make sure jQuery is not included more than once in your page. Remove any duplicate `script` references to jQuery. If the application is also using Telerik Extensions for ASP.NET MVC tell the `ScriptRegistrar` not to include jQuery:

    Html.Telerik().ScriptRegistrar().jQuery(false)

If using ASP.NET bundles make sure the `Scripts.Render("~/bundles/jquery")` block appears **before** the Kendo JavaScript files. In that case you should not include jQuery as a `script` element.

## JavaScript error that jQuery is unavailable or undefined

If jQuery is not included (or included after) the Kendo UI widgets will not function as expected. The following JavaScript errors will be thrown (depending on the browser):

* ReferenceError: jQuery is not defined (in Google Chrome and FireFox)
* 'jQuery' is undefined (in Internet Explorer)

### Solution

Include that jQuery is included **before** the Kendo JavaScript files. If using ASP.NET bundles move the `Scripts.Render("~/bundles/jquery")` block **before** the Kendo JavaScript files.

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
