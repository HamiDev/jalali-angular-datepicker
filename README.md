# Angular Jalali Date Picker
This is a configurable jalali (persian, khorshidi, shamsi) date-picker build for Angular 2 or 4 applications and uses [jalali-moment](https://github.com/fingerpich/moment-jalaali) as its dependency. it's only Angular! No jQuery.
[DEMO](https://fingerpich.github.io/jalali-angular-datepicker/)

Read this in other languages: [فارسی](./README.fa.md)

[![Build Status](https://travis-ci.org/fingerpich/jalali-angular-datepicker.svg?branch=jalali-master)](https://travis-ci.org/fingerpich/jalali-angular-datepicker) 
[![npm version](https://badge.fury.io/js/ng2-jalali-date-picker.svg)](https://badge.fury.io/js/ng2-jalali-date-picker)
[![Package Quality](http://npm.packagequality.com/shield/ng2-jalali-date-picker.svg)](http://packagequality.com/#?package=ng2-jalali-date-picker)
[![dependency Quality](https://david-dm.org/fingerpich/jalali-angular-datepicker.svg)](https://david-dm.org/fingerpich/jalali-angular-datepicker)
[![dev dependency Quality](https://david-dm.org/fingerpich/jalali-angular-datepicker/dev-status.svg)](https://david-dm.org/fingerpich/jalali-angular-datepicker?type=dev)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/72a073fa893f4f0b823f41106c9e4f56)](https://www.codacy.com/app/zarei-bs/jalali-angular-datepicker?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=fingerpich/jalali-angular-datepicker&amp;utm_campaign=Badge_Grade)
[![Codacy Badge](https://api.codacy.com/project/badge/Coverage/72a073fa893f4f0b823f41106c9e4f56)](https://www.codacy.com/app/zarei-bs/jalali-angular-datepicker?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=fingerpich/jalali-angular-datepicker&amp;utm_campaign=Badge_Coverage)

## Screenshots

<div style="display: flex; justify-content: space-between;">
  [<img alt="date picker" src="./screenshots/date_picker.jpg" width="200px">](https://fingerpich.github.io/jalali-angular-datepicker/)
  [<img alt="date time picker" src="./screenshots/date_time_picker.jpg" width="200px">](https://fingerpich.github.io/jalali-angular-datepicker/)
  [<img alt="month picker" src="./screenshots/month_picker.jpg" width="200px">](https://fingerpich.github.io/jalali-angular-datepicker/)
</div>

## Installation:
1. Download from npm:
`npm install ng2-jalali-date-picker --save`  
2. import the `DpDatePickerModule` module in typescript (.ts) or es6 files like below:  
 `import {DpDatePickerModule} from 'ng2-jalali-date-picker';`  
3. Add `DpDatePickerModule` to your module imports:  
```ts
 @NgModule({
   ...
   imports: [
     ...
     DpDatePickerModule
   ]
 })
```

## How to use

```html
 <dp-date-picker 
   dir="rtl"
   [(ngModel)]="dateObject"
   mode="day"
   placeholder="تاریخ"
   theme="dp-material">
 </dp-date-picker>
```

```ts
 dateObject = "";
 
 //OR if you have initial value you could use following code
 import * as moment from 'jalali-moment';
 dateObject = moment('1395-11-22','jYYYY,jMM,jDD');
```
[Demo](https://plnkr.co/XJSWtt)

#### How to use the output as a jalali (shamsi) date
 ```ts
import * as moment from 'jalali-moment';
dateObject.format('jYYYY/jMM/jD)'
```
read [jalali-moment](https://github.com/fingerpich/jalali-moment)

#### How to use it with system.js
[this Demo](https://plnkr.co/XJSWtt) is using system.js. 


### Attributes:
all attributes in the following table could be used as 
```html
// a future selector
<dp-date-picker mode="day" placeholder="تاریخ" [minDate]="moment()" [(ngModel)]="selectedDate"></dp-date-picker>
```
| Name                 | Type                                | Default            | Applies To                | Description                                                                                                                                                                                                                                        |
|----------------------|:-----------------------------------:|:------------------:|:-------------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| dir                  | `rtl`|`ltr`         | `ltr`                                                                    | the type of the calender which will be displayed in the picker                                                                                                                                                                                     |
| mode                 | `"day"\|"month"\|"time"\|"daytime"` | `"day"`            | All                       | the mode of the calender which will be displayed in the picker                                                                                                                                                                                     |
| disabled             | `Boolean`                           | `false`            | All                       | If set to true the input would be disabled                                                                                                                                                                                                         |
| placeholder          | `String`                            | `""`               | All                       | The date-picker input placeholder                                                                                                                                                                                                                  |
| required             | `Boolean`                           | `undefined`        | All                       | This is a validation rule, if there won't be any selected date then the containing form will be invalid.                                                                                                                                           |
| minDate              | `Moment\|String`                    | `undefined`        | `day\|month\|daytime`     | This is a validation rule, if the selected date will be before `minDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                            |
| maxDate              | `Moment\|String`                    | `undefined`        | `day\|month\|daytime`     | This is a validation rule, if the selected date will be after `maxDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                             |
| minTime              | `Moment\|String`                    | `undefined`        | `time`                    | This is a validation rule, if the selected date will be before `minTime` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                            |
| maxTime              | `Moment\|String`                    | `undefined`        | `time`                    | This is a validation rule, if the selected date will be after `maxTime` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                             |
| theme                | `String`                            | `""`               | All                       | Theme is a class added to the popup container (and inner components) - this will allow styling of the calendar when it's appended to outer element (for example - body). There is a built in theme named dp-material, you can find it in the demo. |
| config               | `IDatePickerConfig`                 | See Below          | All                       | Configuration object - see description below.                                                                                                                                                                                                      |

### Configuration:  
In order to provide configurations to the date-picker you need to pass it to the `dp-date-picker` component:  
```html
<dp-date-picker [(ngModel)]="selectedDate" [config]="datePickerConfig"></dp-date-picker>
```
```ts
datePickerConfig = {
    drops: 'up',
    format: 'YY/M/D'
}
```
Here are the available configurations:  

| Name                        | Type                  | Default                                                                   | Applies To                | Description                                                                                                                                                                                                                                                                   |
|-----------------------------|:---------------------:|:-------------------------------------------------------------------------:|:-------------------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| appendTo                    | `String\|HTMLElement` | `undefined`                                                               | All                       | The selector/element to which the calendar popup will append to (this is useful for `overflow: hidden` container issues). Please note that the `appendTo` element will be set with position `absolute` if it has position `static` (the default position).                    |
| locale                      | `String`              | `en`                                                                      | All                       | Localisation of language (see in the demo all supported locales)                                                                                                                                                                                                              |
| disableKeypress             | `Boolean`             | `false`                                                                   | All                       | Disables the possibility to change the date value by typing it - changing the date would be possible only from the picker                                                                                                                                                     |
| drops                       | `'up'\|'down'`        | `down`                                                                    | All                       | Whether the picker appears below or above the input element.                                                                                                                                                                                                                  |
| format                      | `String`              | `"DD-MM-YYYY"`                                                            | All                       | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                              |
| onOpenDelay                 | `Number`              | `0`                                                                       | All                       | The delay (in ms) between the date picker focusing and the date-picker popup apparel                                                                                                                                                                                          |
| opens                       | `'right'\|'left'`     | `right`                                                                   | All                       | Whether the picker appears aligned to the left or to the right the input element.                                                                                                                                                                                             |
| closeOnSelect               | `Boolean`             | `true`                                                                    | `day\|month`              | If set to `true` will close the date-picker after choosing a date from the calender, otherwise, won't.                                                                                                                                                                        |
| closeOnSelectDelay          | `Number`              | `100`                                                                     | `day\|month`              | The delay (in ms) between the date selection and the date-picker collapse                                                                                                                                                                                                     |
| allowMultiSelect            | `Boolean`             | `undefined`                                                               | `day\|month`              | If set to `true` will allow for choosing multiple dates. `false` will force a single selection. If `undefined`, the picker will attempt to guess based on the type of the input value.                                                                                        |
| dayBtnFormat                | `String`              | `DD`                                                                      | `day\|daytime`            | The day format of the day button in the calendar.                                                                                                                                                                                                                             |
| dayBtnFormatter             | `(Moment) => String`  | `undefined`                                                               | `day\|daytime`            | The formatter (callback function) of the day button in the calendar.                                                                                                                                                                                                          |
| enableMonthSelector         | `Boolean`             | `true`                                                                    | `day\|daytime`            | Whether to enable/disable the selection of a moth granularity picker.                                                                                                                                                                                                         |
| firstDayOfWeek              | `String`              | `"su"`                                                                    | `day\|daytime`            | The first day of the calendar's week. Should be one of: `"su", "mo", "tu", "we", "th", "fr", "sa"`                                                                                                                                                                            |
| isDayDisabledCallback       | `(Moment) => boolean` | `undefined`                                                               | `day\|daytime`            | Callback which should indicate if specific day is disabled.                                                                                                                                                                                                                   |
| monthFormat                 | `String`              | `"MMM-YYYY"`                                                              | `day\|daytime`            | The date format of the day calendar, the one that seen above the calendar days. Will be overwritten if `monthFormatter` provided.                                                                                                                                             |
| monthFormatter              | `(Moment) => String`  | `undefined`                                                               | `day\|daytime`            | The date formatter (callback function) of the day calendar, the one that seen above the calendar days.                                                                                                                                                                        |
| showNearMonthDays           | `Boolean`             | `true`                                                                    | `day\|daytime`            | Whether to show/hide next and previous month days.                                                                                                                                                                                                                            |
| showWeekNumbers             | `Boolean`             | `false`                                                                   | `day\|daytime`            | Whether to show/hide the week number of each week (iso week number).                                                                                                                                                                                                          |
| isMonthDisabledCallback     | `(Moment) => boolean` | `undefined`                                                               | `day\|month\|daytime`     | Callback which should indicate if specific month is disabled (month selector).                                                                                                                                                                                                |
| max                         | `Moment\|String`      | `undefined`                                                               | `day\|month\|daytime`     | Disables all dates (on the date-picker) that are set to after the `max`, note that if invalid date would be set by the input then the date picker value would be the max date but the input will show the user typed date.                                                    |
| min                         | `Moment\|String`      | `undefined`                                                               | `day\|month\|daytime`     | Disables all dates (on the date-picker) that are set to before the `min`, note that if invalid date would be set by the input then the date picker value would be the min date but the input will show the user typed date.                                                   |
| monthBtnFormat              | `String`              | `DD`                                                                      | `day\|month\|daytime`     | The month format of the month button in the calendar.                                                                                                                                                                                                                         |
| monthBtnFormatter           | `(Moment) => String`  | `undefined`                                                               | `day\|month\|daytime`     | The formatter (callback function) of the month button in the calendar.                                                                                                                                                                                                        |
| yearFormat                  | `String`              | `"YYYY"`                                                                  | `day\|month\|daytime`     | The date format of the month calendar, the one that seen above the calendar months. Will be overwritten if `yearFormatter` provided. (available when `enableMonthSelector` is set to `true`).                                                                                 |
| yearFormatter               | `(Moment) => String`  | `undefined`                                                               | `day\|month\|daytime`     | The date formatter (callback function) of the month calendar, the one that seen above the calendar months. (available when `enableMonthSelector` is set to `true`).                                                                                                           |
| hours12Format               | `String`              | `"hh"`                                                                    | `daytime\|time`           | The hours format of the time select when `showTwentyFourHours` is `false`.                                                                                                                                                                                                    |
| hours24Format               | `String`              | `"HH"`                                                                    | `daytime\|time`           | The hours format of the time select when `showTwentyFourHours` is `true`.                                                                                                                                                                                                     |
| maxTime                     | `Moment\|String`      | `undefined`                                                               | `daytime\|time`           | Disables arrow buttons on the time select that would make the time after the `maxTime`.                                                                                                                                                                                       |
| meridiemFormat              | `String`              | `"A"`                                                                     | `daytime\|time`           | The AM/PM format of the time select when `showTwentyFourHours` is `false`.                                                                                                                                                                                                    |
| minTime                     | `Moment\|String`      | `undefined`                                                               | `daytime\|time`           | Disables arrow buttons on the time select that would make the time before the `minTime`.                                                                                                                                                                                      |
| minutesFormat               | `String`              | `"mm"`                                                                    | `daytime\|time`           | The minutes format of the time select.                                                                                                                                                                                                                                        |
| minutesInterval             | `number`              | `1`                                                                       | `daytime\|time`           | The number of minutes that will be added/subtracted when clicking up/down arrows on the time select.                                                                                                                                                                          |
| secondsFormat               | `String`              | `"ss"`                                                                    | `daytime\|time`           | The seconds format of the time select.                                                                                                                                                                                                                                        |
| secondsInterval             | `number`              | `1`                                                                       | `daytime\|time`           | The number of seconds that will be added/subtracted when clicking up/down arrows on the time select.                                                                                                                                                                          |
| showSeconds                 | `boolean`             | `false`                                                                   | `daytime\|time`           | If set to `true` will show seconds in the time select, otherwise, won't.                                                                                                                                                                                                      |
| showTwentyFourHours         | `boolean`             | `false`                                                                   | `daytime\|time`           | If set to `true` will show hours in 24 hour format. `false` will show hours in 12 hours format and append AM/PM to the end of the time select.                                                                                                                                |
| timeSeparator               | `String`              | `":"`                                                                     | `daytime\|time`           | The separator that will be placed between hours and minutes and between minutes and seconds on the time select.                                                                                                                                                               |
| showMultipleYearsNavigation | `boolean`             | `false`                                                                   | `day\|month\|daytime`     | If set to `true` will show buttons to navigate by multiple years (10 by default)                                                                                                                                                                                              |
| multipleYearsNavigateBy     | `number`              | `10`                                                                      | `day\|month\|daytime`     | Number of years to navigate when showMultipleYearsNavigation is `true`                                                                                                                                                                                                        |
| calendarSystem            | `ECalendarSystem`    | `ECalendarSystem.jalali`                                                            | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                    |

### API:
In order to use the date-picker api user the `@ViewChild` annotation in the date-picker containing component class, take at the example below:  
Container component:
```ts  
import {Component, ViewChild} from '@angular/core';
import {DatePickerComponent} from 'ng2-jalali-date-picker';

@Component({
selector: 'my-container',
template: `
<div>
    <h1>Container</h1>
    <dp-date-picker #dayPicker></dp-date-picker>
    <button (click)="open()"></button>
    <button (click)="close()"></button>
</div>
`
});
class MyContainer {
    @ViewChild('dayPicker') datePicker: DatePickerComponent;

    open() {
        this.datePicker.api.open();
    }

    close() {
         this.datePicker.api.close();
    }
}  
```
Here is the list of APIs:  

| Name                 | Signature       | Description            |
|----------------------|:---------------:|------------------------|
| open                 | `() => void`    | Opens the date picker  |
| close                | `() => void`    | Closes the date picker |


## Inline - Day Calendar

You can use the `<dp-day-calendar>` component to display the calendar widget without an associated input box.

i.e.
```html
<dp-day-calendar [(ngModel)]="selectedDate" [config]="config"></dp-day-calendar>
```

### Attributes:  
| Name                 | Type                | Default                                                                  | Description                                                                                                                                                                                                                                        |
|----------------------|:-------------------:|:------------------------------------------------------------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| required             | `Boolean`           | `undefined`                                                              | This is a validation rule, if there won't be any selected date then the containing form will be invalid.                                                                                                                                           |
| minDate              | `Moment\|String`    | `undefined`                                                              | This is a validation rule, if the selected date will be before `minDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                            |
| maxDate              | `Moment\|String`    | `undefined`                                                              | This is a validation rule, if the selected date will be after `maxDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                             |
| theme                | `String`            | `''`                                                                     | Theme is a class added to the popup container (and inner components) - this will allow styling of the calendar when it's appended to outer element (for example - body). There is a built in theme named dp-material, you can find it in the demo. |
| config               | `IDayPickerConfig`  | See Below                                                                | Configuration object - see description below.                                                                                                                                                                                                      |

### Configuration:  
In order to provide configurations to the day-calendar you need to pass it to the `dp-day-calendar` component:  
```html
<dp-day-calendar [(ngModel)]="selectedDate" [config]="config"></dp-day-calendar>
```
Here are the available configurations:  

| Name                        | Type                 | Default                                                                   | Description                                                                                                                                                                                                                                                                   |
|-----------------------------|:--------------------:|:-------------------------------------------------------------------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| format                      | `String`             | `"DD-MM-YYYY"`                                                            | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                              |
| firstDayOfWeek              | `String`             | `"su"`                                                                    | The first day of the calendar's week. Should be one of: `"su", "mo", "tu", "we", "th", "fr", "sa"`                                                                                                                                                                            |
| monthFormat                 | `String`             | `"MMM-YYYY"`                                                              | The date format of the day calendar, the one that seen above the calendar days. Will be overwritten if `monthFormatter` provided.                                                                                                                                             |
| monthFormatter              | `(Moment) => String` | `undefined`                                                               | The date formatter (callback function) of the day calendar, the one that seen above the calendar days.                                                                                                                                                                        |
| yearFormat                  | `String`             | `"YYYY"`                                                                  | The date format of the month calendar, the one that seen above the calendar months. Will be overwritten if `yearFormatter` provided. (available when `enableMonthSelector` is set to `true`).                                                                                 |
| yearFormatter               | `(Moment) => String` | `undefined`                                                               | The date formatter (callback function) of the month calendar, the one that seen above the calendar months. (available when `enableMonthSelector` is set to `true`).                                                                                                           |
| allowMultiSelect            | `Boolean`            | `undefined`                                                               | If set to `true` will allow for choosing multiple dates. `false` will force a single selection. If `undefined`, the picker will attempt to guess based on the type of the input value.                                                                                        |
| min                         | `Moment\|String`     | `undefined`                                                               | Disables all dates (on the date-picker) that are set to before the `min`, note that if invalid date would be set by the input then the date picker value would be the min date but the input will show the user typed date.                                                   |
| max                         | `Moment\|String`     | `undefined`                                                               | Disables all dates (on the date-picker) that are set to after the `max`, note that if invalid date would be set by the input then the date picker value would be the max date but the input will show the user typed date.                                                    |
| showNearMonthDays           | `Boolean`            | `true`                                                                    | Whether to show/hide next and previous month days.                                                                                                                                                                                                                            |
| showWeekNumbers             | `Boolean`            | `false`                                                                   | Whether to show/hide the week number of each week (iso week number).                                                                                                                                                                                                          |
| enableMonthSelector         | `Boolean`            | `true`                                                                    | Whether to enable/disable the selection of a moth granularity picker.                                                                                                                                                                                                         |
| isDayDisabledCallback       | `(Moment) => boolean`| `undefined`                                                               | Callback which should indicate if specific day is disabled.                                                                                                                                                                                                                   |
| isMonthDisabledCallback     | `(Moment) => boolean`| `undefined`                                                               | Callback which should indicate if specific month is disabled (month selector).                                                                                                                                                                                                |
| dayBtnFormat                | `String`             | `DD`                                                                      | The day format of the day button in the calendar.                                                                                                                                                                                                                             |
| dayBtnFormatter             | `(Moment) => String` | `undefined`                                                               | The formatter (callback function) of the day button in the calendar.                                                                                                                                                                                                          |
| monthBtnFormat              | `String`             | `DD`                                                                      | The month format of the month button in the calendar.                                                                                                                                                                                                                         |
| monthBtnFormatter           | `(Moment) => String` | `undefined`                                                               | The formatter (callback function) of the month button in the calendar.                                                                                                                                                                                                        |
| showMultipleYearsNavigation | `boolean`            | `false`                                                                   | If set to `true` will show buttons to navigate by multiple years (10 by default)                                                                                                                                                                                              |
| multipleYearsNavigateBy     | `number`             | `10`                                                                      | Number of years to navigate when showMultipleYearsNavigation is `true`                                                                                                                                                                                                        |

## Inline - Month Calendar

You can use the `<dp-month-calendar>` component to display the calendar widget without an associated input box.

i.e.
```html
<dp-month-calendar [(ngModel)]="selectedDate" [config]="config"></dp-month-calendar>
```

### Attributes:  
| Name                 | Type                 | Default              | Description                                                                                                                                                                                                                                        |
|----------------------|:--------------------:|:--------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| required             | `Boolean`            | `undefined`          | This is a validation rule, if there won't be any selected date then the containing form will be invalid.                                                                                                                                           |
| minDate              | `Moment\|String`     | `undefined`          | This is a validation rule, if the selected date will be before `minDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                            |
| maxDate              | `Moment\|String`     | `undefined`          | This is a validation rule, if the selected date will be after `maxDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                             |
| theme                | `String`             | `''`                 | Theme is a class added to the popup container (and inner components) - this will allow styling of the calendar when it's appended to outer element (for example - body). There is a built in theme named dp-material, you can find it in the demo. |
| config               | `IMonthPickerConfig` | See Below            | Configuration object - see description below.                                                                                                                                                                                                     |

### Configuration:  
In order to provide configurations to the month-calendar you need to pass it to the `dp-month-calendar` component:  
```html
<dp-month-calendar [(ngModel)]="selectedDate" [config]="config"></dp-month-calendar>
```
Here are the available configurations:  

| Name                        | Type                 | Default                                                                   | Description                                                                                                                                                                                                                                                                   |
|-----------------------------|:--------------------:|:-------------------------------------------------------------------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| format                      | `String`             | `"DD-MM-YYYY"`                                                            | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                              |
| yearFormat                  | `String`             | `"YYYY"`                                                                  | The date format of the month calendar, the one that seen above the calendar months. Will be overwritten if `yearFormatter` provided. (available when `enableMonthSelector` is set to `true`).                                                                                 |
| yearFormatter               | `(Moment) => String` | `undefined`                                                               | The date formatter (callback function) of the month calendar, the one that seen above the calendar months. (available when `enableMonthSelector` is set to `true`).                                                                                                           |
| allowMultiSelect            | `Boolean`            | `undefined`                                                               | If set to `true` will allow for choosing multiple dates. `false` will force a single selection. If `undefined`, the picker will attempt to guess based on the type of the input value.                                                                                        |
| min                         | `Moment\|String`     | `undefined`                                                               | Disables all dates (on the date-picker) that are set to before the `min`, note that if invalid date would be set by the input then the date picker value would be the min date but the input will show the user typed date.                                                   |
| max                         | `Moment\|String`     | `undefined`                                                               | Disables all dates (on the date-picker) that are set to after the `max`, note that if invalid date would be set by the input then the date picker value would be the max date but the input will show the user typed date.                                                    |
| isMonthDisabledCallback     | `(Moment) => boolean`| `undefined`                                                               | Callback which should indicate if specific month is disabled (month selector).                                                                                                                                                                                                |
| monthBtnFormat              | `String`             | `DD`                                                                      | The month format of the month button in the calendar.                                                                                                                                                                                                                         |
| monthBtnFormatter           | `(Moment) => String` | `undefined`                                                               | The formatter (callback function) of the month button in the calendar.                                                                                                                                                                                                        |
| showMultipleYearsNavigation | `boolean`            | `false`                                                                   | If set to `true` will show buttons to navigate by multiple years (10 by default)                                                                                                                                                                                              |
| multipleYearsNavigateBy     | `number`             | `10`                                                                      | Number of years to navigate when showMultipleYearsNavigation is `true`                                                                                                                                                                                                        |
| calendarSystem            | `ECalendarSystem`    | `ECalendarSystem.jalali`                                                     | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                             |

## Inline - Time Select

You can use the `<dp-time-select>` component to display the time select widget without an associated input box.

i.e.
```html
<dp-time-select [(ngModel)]="selectedDate" [config]="config"></dp-time-select>
```

### Attributes:  
| Name                 | Type                 | Default              | Description                                                                                                                                                                                                                                        |
|----------------------|:--------------------:|:--------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| required             | `Boolean`            | `undefined`          | This is a validation rule, if there won't be any selected date then the containing form will be invalid.                                                                                                                                           |
| minTime              | `Moment\|String`     | `undefined`          | This is a validation rule, if the selected date will be before `minTime` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                            |
| maxTime              | `Moment\|String`     | `undefined`          | This is a validation rule, if the selected date will be after `maxTime` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                             |
| theme                | `String`             | `''`                 | Theme is a class added to the popup container (and inner components) - this will allow styling of the calendar when it's appended to outer element (for example - body). There is a built in theme named dp-material, you can find it in the demo. |
| config               | `ITimeSelectConfig`  | See Below            | Configuration object - see description below.                                                                                                                                                                                                      |

### Configuration:  
In order to provide configurations to the time-select you need to pass it to the `dp-time-select` component:  
```html
<dp-time-select [(ngModel)]="selectedDate" [config]="config"></dp-time-select>
```
Here are the available configurations:  

| Name                      | Type                 | Default                                                                   | Description                                                                                                                                                                                                                                                                   |
|---------------------------|:--------------------:|:-------------------------------------------------------------------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| hours12Format             | `String`             | `"hh"`                                                                    | The hours format of the time select when `showTwentyFourHours` is `false`.                                                                                                                                                                                                    |
| hours24Format             | `String`             | `"HH"`                                                                    | The hours format of the time select when `showTwentyFourHours` is `true`.                                                                                                                                                                                                     |
| maxTime                   | `Moment\|String`     | `undefined`                                                               | Disables arrow buttons on the time select that would make the time after the `maxTime`.                                                                                                                                                                                       |
| meridiemFormat            | `String`             | `"A"`                                                                     | The AM/PM format of the time select when `showTwentyFourHours` is `false`.                                                                                                                                                                                                    |
| minTime                   | `Moment\|String`     | `undefined`                                                               | Disables arrow buttons on the time select that would make the time before the `minTime`.                                                                                                                                                                                      |
| minutesFormat             | `String`             | `"mm"`                                                                    | The minutes format of the time select.                                                                                                                                                                                                                                        |
| minutesInterval           | `number`             | `1`                                                                       | The number of minutes that will be added/subtracted when clicking up/down arrows on the time select.                                                                                                                                                                          |
| secondsFormat             | `String`             | `"ss"`                                                                    | The seconds format of the time select.                                                                                                                                                                                                                                        |
| secondsInterval           | `number`             | `1`                                                                       | The number of seconds that will be added/subtracted when clicking up/down arrows on the time select.                                                                                                                                                                          |
| showSeconds               | `boolean`            | `false`                                                                   | If set to `true` will show seconds in the time select, otherwise, won't.                                                                                                                                                                                                      |
| showTwentyFourHours       | `boolean`            | `false`                                                                   | If set to `true` will show hours in 24 hour format. `false` will show hours in 12 hours format and append AM/PM to the end of the time select.                                                                                                                                |
| timeSeparator             | `String`             | `":"`                                                                     | The separator that will be placed between hours and minutes and between minutes and seconds on the time select.                                                                                                                                                               |
| calendarSystem            | `ECalendarSystem`    | `ECalendarSystem.jalali`                                                            | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                    |

## Inline - DayTime Calendar

You can use the `<dp-day-time-calendar>` component to display the calendar widget and time select widget without an associated input box.

i.e.
```html
<dp-day-time-calendar [(ngModel)]="selectedDate" [config]="config"></dp-day-time-calendar>
```

### Attributes:  
| Name                 | Type                | Default                                                                  | Description                                                                                                                                                                                                                                        |
|----------------------|:-------------------:|:------------------------------------------------------------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| required             | `Boolean`           | `undefined`                                                              | This is a validation rule, if there won't be any selected date then the containing form will be invalid.                                                                                                                                           |
| minDate              | `Moment\|String`    | `undefined`                                                              | This is a validation rule, if the selected date will be before `minDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                            |
| maxDate              | `Moment\|String`    | `undefined`                                                              | This is a validation rule, if the selected date will be after `maxDate` the containing form will be invalid. Note: if provided as string format configuration should be provided in the config object.                                             |
| theme                | `String`            | `''`                                                                     | Theme is a class added to the popup container (and inner components) - this will allow styling of the calendar when it's appended to outer element (for example - body). There is a built in theme named dp-material, you can find it in the demo. |
| config               | `IDayPickerConfig`  | See Below                                                                | Configuration object - see description below.                                                                                                                                                                                                      |

### Configuration:  
In order to provide configurations to the day-time-calendar you need to pass it to the `dp-day-time-calendar` component:  
```html
<dp-day-time-calendar [(ngModel)]="selectedDate" [config]="config"></dp-day-time-calendar>
```
Here are the available configurations:  

| Name                        | Type                 | Default                                                                   | Description                                                                                                                                                                                                                                                                   |
|-----------------------------|:--------------------:|:-------------------------------------------------------------------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| format                      | `String`             | `"DD-MM-YYYY"`                                                            | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                              |
| firstDayOfWeek              | `String`             | `"su"`                                                                    | The first day of the calendar's week. Should be one of: `"su", "mo", "tu", "we", "th", "fr", "sa"`                                                                                                                                                                            |
| monthFormat                 | `String`             | `"MMM-YYYY"`                                                              | The date format of the day calendar, the one that seen above the calendar days. Will be overwritten if `monthFormatter` provided.                                                                                                                                             |
| monthFormatter              | `(Moment) => String` | `undefined`                                                               | The date formatter (callback function) of the day calendar, the one that seen above the calendar days.                                                                                                                                                                        |
| yearFormat                  | `String`             | `"YYYY"`                                                                  | The date format of the month calendar, the one that seen above the calendar months. Will be overwritten if `yearFormatter` provided. (available when `enableMonthSelector` is set to `true`).                                                                                 |
| yearFormatter               | `(Moment) => String` | `undefined`                                                               | The date formatter (callback function) of the month calendar, the one that seen above the calendar months. (available when `enableMonthSelector` is set to `true`).                                                                                                           |
| allowMultiSelect            | `Boolean`            | `undefined`                                                               | If set to `true` will allow for choosing multiple dates. `false` will force a single selection. If `undefined`, the picker will attempt to guess based on the type of the input value.                                                                                        |
| min                         | `Moment\|String`     | `undefined`                                                               | Disables all dates (on the date-picker) that are set to before the `min`, note that if invalid date would be set by the input then the date picker value would be the min date but the input will show the user typed date.                                                   |
| max                         | `Moment\|String`     | `undefined`                                                               | Disables all dates (on the date-picker) that are set to after the `max`, note that if invalid date would be set by the input then the date picker value would be the max date but the input will show the user typed date.                                                    |
| showNearMonthDays           | `Boolean`            | `true`                                                                    | Whether to show/hide next and previous month days.                                                                                                                                                                                                                            |
| showWeekNumbers             | `Boolean`            | `false`                                                                   | Whether to show/hide the week number of each week (iso week number).                                                                                                                                                                                                          |
| enableMonthSelector         | `Boolean`            | `true`                                                                    | Whether to enable/disable the selection of a moth granularity picker.                                                                                                                                                                                                         |
| isDayDisabledCallback       | `(Moment) => boolean`| `undefined`                                                               | Callback which should indicate if specific day is disabled.                                                                                                                                                                                                                   |
| isMonthDisabledCallback     | `(Moment) => boolean`| `undefined`                                                               | Callback which should indicate if specific month is disabled (month selector).                                                                                                                                                                                                |
| dayBtnFormat                | `String`             | `DD`                                                                      | The day format of the day button in the calendar.                                                                                                                                                                                                                             |
| dayBtnFormatter             | `(Moment) => String` | `undefined`                                                               | The formatter (callback function) of the day button in the calendar.                                                                                                                                                                                                          |
| monthBtnFormat              | `String`             | `DD`                                                                      | The month format of the month button in the calendar.                                                                                                                                                                                                                         |
| monthBtnFormatter           | `(Moment) => String` | `undefined`                                                               | The formatter (callback function) of the month button in the calendar.                                                                                                                                                                                                        |
| hours12Format               | `String`             | `"hh"`                                                                    | The hours format of the time select when `showTwentyFourHours` is `false`.                                                                                                                                                                                                    |
| hours24Format               | `String`             | `"HH"`                                                                    | The hours format of the time select when `showTwentyFourHours` is `true`.                                                                                                                                                                                                     |
| meridiemFormat              | `String`             | `"A"`                                                                     | The AM/PM format of the time select when `showTwentyFourHours` is `false`.                                                                                                                                                                                                    |
| minutesFormat               | `String`             | `"mm"`                                                                    | The minutes format of the time select.                                                                                                                                                                                                                                        |
| minutesInterval             | `number`             | `1`                                                                       | The number of minutes that will be added/subtracted when clicking up/down arrows on the time select.                                                                                                                                                                          |
| secondsFormat               | `String`             | `"ss"`                                                                    | The seconds format of the time select.                                                                                                                                                                                                                                        |
| secondsInterval             | `number`             | `1`                                                                       | The number of seconds that will be added/subtracted when clicking up/down arrows on the time select.                                                                                                                                                                          |
| showSeconds                 | `boolean`            | `false`                                                                   | If set to `true` will show seconds in the time select, otherwise, won't.                                                                                                                                                                                                      |
| showTwentyFourHours         | `boolean`            | `false`                                                                   | If set to `true` will show hours in 24 hour format. `false` will show hours in 12 hours format and append AM/PM to the end of the time select.                                                                                                                                |
| timeSeparator               | `String`             | `":"`                                                                     | The separator that will be placed between hours and minutes and between minutes and seconds on the time select.                                                                                                                                                               |
| showMultipleYearsNavigation | `boolean`            | `false`                                                                   | If set to `true` will show buttons to navigate by multiple years (10 by default)                                                                                                                                                                                              |
| multipleYearsNavigateBy     | `number`             | `10`                                                                      | Number of years to navigate when showMultipleYearsNavigation is `true`                                                                                                                                                                                                        |
| calendarSystem              | `ECalendarSystem`    | `ECalendarSystem.jalali`                                                            | If ngModel provided as `String` the format is required, this format also will be used as the input format style.                                                                                                                                                    |

## Directive

You can use the `[dpDayPicker]` directive to attach the picker to any component with an `ngModel` or a `FormControl` (using reactive forms).

i.e.
```html
<input name="someName" [(ngModel)]="selectedDate" [dpDayPicker]="config" />
```

or using reactive forms:
```html
<input name="someName" formControlName="selectedDate" [dpDayPicker]="config" />
<!-- OR -->
<input name="someName" [formControl]="selectedDateFormControl" [dpDayPicker]="config" />
```

or with `@angular/material`:
```html
<md-input-container>
  <input mdInput name="someName" [(ngModel)]="selectedDate" [dpDayPicker]="config" theme="dp-material" attachTo=".mat-input-wrapper" />
</md-input-container>
```

### Attributes:  
| Name                 | Type                                      | Default       | Description                                                                                                                                                                                                                                        |
|----------------------|:-----------------------------------------:|:-------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mode                 | `'day'\|'month'\|'time'\|'daytime'`       | `'day'`       | the type of the calender which will be displayed in the picker                                                                                                                                                                                     |
| attachTo             | `ElementRef\|String`                      | `undefined`   | the element used to position the picker.  If `attachTo` is a `String`, it is used as a css selector to match any parent of the directive's host component.  If `attachTo` is `undefined`, the host component itself is used.                       |
| theme                | `String`                                  | `''`          | Theme is a class added to the popup container (and inner components) - this will allow styling of the calendar when it's appended to outer element (for example - body). There is a built in theme named dp-material, you can find it in the demo. |
| config               | `IDatePickerDirectiveConfig`              | See Below     | Configuration object - see description below.                                                                                                                                                                                                      |

### Configuration:  
In order to provide configurations to the date-picker you need to pass it to the `[dpDayPicker]` directive:  
```html
<input [(ngModel)]="selectedDate" [dpDayPicker]="datePickerConfig" />
```

The `IDatePickerDirectiveConfig` is identical to [`IDatePickerConfig`](#configuration) above except that it lacks the `showGoToCurrent` property.
