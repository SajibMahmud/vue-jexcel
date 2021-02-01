<template>
  <div ref="spreadsheet"></div>
</template>

<script>
import jexcel from 'jexcel';
import 'jexcel/dist/jexcel.css';

export default {
  name: 'VueJexcel',
  components: { },
  props: {
    data: {
      type: Array,
      required: true,
    },
    columns: {
      type: Array,
      required: true,
    },
    allowToolbar: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      initialized: false,
    };
  },
  computed: {      
    options() {
      return {
        data: this.data,
        columns: this.columns,
        allowToolbar: this.allowToolbar,
        onchange: (instance, cell, x, y, value) => this.$emit('onchange', { instance, cell, x, y, value }),
        onsort: (obj, cell) => this.$emit('onsort', { obj, cell }),
        updateTable: (instance, cell, x, y, source, value, id) => this.$emit('updateTable', { instance, cell, x, y, source, value, id }),
        onpaste: (instance, data) => this.$emit('onpaste', { instance, data }),
      };
    },
  },
  watch: {
    columns(list) {
      if (!this.initialized) {
        this.initialized = true;
        list.forEach((header, index) => this.table.insertColumn(1, index, false, header));
      }
    },
    data(list) {
      this.table.setData(list);
    },
  },
  mounted() {
    const table = jexcel(this.$refs.spreadsheet, this.options);
    Object.assign(this, { table }); 
  },
  methods: {
  },
};
</script>

<style>
</style>
