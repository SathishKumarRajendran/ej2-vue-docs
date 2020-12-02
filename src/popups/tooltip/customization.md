---
title: "Tooltip Customization"
component: "Tooltip"
description: "Vue tooltip component’s complete look and feel can be customized by changing its background color, opacity, content font, etc."
---

# Customization

The Tooltip can be customized by using the `cssClass` property, which accepts custom CSS class names that define specific user-defined
 styles and themes to be applied on the Tooltip element.

## Tip pointer customization

Styling the tip pointer's size, background, and border colors can be done using the `cssClass` property, as given below.

{% tab template="tooltip/custom-tip", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-tooltip ref="tooltip"  class="tooltipcontainer" :cssClass="cssClass" content='Tooltip arrow customized' >
            <div id="target">
                Show tooltip
            </div>
    </ejs-tooltip>
  </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

export default {
    data() {
    return {
        cssClass: 'customtip'
    }
    }
}
</script>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#target {
    background-color: #cfd8dc;
    border: 3px solid #eceff1;
    box-sizing: border-box;
    margin: 80px auto;
    padding: 20px 0;
    width: 200px;
    text-align: center;
    color: #424242;
    font-size: 20px;
    user-select: none;
}


/* csslint ignore:start */

.customtip.e-tooltip-wrap {
    padding: 4px;
}

.customtip.e-tooltip-wrap .e-arrow-tip.e-tip-bottom {
    height: 20px;
    width: 12px;
}

.customtip.e-tooltip-wrap .e-arrow-tip.e-tip-top {
    height: 20px;
    width: 12px;
}

.customtip.e-tooltip-wrap .e-arrow-tip.e-tip-left {
    height: 12px;
    width: 20px;
}

.customtip.e-tooltip-wrap .e-arrow-tip.e-tip-right {
    height: 12px;
    width: 20px;
}

.customtip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-bottom {
    border-left: 6px solid transparent;
    border-right: 6px solid transparent;
    border-top: 20px solid #616161;
}

.customtip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-top {
    border-bottom: 20px solid #616161;
    border-left: 6px solid transparent;
    border-right: 6px solid transparent;
}

.customtip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-left {
    border-bottom: 6px solid transparent;
    border-right: 20px solid #616161;
    border-top: 6px solid transparent;
}

.customtip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-right {
    border-bottom: 6px solid transparent;
    border-left: 20px solid #616161;
    border-top: 6px solid transparent;
}
/* csslint ignore:end */
</style>

```

{% endtab %}

## Tooltip customization

The complete look and feel of the Tooltip can be customized by changing it's background color, opacity, content font, etc.
The following code example shows the way to achieve it.

{% tab template="tooltip/custom-tooltip", isDefaultActive=true %}

```html
<template>
    <div id="app">
    <ejs-tooltip ref="tooltip"  class="tooltipcontainer" :cssClass="cssClass" content='Tooltip arrow customized' >
            <div id="target">
                Show tooltip
            </div>
        </ejs-tooltip>
  </div>
</template>
<script>
import Vue from "vue";
import { TooltipPlugin } from "@syncfusion/ej2-vue-popups";
Vue.use(TooltipPlugin);

export default {
    data() {
    return {
        cssClass: 'customtooltip'
    }
    }
}
</script>
<style>
@import "node_modules/@syncfusion/ej2-base/styles/material.css";
@import "node_modules/@syncfusion/ej2-vue-popups/styles/material.css";
#target {
    background-color: #cfd8dc;
    border: 3px solid #eceff1;
    box-sizing: border-box;
    margin: 80px auto;
    padding: 20px 0;
    width: 200px;
    text-align: center;
    color: #424242;
    font-size: 20px;
    user-select: none;
}


/* csslint ignore:start */

.customtooltip.e-tooltip-wrap .e-tip-content {
    line-height: 20px;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip.e-tip-bottom {
    height: 12px;
    left: 50%;
    top: 100%;
    width: 24px;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip.e-tip-top {
    height: 12px;
    left: 50%;
    top: -9px;
    width: 24px;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip.e-tip-left {
    height: 24px;
    left: -9px;
    top: 48%;
    width: 12px;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip.e-tip-right {
    height: 24px;
    left: 100%;
    top: 50%;
    width: 12px;
}

.customtooltip.e-tooltip-wrap {
    border-radius: 4px;
    opacity: 1;
}

.customtooltip.e-tooltip-wrap.e-popup {
    background-color: #fff;
    border: 2px solid #000;
}

.customtooltip.e-tooltip-wrap .e-tip-content {
    color: #000;
    font-size: 12px;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-bottom {
    border-left: 12px solid transparent;
    border-right: 14px solid transparent;
    border-top: 12px solid #000;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-top {
    border-bottom: 12px solid #000;
    border-left: 12px solid transparent;
    border-right: 12px solid transparent;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-left {
    border-bottom: 12px solid transparent;
    border-right: 12px solid #000;
    border-top: 12px solid transparent;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip-outer.e-tip-right {
    border-bottom: 12px solid transparent;
    border-left: 12px solid #000;
    border-top: 12px solid transparent;
}

.customtooltip.e-tooltip-wrap .e-arrow-tip-inner.e-tip-bottom {
    color: #fff;
    font-size: 25.9px;
}

/* csslint ignore:end */
</style>

```

{% endtab %}
