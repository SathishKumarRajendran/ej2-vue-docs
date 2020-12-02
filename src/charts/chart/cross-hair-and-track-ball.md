---
title: " Chart Crosshair and Trackball | Vue "

component: "Chart"

description: "Crosshair has a vertical and horizontal line to view the value of the axis at mouse position.The trackball used to display data collections"
---

# Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairSettings/#enable) property in the `crosshair`.

{% tab template="chart/user-interaction/crosshair" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis' :crosshair='crosshair'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Line' xName='x' yName='y' name='Temperature'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Legend, Crosshair, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
           valueType: 'DateTime',
           labelFormat: 'yMMM'
        },
        title: "Weather Condition",
        crosshair: { enable: true }
    };
  },
  provide: {
    chart: [LineSeries, Crosshair, DateTime]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

## Tooltip for axis

Tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltip/#enable)
property of `crosshairTooltip` in the corresponding axis.

{% tab template="chart/user-interaction/crosshair" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :crosshair='crosshair'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Line' xName='x' yName='y' name='Temperature'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Legend, Crosshair, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
            valueType: 'DateTime',
            crosshairTooltip: { enable: true },
            labelFormat: 'yMMM'
        },
         primaryYAxis: {
           crosshairTooltip: { enable: true }
        },
        title: "Weather Condition",
        crosshair: { enable: true }
    };
  },
  provide: {
    chart: [LineSeries, Crosshair, DateTime]
  }
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

## Customization

The [`fill`](../api/chart/crosshairTooltip/#fill) and [`textStyle`](../api/chart/crosshairTooltip/#textstyle)
property of the `crosshairTooltip` is used to customize the background color and font style of the crosshair label
respectively. Color and width of the crosshair line can be customized by using the
[`line`](../api/chart/crosshairSettingsModel/#line) property in the crosshair.

{% tab template="chart/user-interaction/crosshair" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :crosshair='crosshair'>
            <e-series-collection>
                <e-series :dataSource='seriesData1' type='Line' xName='x' yName='y' name='Temperature'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Legend, Crosshair, DateTime } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

let series1: Object[] = [];
let point1: Object;
let value: number = 40;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}

export default {
  data() {
    return {
      seriesData1: series1,
      primaryXAxis: {
            valueType: 'DateTime',
             crosshairTooltip: { enable: true, fill: 'green' },
            labelFormat: 'yMMM'
        },
         primaryYAxis: {
            crosshairTooltip: { enable: true, fill: 'green' },
        },
        title: "Weather Condition",
        crosshair: {  enable: true, line: {width: 2, color: 'green'}, fill: 'green' }
    };
  },
  provide: {
    chart: [LineSeries, Crosshair, DateTime]
  }
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}

>Note: To use crosshair feature, we need to inject `Crosshair` into the `provide`.

## Trackball

Trackball is used to track a data point closest to the mouse or touch position. Trackball marker indicates the
closest point and trackball tooltip displays the information about the point. To use trackball feature,
we need to inject `Crosshair` and `Tooltip` into the `provide`.

Trackball can be enabled by setting the [`enable`](../api/chart/crosshairSettings/#enable) property of the crosshair to true and
[`shared`](../api/chart/tooltipSettings/#shared) property in `tooltip` to true in chart.

{% tab template="chart/user-interaction/trackball" %}

```html
<template>
    <div id="app">
         <ejs-chart id= "container" :title='title' :primaryXAxis='primaryXAxis' :crosshair='crosshair' :tooltip='tooltip'>
            <e-series-collection>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y' name='John' :marker='marker'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y1' name='Andrew' :marker='marker'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y2' name='Thomas' :marker='marker'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y3' name='Mark' :marker='marker'> </e-series>
                <e-series :dataSource='seriesData' type='Line' xName='x' yName='y4' name='William' :marker='marker'> </e-series>
            </e-series-collection>
        </ejs-chart>
    </div>
</template>
<script>
import Vue from "vue";
import { ChartPlugin, LineSeries, Legend, Crosshair, DateTime, Tooltip } from "@syncfusion/ej2-vue-charts";

Vue.use(ChartPlugin);

export default {
  data() {
    return {
        seriesData: [
            { x: new Date(2000, 2, 11), y: 15, y1: 39, y2: 60, y3: 75, y4: 85 },
            { x: new Date(2000, 9, 14), y: 20, y1: 30, y2: 55, y3: 75, y4: 83 },
            { x: new Date(2001, 2, 11), y: 25, y1: 28, y2: 48, y3: 68, y4: 85 },
            { x: new Date(2001, 9, 16), y: 21, y1: 35, y2: 57, y3: 75, y4: 87 },
            { x: new Date(2002, 2, 7), y: 13, y1: 39, y2: 62, y3: 71, y4: 82 },
            { x: new Date(2002, 9, 7), y: 18, y1: 41, y2: 64, y3: 69, y4: 74 },
            { x: new Date(2003, 2, 11), y: 24, y1: 45, y2: 57, y3: 81, y4: 73 },
            { x: new Date(2003, 9, 14), y: 23, y1: 48, y2: 53, y3: 84, y4: 75 },
            { x: new Date(2004, 2, 6), y: 19, y1: 54, y2: 63, y3: 85, y4: 73 },
            { x: new Date(2004, 9, 6), y: 31, y1: 55, y2: 50, y3: 87, y4: 60 },
            { x: new Date(2005, 2, 11), y: 39, y1: 57, y2: 66, y3: 75, y4: 48 },
            { x: new Date(2005, 9, 11), y: 50, y1: 60, y2: 65, y3: 70, y4: 55 },
            { x: new Date(2006, 2, 11), y: 24, y1: 60, y2: 79, y3: 85, y4: 40 }
              ],
      primaryXAxis: {
            title: 'Years',
            minimum: new Date(2000, 1, 1), maximum: new Date(2006, 2, 11),
            intervalType: 'Years',
            valueType: 'DateTime',
        },
        title: "Average Sales per Person",
        crosshair: {  enable: true, lineType: 'Vertical' },
        tooltip: { enable: true, shared: true, format: '${series.name} : ${point.x} : ${point.y}' },
        marker: { visible: true }
    };
  },
  provide: {
    chart: [LineSeries, Crosshair, DateTime, Tooltip]
  },
};
</script>
<style>
 #container {
   height: 350px;
 }
</style>
```

{% endtab %}
