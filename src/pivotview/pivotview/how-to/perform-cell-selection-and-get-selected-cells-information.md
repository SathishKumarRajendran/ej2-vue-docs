# Perform cell selection and get selected cells information

You can select any cell/row by setting the property `gridSettings.allowSelection` as `true` where the selected cells can be highlighted. It can be done through mouse down or arrow keys.

## Selection mode

It supports four types of selection mode that can be set by the property `gridSettings.selectionSettings.mode`. They are,

* **`Row`**: The `Row` value is set by default, and allows you to select only rows.
* **`Column`**: Allows you to select only columns.
* **`Cell`**: Allows you to select only cells.
* **`Both`**: Allows you to select rows and columns at the same time.

## Selection type

It supports two types of selection that can be set by the property `gridSettings.selectionSettings.type`. They are,

* **`Single`**: The `Single` value is set by default, and it only allows selection of a single row or a column or a cell.
* **`Multiple`**: Allows you to select multiple rows or cells.
To perform the multi-selection, press and hold CTRL key and click the desired rows or columns or cells. To select range of rows or cells, press and hold the SHIFT key and click the rows or columns or cells.

## Event

The event `cellSelected` fires on every cell/row/column on selected/deselected operations and it provides the selected cells information with its corresponding column and row headers.
{% tab template="pivot-grid/common" %}

{% raw %}

```html
<template>
    <div id="app">
        <ejs-pivotview :height="height" :dataSourceSettings="dataSourceSettings" :gridSettings="gridSettings" :cellSelected="cellSelected"> </ejs-pivotview>
    </div>
</template>

<script>
import Vue from "vue";
import { PivotViewPlugin, PivotCellSelectedEventArgs } from "@syncfusion/ej2-vue-pivotview";
import { pivotData } from './datasource.js';

Vue.use(PivotViewPlugin);

export default {
  data () {
    return {
      dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
      },
      height: 350,
      gridSettings: {
        allowSelection: true,
        selectionSettings: { mode: 'Both', type: 'Multiple' }
      }
    }
  },
  methods: {
    cellSelected: function(args: PivotCellSelectedEventArgs) {
        //args.selectedCellsInfo -> get selected cells information.
        //args.pivotValues -> get the pivot values of the pivot table.
    },
  }
}
</script>
<style>
@import "@syncfusion/ej2-vue-pivotview/styles/material.css";
</style>
```

{% endraw %}

{% endtab %}
