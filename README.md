![image](https://user-images.githubusercontent.com/5319267/28922057-f0d471fa-7858-11e7-8478-010657fd0e60.png)

[![Greenkeeper badge](https://badges.greenkeeper.io/biig-io/ngx-tabset.svg)](https://greenkeeper.io/)
[![Build Status](https://travis-ci.org/biig-io/ngx-tabset.svg?branch=master)](https://travis-ci.org/biig-io/ngx-tabset) [![npm version](https://badge.fury.io/js/ngx-tabset.svg)](https://badge.fury.io/js/ngx-tabset) [![npm downloads](https://img.shields.io/npm/dm/ngx-tabset.svg)](https://npmjs.org/ngx-tabset) [![codecov](https://codecov.io/gh/biig-io/ngx-tabset/branch/master/graph/badge.svg)](https://codecov.io/gh/biig-io/ngx-tabset)

`ngx-tabset` is a very simple library (less than 14ko!) to let you create some tabs. It uses flex-box and is 
compatible with Angular >=2.0.0.

## Demo
http://biig-io.github.io/ngx-tabset/

**This library doesn't use any framework (no CSS library, no JQuery...)**

## Setup
To use `ngx-tabset` in your project install it via [npm](https://www.npmjs.com/package/ngx-tabset) / [yarn](https://yarnpkg.com/fr/package/ngx-tabset):
```
npm i ngx-tabset --save
```
or
```
yarn add ngx-tabset
```

If you are using system.js you may want to add this into `map` and `package` config:
    
```json
{
    "map": {
        "ngx-tabs": "node_modules/ngx-tabset"
    },
    "packages": {
        "ngx-tabset": { "main": "index.js", "defaultExtension": "js" }
    }
}
```

## Usage

Import `TabsModule` in your app module and start using it in any component:
```typescript
import {BrowserModule} from '@angular/platform-browser';
import {NgModule} from '@angular/core';

import {AppComponent} from './app.component';
import {TabsModule} from 'ngx-tabset';
import {CommonModule} from '@angular/common';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    CommonModule,
    TabsModule.forRoot()
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {
}
```

### Basic example
```html
<ngx-tabset>
  <ngx-tab title="About me">
    Its all about me.
  </ngx-tab>
  <ngx-tab title="Contacts">
    This is content of the contacts tab
  </ngx-tab>
  <ngx-tab title="Map" [disabled]="true">
    Content of the Map Tab
  </ngx-tab>
</ngx-tabset>
```

### More complete example
```html
<ngx-tabset [disableStyle]="true" (onSelect)="doSomethingOnTabSelect($event)">
    <ngx-tab title="Tab title" [disabled]="false" [active]="true">
        <span *tabHeading>
            <b style="color: deepskyblue">Dynamic html</b> <i style="color: deeppink">tab heading</i>
        </span>
        Tab contents.
    </ngx-tab>
    ...
</ngx-tabset>
```

* `<ngx-tabset>` is a container for all tabs
    * `[disableStyle]="true|false"` Disables/enables the built-in style. It allows you to style the entire tab yourself
    * `(onSelect)="doSomethingOnTabSelect($event)"` Callback to be called when tab is being selected
* `<ngx-tab>` is a single tab item
    * `title` Simple tab title
    * `[disabled]="true|false` Indicates if current tab is enabled or disabled
    * `<span *tabHeading>...</span>` Allows to specify dynamic html content of the tab title
    * `[active]="true|false"` Specifies which tab should be active on init. By default the first tab will be active

### Style and customization options
`ngx-tabset` comes with several options in order to facilitate integration (with CSS frameworks, custom style, etc.).

The below documentation will use the following pattern: 
> `parameter/option name` (type) | default value | required? ― _description_

- `disableStyle` (boolean) | `false` ― _Enable / disable default tabset style_

- `animate` (boolean) | `true` ― _Enable / disable the tabs transition animation_

- `customNavClass` (string) | `''` ― _All the additionnal classes you want to add to the tabset **header** (e.g.: any bootstrap modal class). You can add several classes by giving a string with space-separated classnames_

- `customTabsClass` (string) | `''` ― _All the additionnal classes you want to add to the tabset **container** (e.g.: any bootstrap modal class). You can add several classes by giving a string with space-separated classnames_

