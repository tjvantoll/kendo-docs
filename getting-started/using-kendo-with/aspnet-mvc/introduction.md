---
title: Introduction
slug: mvc-introduction
publish: true
---

## What is ASP.NET MVC

 [ASP.NET MVC](http://www.asp.net/mvc/) is a free and fully supported Microsoft framework for building web applications that use the model-view-controller pattern.
ASP.NET MVC is built on top of the [ASP.NET](http://www.asp.net/) framework.

## What is Kendo UI Complete for ASP.NET MVC

Kendo UI Complete for ASP.NET MVC is a set of HTML helpers which help you configure Kendo UI widgets by using server-side code in ASP.NET MVC applications.

Kendo UI Complete for ASP.NET MVC provides the following benefits:

*   Built on top of the Kendo UI HTML5 framework and jQuery
*   Leverages ASP.NET MVC features - data annotation, editor and display templates, validation, authorization
*   Supports the WebForms and Razor view engines

## Downloading and Installing Kendo UI Complete for ASP.NET MVC

You can choose to download either the MSI installer or the ZIP file. If you choose the former just run the MSI file to install it. If you choose to
download the ZIP file simply extract it to your preferred location.

The distribution files contain the following:

*   **\js** - Kendo UI minified JavaScript files.
*   **\styles** - Kendo UI minified CSS files and background images used by the themes.
*   **\src** - Complete JavaScript, CSS and C# source code.
> **Note**: The source code is available only in the commercial distribution of Kendo UI Complete for ASP.NET MVC.
*   **\wrappers\aspnetmvc\Binaries** - Kendo UI Complete for ASP.NET MVC assemblies.
*   **\wrappers\aspnetmvc\Examples** - a sample ASP.NET MVC application.
*   **\wrappers\aspnetmvc\EditorTemplates** - ready-to-use editor templates based on various Kendo UI widgets.
*   **\wrappers\aspnermvc\LegacyThemes** - Kendo UI themes ported from [Telerik Extensions for ASP.NET MVC](http://www.telerik.com/products/aspnet-mvc.aspx) themes.

## Running the sample application

You can find a sample ASP.NET MVC application in the **\wrappers\aspnetmvc\Examples** folder.
It contains the following:

*   **Areas/aspx** - WebForm views
*   **Areas/razor** - Razor views
*   **Controllers** - controller classes
*   **Models** - model classes

## Kendo UI for ASP.NET MVC Visual Studio Extensions

You can download the [Kendo UI for ASP.NET MVC Visual Studio Extensions package](http://visualstudiogallery.msdn.microsoft.com/65b78c2c-951e-43a8-bae7-f9039f59fb9b). It adds a
few project templates and wizards that allow the following:

* Create a new Kendo ASP.NET MVC 3/4 application
* Add Kendo UI Complete for ASP.NET MVC to an existing application
* Configure a Kendo UI ASP.NET MVC application
* Automatically check and update Kendo UI Complete for ASP.NET MVC

## Manually add Kendo UI to ASP.NET MVC applications

### Using Kendo UI in ASP.NET MVC 3 application

1.  Create a new ASP.NET MVC 3 application from Visual Studio or open an existing one.

2.  Add a reference to **\wrappers\aspnetmvc\Binaries\Mvc3\Kendo.Mvc.dll**.

3.  Copy the Kendo UI JavaScript files from the **\js** folder of the installation to the **Scripts** folder of your application.
If you want to use CDN skip steps 3, 4 and 5 and check the [Using CDN](#using-cdn) section.

4.  Copy the Kendo UI CSS files and folders from the **\styles** folder of the installation to the **Content** folder of your application. If you want to use only one theme
copy **kendo.common.min.css**, the theme file (e.g. **kendo.default.min.css**), the theme folder (e.g. **Default**) and the **textures** folder.

5.  Configure your ASP.NET MVC layout page to include the Kendo UI Web JavaScript and CSS files:
    * WebForms:

             <link href="<%= Url.Content("~/Content/kendo.common.min.css") %>" rel="stylesheet" type="text/css" />
             <link href="<%= Url.Content("~/Content/kendo.default.min.css") %>" rel="stylesheet" type="text/css" />
             <script src="<%= Url.Content("~/Scripts/jquery.min.js") %>"></script>
             <script src="<%= Url.Content("~/Scripts/kendo.web.min.js") %>"></script>
             <script src="<%= Url.Content("~/Scripts/kendo.aspnetmvc.min.js") %>"></script>
    * Razor:

             <link rel="stylesheet" href="@Url.Content("~/Content/kendo.common.min.css")">
             <link rel="stylesheet" href="@Url.Content("~/Content/kendo.default.min.css")">
             <script src="@Url.Content("~/Scripts/jquery.min.js")"></script>
             <script src="@Url.Content("~/Scripts/kendo.web.min.js")"></script>
             <script src="@Url.Content("~/Scripts/kendo.aspnetmvc.min.js")"></script>

6.  Configure your ASP.NET MVC layout page to include the Kendo UI DataViz JavaScript and CSS files. **Important**: If you want to use Kendo UI Web and DataViz at the same time you should include **kendo.all.min.js** instead of **kendo.web.min.js** and **kendo.dataviz.min.js**. You
    can also create a custom JavaScript file using the [Custom Download Builder](http://www.kendoui.com/custom-download).

    * WebForms:

             <link href="<%= Url.Content("~/Content/kendo.dataviz.min.css") %>" rel="stylesheet" type="text/css" />
             <script src="<%= Url.Content("~/Scripts/jquery.min.js") %>"></script>
             <script src="<%= Url.Content("~/Scripts/kendo.dataviz.min.js") %>"></script>
             <script src="<%= Url.Content("~/Scripts/kendo.aspnetmvc.min.js") %>"></script>
    * Razor:

             <link href="@Url.Content("~/Content/kendo.dataviz.min.css")" rel="stylesheet" type="text/css" />
             <script src="@Url.Content("~/Scripts/jquery.min.js")"></script>
             <script src="@Url.Content("~/Scripts/kendo.dataviz.min.js")"></script>
             <script src="@Url.Content("~/Scripts/kendo.aspnetmvc.min.js")"></script>

7. Add a reference to the **Kendo.Mvc.UI** namespace to your **web.config**. Then the `Kendo` HtmlHelper extension would
be availble in your views. Rebuild your project after adding the namespace to the web.config (required for Visual Studio to show intellisense for Kendo.Mvc.UI).
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

8.  Use any Kendo UI HtmlHelper extension:
    * WebForms

            <%: Html.Kendo().DatePicker().Name("Birthday") %>
    * Razor

            @(Html.Kendo().DatePicker().Name("Birthday"))

### Using Kendo UI in ASP.NET MVC 4 application

1. Create a new ASP.NET MVC 4 application from Visual Studio or open an existing one.

2. Add a reference to **\wrappers\aspnetmvc\Binaries\Mvc3\Kendo.Mvc.dll**.
> **Important:** Kendo UI Complete for ASP.NET MVC currently ships a single assembly which works in both ASP.NET MVC 3 and 4 applications.

3. Make sure the following section is present in your **web.config**. Add if not present:

        <configuration>
          <!--... elements deleted for clarity ...-->
          <runtime>
            <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
              <dependentAssembly>
                <assemblyIdentity name="System.Web.Helpers" publicKeyToken="31bf3856ad364e35" />
                <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="2.0.0.0" />
              </dependentAssembly>
              <dependentAssembly>
                <assemblyIdentity name="System.Web.Mvc" publicKeyToken="31bf3856ad364e35" />
                <bindingRedirect oldVersion="1.0.0.0-4.0.0.0" newVersion="4.0.0.0" />
              </dependentAssembly>
              <dependentAssembly>
                <assemblyIdentity name="System.Web.WebPages" publicKeyToken="31bf3856ad364e35" />
                <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="2.0.0.0" />
              </dependentAssembly>
            </assemblyBinding>
          </runtime>
        </configuration>

4.  Copy the Kendo UI JavaScript files from the **\js** folder of the installation to the **Scripts** folder of your application.
If you want to use CDN skip steps 3, 4 and 5 and check the [Using CDN](#using-cdn) section.

5.  Copy the Kendo UI CSS files and folders from the **\styles** folder of the installation to the **Content** folder of your application. If you want to use only one theme
copy **kendo.common.min.css**, the theme file (e.g. **kendo.default.min.css**), the theme folder (e.g. **Default**) and the **textures** folder.

6.  Create bundles for the CSS and JavaScript files of Kendo UI:

        public static void RegisterBundles(BundleCollection bundles)
        {
            // The jQuery bundle
            bundles.Add(new ScriptBundle("~/bundles/jquery").Include(
                            "~/Scripts/jquery-1.*"));

            // The Kendo JavaScript bundle
            bundles.Add(new ScriptBundle("~/bundles/kendo").Include(
                    "~/Scripts/kendo.web.*", // or kendo.all.* if you want to use Kendo UI Web and Kendo UI DataViz
                    "~/Scripts/kendo.aspnetmvc.*"));

            // The Kendo CSS bundle
            bundles.Add(new StyleBundle("~/Content/kendo").Include(
                    "~/Content/kendo.common.*",
                    "~/Content/kendo.default.*"));

            // Clear all items from the default ignore list to allow minified CSS and JavaScript files to be included in debug mode
            bundles.IgnoreList.Clear();

            // Add back the default ignore list rules sans the ones which affect minified files and debug mode
            bundles.IgnoreList.Ignore("*.intellisense.js");
            bundles.IgnoreList.Ignore("*-vsdoc.js");
            bundles.IgnoreList.Ignore("*.debug.js", OptimizationMode.WhenEnabled);
        }

7.  Register the bundles in your layout page at the end of the `head` element. **Remove any existing jQuery bundle registration at end of the `body` element of the page.** **Note:** If you don't want to use ASP.NET bundles perform steps 5 and 6 from the [Using Kendo UI in ASP.NET MVC 3 application](#using-kendo-ui-in-asp.net-mvc-3-application) section.
    * WebForms:

            <head>
                <!-- other content -->
                <%: Styles.Render("~/Content/kendo") %>
                <%: Scripts.Render("~/bundles/jquery") %>
                <%: Scripts.Render("~/bundles/kendo") %>
            </head>
    * Razor:

            <head>
                <!-- other content -->
                @Styles.Render("~/Content/kendo")
                @Scripts.Render("~/bundles/jquery")
                @Scripts.Render("~/bundles/kendo")
            </head>

8. Add a reference to the **Kendo.Mvc.UI** namespace to your **web.config**. Then the `Kendo` HtmlHelper extension would
be availble in your views. Rebuild your project after adding the namespace to the web.config (required for Visual Studio to show intellisense for Kendo.Mvc.UI).
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

9.  Use any Kendo UI HtmlHelper extension:
    * WebForms

            <%: Html.Kendo().DatePicker().Name("Birthday") %>
    * Razor

            @(Html.Kendo().DatePicker().Name("Birthday"))

### Using CDN

You can include the JavaScript and CSS files from CDN. Don't forget to specify the version (e.g. 2012.2.710)

    <link href="http://cdn.kendostatic.com/<version>/styles/kendo.common.min.css" rel="stylesheet" type="text/css" />
    <link href="http://cdn.kendostatic.com/<version>/styles/kendo.default.min.css" rel="stylesheet" type="text/css" />
    <!-- jQuery is not hosted on Kendo CDN - include from another location -->
    <script src="http://code.jquery.com/jquery-1.7.1.min.js"></script>
    <script src="http://cdn.kendostatic.com/<version>/js/kendo.web.min.js"></script>
    <script src="http://cdn.kendostatic.com/<version>/js/kendo.aspnetmvc.min.js"></script>

