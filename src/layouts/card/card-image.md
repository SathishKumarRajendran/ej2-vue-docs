---
title: "Images and Divider"
component: "Card"
description: "This section explains how to create the Essential JS 2 Card control with different images, title, and divider."
---

# Images and Divider

## Images

The Card supports to include images within the elements, you can add image as direct element anywhere inside card root by adding the
`e-card-image` class to `div` element. Using the class defined, you can write CSS styles to load images to that element.

> By default, card images occupies full width of its parent element.

```html
    <div class = "e-card">
        <div class="e-card-image">
        </div>
    </div>
```

### Title

Card image is supported to include a title or caption for the image. By default, Title is placed over the image on left-bottom position with
overlay.

```html
    <div class = "e-card">
        <div class="e-card-image">
            <div class="e-card-title"></div>
        </div>
    </div>
```

{% tab template="card/images-divider/title", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <div class="e-card">
            <div class="e-card-image">
                <div class="e-card-title">JavaScript </div>
            </div>
            <div class="e-card-content"> JavaScript Succinctly was written to give readers an accurate, concise examination of JavaScript objects and their supporting nuances, such as complex values, primitive values, scope, inheritance, the head object, and more. </div>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';

export default {
  name: 'app',
}
</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';

.e-card-image {
    background: url('./sample.jpg');
    height: 160px;;
}

.e-card {
    width: 300px;
    margin: auto;
}
</style>
```

{% endtab %}

## Divider

Divider used to separate the elements inside the card. You can add divider inside the card elements to separate it.

* Place the `div` element with `e-card-separator` class inside the card element for adding a divider.

{% tab template="card/images-divider/divider", isDefaultActive=true %}

```html
<template>
  <div id="app">
       <div tabindex="0" class="e-card" id="basic">
            <div class="e-card-title">Explore Cities</div>
            <div class="e-card-separator"></div>
            <div class="e-card-content">
                Sydney is a city on the east coast of Australia. Sydney is the capital city of New South Wales. About four million people
                live in Sydney which makes it the biggest city in Oceania.
            </div>
            <div class="e-card-separator"></div>
            <div class="e-card-content">
                New York City has been described as the cultural, financial, and media capital of the world, and exerts a significant impact
                upon commerce and etc.,
            </div>
            <div class="e-card-separator"></div>
            <div class="e-card-content">
                Malaysia is one of the Southeast Asian countries, on a peninsula of the Asian continent, to a certain extent; it can be recognized
                as part of the Asian continent.
            </div>
        </div>
  </div>
</template>
<script>
import Vue from 'vue';
export default {
  name: 'app',
}
</script>
<style>
  @import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css';

#container {
    visibility: hidden;
}

#loader {
    color: #008cff;
    height: 40px;
    left: 45%;
    position: absolute;
    top: 45%;
    width: 30%;
}
.e-card {
    width: 300px
}
</style>
```

{% endtab %}

## See Also

* [How to customize the card image title position](./how-to/customize-the-card-image-title-position/)