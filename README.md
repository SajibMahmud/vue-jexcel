# vue-jexcel

**vue-jexcel** is a wrapper for [Jexcel CE](https://github.com/jspreadsheet/jexcel) in vue. You can easily create reuseable spreadsheet components.

[[toc]]

## Installation

```
npm install vue-jexcel
```

## Usage

### Bundler (Webpack, Rollup)

```js
import Vue from "vue";
import VueJexcel from "vue-jexcel";

Vue.use(VueJexcel);
```

### Browser

```html
<!-- Include after Vue -->
<!-- Local files -->
<script src="vue-jexcel/dist/vue-jexcel.js"></script>

<!-- From CDN -->
<script src="https://unpkg.com/vue-jexcel"></script>
```

## How to use

You need to import the component and thenplace it inside your components.

```javascript
<template>
  <vue-jexcel :data="data" :columns="columns" />
</template>

<script>
import VueJexcel from 'vue-jexcel'
export default {
  components: { VueJexcel },
  data: [{1, "Adam"}, {2, "Boy"}],
  columns: [{ title: 'Index' }, { title: 'Name' }]
}
</script>
```
