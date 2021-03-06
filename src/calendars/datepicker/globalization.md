---
title: "Globalization"
component: "DatePicker"
description: "Learn about how to globalize the date picker component and how to localize the culture related content."
---

# Globalization

Globalization is the combination of  adapting the component to
various languages by means of parsing and formatting the date or
number [`Internationalization`](../common/internationalization/) and also by adding cultural specific customizations and translating the text [`localization`](../common/localization/)

By default, DatePicker date format, week and month names are specific to English culture. It utilizes the
[`Essential JavaScript 2 Internationalization`](../common/internationalization/)
package to parse and format the date object based on the culture by using the official [`UNICODE CLDR`](http://cldr.unicode.org/)
JSON data and it allows to load the culture specific CLDR JSON data by using
`loadCldr`
method

The DatePicker component supports only the Gregorian type of calendar.
All the Essential JS 2 component are specific to English culture ('en-US').
If you want to go with the different culture other than English, follow the below steps.

* Install the `CLDR-Data` package by using the below command (it installs the CLDR JSON data). To
know more about CLDR-Data refer the
[`CLDR-Data`](http://cldr.unicode.org/index/cldr-spec/json) link.

```cmd
npm install cldr-data --save
```

 Once the package installed, you can find the culture
specific JSON data under the location `\node_modules\cldr-data`.

* Now import the installed CLDR JSON data into the `app.vue` file.

* Now use the `loadCldr`
method
to load the culture specific CLDR JSON data
from the installed location to `app.vue` file.

* DatePicker displayed `Sunday` as the first day of week based on default culture ("en-US"). If you want to display the DatePicker with loaded culture’s first day of week, you need to import `weekdata.json` file from the `cldr-data/suppemental` as given in the code example.

```typescript
//Load the loadCldr from ej2-base
import { loadCldr } from '@syncfusion/ej2-base';

import * as numberingSystems from 'cldr-data/supplemental/numberingSystems.json';
import * as gregorian from 'cldr-data/main/de/ca-gregorian.json';
import * as numbers from 'cldr-data/main/de/numbers.json';
import * as timeZoneNames from 'cldr-data/main/de/timeZoneNames.json';
import * as weekData from 'cldr-data/supplemental/weekdata.json';// To load the culture based first day of week

loadCldr(numberingSystems, gregorian, numbers, timeZoneNames, weekData);
```

> The `Localization` library allows you to localize default text content of the DatePicker. The DatePicker component has static text for  **today** feature that can be changed to other cultures (Arabic, Deutsch, French, etc.) by defining the
[`locale`](../api/datepicker#locale) value and translation object.

Locale keywords |Text
-----|-----
today | Name of the button to choose Today date.
placeholder | Hint to describe expected value in input element.

* Before changing the culture other than `English`, ensure that locale text for the concerned culture is loaded through `load` method of
[L10n](https://ej2.syncfusion.com/documentation/api/base/l10n#load) class.

```typescript

//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
    'de': {
        'datepicker': { placeholder: 'Wählen Sie ein Datum aus', today: 'heute' }
    }
});
```

* Set the culture by using the
[`locale`](../api/datepicker#locale)
property. The following example demonstrates the DatePicker in `German` culture.

{% tab template="datepicker/locale", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datepicker id="datepicker" locale='de' ></ejs-datepicker>
      </div>
    </div>
</template>
<script>
import Vue from "vue";
import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(DatePickerPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);
L10n.load({
    'de': {
      'datepicker': { placeholder: "Wählen Sie Datum und Uhrzeit",
             today: "heute"}
    }
});
export default {}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    margin: 0px auto;
    width: 240px;
}
</style>
```

{% endtab %}

## Right-To-Left

The DatePicker supports right-to-left functionality for languages like Arabic, Hebrew to displays
the text in the right-to-left direction. Use
[`enableRtl`](../api/datepicker#enablertl)
property to set the RTL direction.

{% tab template="datepicker/rtl", isDefaultActive=true %}

```html
<template>
    <div id="app">
      <div class='wrapper'>
        <ejs-datepicker id="datepicker" :locale="locale" :enableRtl="rtl" ></ejs-datepicker>
      </div>
    </div>
</template>
<script>
import Vue from "vue";
import { loadCldr, L10n } from '@syncfusion/ej2-base';
import { DatePickerPlugin } from "@syncfusion/ej2-vue-calendars";
// Here we have referred local json files for preview purpose
import * as numberingSystems from './numberingSystems.json';
import * as gregorian from './ca-gregorian.json';
import * as numbers from './numbers.json';
import * as timeZoneNames from './timeZoneNames.json';

Vue.use(DatePickerPlugin);
loadCldr(numberingSystems, gregorian, numbers, timeZoneNames);
L10n.load({
    'he': {
      'datepicker': { placeholder: 'הזן תאריך',
             today: 'היו'}
    }
});
export default {
    data () {
       return {
           locale: "he",
           rtl: true
        }
    }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import "../node_modules/@syncfusion/ej2-vue-calendars/styles/material.css";
 .wrapper {
    margin: 0px auto;
    width: 240px;
}
</style>
```

{% endtab %}