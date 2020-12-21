---
title: "Frozen"
component: "Grid"
description: "Learn how to freeze the grid columns at left or right side and how to freeze the grid rows at top."
---

# Frozen rows and columns

Frozen rows and columns provides an option to make rows and columns always visible in the top and left side of the grid while scrolling.

To use frozen rows and columns support, inject the `Freeze` module in the `provide` section.

In this demo, the [`frozenColumns`](../api/grid/#frozencolumns) is set as '2' and the [`frozenRows`](../api/grid/#frozenrows)
is set as '3'. Hence, the left two columns and top three rows are frozen.

{% tab template="grid/scroll/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height=315 :frozenColumns='2' :frozenRows='3' :allowSelection='false' :enableHover='false' width='600'>
                <e-columns>
                    <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                    <e-column field='CustomerID' headerText='Customer ID' width=150></e-column>
                    <e-column field='OrderDate' headerText='Order Date' width=130 format='yMd' textAlign='Right' type='date'></e-column>
                    <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
                    <e-column field='ShipAddress' headerText='Ship Address' width=170></e-column>
                    <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                    <e-column field='ShipCountry' headerText='Ship Country' width=150></e-column>
                    <e-column field='ShipRegion' headerText='Ship Region' width=150></e-column>
                    <e-column field='ShipPostalCode' headerText='Ship Postal Code' width=150></e-column>
                    <e-column field='Freight' headerText='Freight' width=120></e-column>
                </e-columns>
               </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Freeze } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
    grid: [Freeze]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * The `height` and `width` must be set while giving frozen rows and columns.
> * Frozen rows and columns should not be set outside the grid view port.
> * Frozen Grid will support row and column virtualization feature, which helps to improve the Grid performance while loading a large dataset.

## Frozen Grid Limitations

The following features are not supported in frozen rows and columns:

* Grouping
* Row Template
* Detail Template
* Hierarchy Grid

## Freeze Direction

You can freeze the Grid columns on the left or right side by using the [`column.freeze`](../api/grid/column/#freeze) property and the remaining columns will be movable. The grid will automatically move the columns to the left or right position based on the [`column.freeze`](../api/grid/column/#freeze) value.

Types of the [`column.freeze`](../api/grid/column/#freeze) directions:

* **`Left`**: Allows you to freeze the columns at the left.
* **`Right`**: Allows you to freeze the columns at the right.

In this demo, the **ShipCountry** column is frozen at the left and the **CustomerID** column is frozen at the right side of the content table.

{% tab template="grid/scroll/default" %}

```html
<template>
    <div id="app">
        <ejs-grid :dataSource='data' height=315 :frozenRows='2' :enableHover='false'>
                <e-columns>
                    <e-column field='OrderID' headerText='Order ID' textAlign='Right' width=120></e-column>
                    <e-column field='Freight' headerText='Freight' width=120></e-column>
                    <e-column field='CustomerID' headerText='Customer ID' width=150 freeze='Right'></e-column>
                    <e-column field='OrderDate' headerText='Order Date' width=130 format='yMd' textAlign='Right' type='date'></e-column>
                    <e-column field='ShipName' headerText='Ship Name' width=150></e-column>
                    <e-column field='ShipAddress' headerText='Ship Address' width=170></e-column>
                    <e-column field='ShipCity' headerText='Ship City' width=150></e-column>
                    <e-column field='ShipCountry' headerText='Ship Country' width=150 freeze='Left'></e-column>
                </e-columns>
               </ejs-grid>
    </div>
</template>
<script>
import Vue from "vue";
import { GridPlugin, Freeze } from "@syncfusion/ej2-vue-grids";
import { data } from "./datasource.js";

Vue.use(GridPlugin);

export default {
  data() {
    return {
      data: data
    };
  },
  provide: {
    grid: [Freeze]
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
</style>
```

{% endtab %}

> * Freeze Direction is not compatible with the [`isFrozen`](../api/grid/column/#isfrozen) and [`frozenColumns`](../api/grid/#frozencolumns) properties.

## Limitations of Freeze Direction

This feature has the below limitations, along with the above mentioned Frozen Grid limitations.

* Column virtualization
* Infinite scroll cache mode
* Freeze direction in the stacked header is not compatible with column reordering.
