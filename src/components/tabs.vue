<template>
  <ul class="nav nav-tabs nav-fill">
    <li
      v-for="(tab,key) in ListTabs"
      :key="key"
      :class="ThisIsActive(tab)"
      @click="ActiveThis(tab)"
    >{{tab}}</li>
  </ul>
</template>
<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "Tabs",
  props: {
    ListTabs: Array
  },
  data() {
    return {
      tabActive: ""
    };
  },
  methods: {
    ActiveThis: function(este: String) {
      console.log(este);
      if (this.ListTabs.includes(este)) this.tabActive = este;

      this.$emit("tabSelect", this.ListTabs.indexOf(este));
    },
    ThisIsActive: function(este: String) {
      if (this.tabActive == este) return "nav-item nav-link active";
      return "nav-item nav-link";
    }
  }
});
</script>