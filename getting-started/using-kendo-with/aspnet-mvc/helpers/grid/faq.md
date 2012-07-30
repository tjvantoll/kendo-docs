---
title: Frequently Asked Questions
slug: mvc-grid-faq
publish: true
---

# Grid Frequently Asked Questions

## Displaying Values

### How do I display HTML in a grid column?

By default the Kendo UI Grid for ASP.NET MVC will encode the HTML entities present in the data. To disable that use the [Encoded](/api/wrappers/aspnet-mvc/Kendo.Mvc.UI.Fluent/GridBoundColumnBuilderi#encodedsystem.boolean) method.

#### Example: Display HTML Entities In Grid Columns

    columns.Bound(o => o.Description).Encoded(false);

### How do I customize the way a property is displayed in a grid bound column?

If the grid is [server bound](/getting-started/using-kendo-with/aspnet-mvc/helpers/grid/server-binding) use the `Template` method.

#### Example: Customize the Column Appearance of a Server Bound Grid (WebForms)

    <% Html.Kendo().Grid<Models.Product>(Model)
           .Name("Grid")
           .Columns(columns =>
           {
               columns.Bound(p => p.Title).Template(p =>
               {
                    %>
                        <strong><%: p.Title %></strong>
                    <%
               });
           })
           .Render();
    %>

#### Example: Customize the Column Appearance of a Server Bound Grid (Razor)

    @(Html.Kendo().Grid<Models.Product>(Model)
          .Name("Grid")
          .Columns(columns =>
          {
              columns.Bound(p => p.Title).Template(@<text>
                   <strong>@item.Title</strong>
              </text>);
          })
    )

> The `Template` method needs a [templated razor delegate](http://haacked.com/archive/2011/02/27/templated-razor-delegates.aspx) when used in Razor views.
The bound item is available using the `@item` parameter.

If the grid is [ajax bound](/getting-started/using-kendo-with/aspnet-mvc/helpers/grid/ajax-binding) use the `ClientTemplate` method.
The value should be a string which represents a valid [Kendo Template](/getting-started/framework/templates/overview).

#### Example: Customize the Column Appearance of a Ajax Bound Grid

    .Columns(columns =>
    {
        columns.Bound(p => p.Title).ClientTemplate("<strong>#: Title #</strong>");
    })

### How do I have conditional logic in a column client template?

A Kendo Template may contain arbitrary JavaScript code. The `#` symbol is used to denote JavaScript blocks.

#### Example: Conditions In ClientTemplate

    colums.Bound(p => p.ProductName).ClientTemplate(
        "# if (HasIcon == true) { #" +
            "<img src='" + Url.Content("~/Content/icons/") + "#= ProductID #.png' alt='#= ProductName # icon' />" +
        "# } else { #" +
            "#: ProductName #" +
        "# } #"
    );

### How do I display a checkbox in an ajax-bound grid?

The `checked` attribute specifies whether a checkbox is displayed as checked or not. Use a condition to set that attribute.

#### Example: Display a Checkbox In Bound ColumnClientTemplate

    columns.Bound(p => p.Enabled).ClientTemplate(
        "<input type='checkbox' value='#= ProductID #' " +
            "# if (Enabled) { #" +
                "checked='checked'" +
            "# } #" +
        "/>"
    );

### How do I use action links?

For server-bound grids the `Template` method should be used.

#### Example: Action Link In Grid Column (WebForms)

    columns.Bound(p => p.ProductID).Template(p =>
    {
        %>
            <%: Html.ActionLink("Show Product Details", "ProductDetails", new { id = p.ProductID } ) %>
        <%
    });

#### Example: Action Link In Grid Column (Razor)

    columns.Bound(p => p.ProductID).Template(@<text>
          @Html.ActionLink("Show Product Details", "ProductDetails", new { id = @item.ProductID } )>
    </text>);

For ajax-bound grids the `ClientTemplate` method should be used.

#### Example: Action Link In Ajax-Bound Grid Column

    columns.Bound(p => p.ProductID).ClientTemplate(
        "<a href='" +
            Url.Action("ProductDetails", "Product") +
            "/#= ProductID #'" +
        ">Show Product Details</a>"
    );

### How do I use a JavaScript function in a column client template?

The Kendo Template has an implicit parameter called `data`. Use that as the argument of the JavaScript function.

#### Example: Use JavaScript Function In ClientTemplate
     // -- removed for brevity
     columns.Bound(p => p.ProductID).ClientTemplate("#= productDetails(data) #");
     // -- removed for brevity

    <script>
    function productDetails(product) {
        var action = '@Url.Action("ProductDetails", "Product")';

        var html = kendo.format("<a href='{0}/{1}'>Show Product Details</a>",
            action,
            product.ProductID
        );

        return html;
    }
    </script>
### How do I change the format of a bound column?

Use the [Format](api/wrappers/aspnet-mvc/Kendo.Mvc.UI.Fluent/GridBoundColumnBuilder#formatsystem.string) method.
The value should be a valid [number](/api/framework/kendo#standard-number-formats) or [date](/api/framework/kendo#standard-date-formats) format.

#### Example: Specify the Format Of a Bound Column

    columns.Bound(o => o.OrderDate).Format("{0:d}"); // Will use the short date pattern

