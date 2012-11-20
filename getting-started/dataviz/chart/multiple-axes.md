---
title: Multiple Axes
slug: chart-multiple-axes
publish: true
---

# Multiple Axes



## Multiple category axes

The chart supports having multiple category axes. This can be useful, for example, if you want to mirror the category axis.

Series can be associated to a category axis by setting their `categoryAxis` option to the axis unique name.

    $("#container").kendoChart({
        title: {
            text: "Average temperature and humidity"
        },
        legend: {
            position: "bottom"
        },
        series: [{
                name: "Temperature",
                data: [20, 25, 32],
                axis: "temperature"
            }, {
                name: "Humidity",
                data: [45, 50, 80],
                axis: "humidity"
        }],
        categoryAxis: [{
            categories: ["Aug", "Sep", "Oct"]
        }, {
			
		}],
        valueAxis: {
            name: "temperature",
            labels: {
                format: "{0}C"
            }
        }
    });


![Chart with multiple axes](chart-multiple-axes.png)

In this example we have defined "temperature" and "humidity" axes. Series are associated to a value axis by specifying its name.

### Multiple value axes

A chart might have more than one value axis. These additional axes must have unique names. For example:

    $("#container").kendoChart({
        title: {
            text: "Average temperature and humidity"
        },
        legend: {
            position: "bottom"
        },
        series: [{
                name: "Temperature",
                data: [20, 25, 32],
                axis: "temperature"
            }, {
                name: "Humidity",
                data: [45, 50, 80],
                axis: "humidity"
        }],
        categoryAxis: {
            categories: ["Aug", "Sep", "Oct"]
        },
        valueAxis: [{
            name: "temperature",
            labels: {
                format: "{0}C"
            }
        }, {
            name: "humidity",
            labels: {
                format: "{0}%"
            }
        }]
    });


![Chart with multiple axes](chart-multiple-axes.png)

In this example we have defined "temperature" and "humidity" axes. Series are associated to a value axis by specifying its name.

#### Value axis crossing value(s)

You can control the arrangement of the value axes by specifying the values (category indices) at which they cross the category axis. For example:

    categoryAxis: {
        categories: ["Aug", "Sep", "Oct"],
        axisCrossingValue: [0, 3]
    }


The first value axis will cross the category axis at the first category (leftmost). The second value axis will cross it at the last category.

![Bar chart with customized axis crossing values](chart-axis-crossing-values.png)


### Multiple X/Y axes

You can define more X and Y axes in addition to the primary axes. These additional axes must have unique names. Series are associated to a X and Y axes by specifying their name.

**Note:** Do not specify a name for the primary X and Y axes.

    $("#container").kendoChart({
        title: {
            text: "Dyno run results"
        },
        legend: {
            position: "bottom"
        },
        seriesDefaults: {
            type: "scatterLine"
        },
        series: [{
            name: "Power",
            data: [[1000,  10], [1500, 19], [2000, 30]]
        }, {
            name: "Torque",
            data: [[1000,  50], [1500, 65], [2000, 80]],
            yAxis: "torque"
        }],
        xAxis: {
            title: "Engine rpm"
        },
        yAxis: [{
            labels: {
                format: "{0} bhp"
            }
        }, {
            name: "torque",
            labels: {
                format: "{0} Nm"
            }
        }]
    });


The first series is associated with the default Y axis, as no axis name is specified. The "torque" series will be plotted on the "torque" Y axis.

![Scatter chart with multiple axes](chart-scatter-line-multiple-axes.png)

### Axis crossing value(s)

You can control the arrangement of the X and Y axes by specifying the values at which they cross the primary axes.

    xAxis: {
        title: "Engine rpm",
        axisCrossingValue: [0, 2500]
    }


The primary Y axis will cross the X axis at 0 (leftmost). The second, "torque" Y axis will cross the X axis at the 2500 mark or at its right end, whichever is first.

![Scatter line chart with customized axis crossing value](chart-scatter-line-axis-crossing-value.png)


