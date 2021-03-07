<script>
import Vue from "vue";
// Uncomment import and local "components" registration if library is not registered globally.
import { ControlWidget } from "@/entry.esm";

export default Vue.extend({
  name: "ServeDev",
  components: {
    ControlWidget,
  },
  data() {
    return {
      controlData: true,
    };
  },
  methods: {
    click() {},
  },
});
</script>

<template>
  <div id="app">
    <control-widget :change="controlData" @buttonClick="click()" />
  </div>
</template>
