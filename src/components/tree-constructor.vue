<template>
  <div class="col col-3" ref="treebase">
    <slot></slot>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import TreeNode from "./tree-node.vue";

export default Vue.extend({
  name: "tree-contructor",
  components: { TreeNode },
  data() {
    return {
      arbol: [
        { id: 1, parent: -1, nombre: "Reconquista" },
        { id: 2, parent: 1, nombre: "San Gerónimo" },
        { id: 3, parent: 2, nombre: "Cale 52" },
        { id: 4, parent: 3, nombre: "Mi Casa" },
        { id: 5, parent: 3, nombre: "Tu Casa" },
        { id: 6, parent: 1, nombre: "Hospital" }
      ]
    };
  },
  mounted() {
    let treebase = this.$refs.treebase;

    let TreeNodeClass = Vue.extend(TreeNode);
    var list_node: Object[];

    this.arbol.forEach(element => {
      let base = new TreeNodeClass();
      base.$props.nombre = element.nombre;
      base.$mount();
      if (list_node.length != 0) {
        list_node.forEach(dom => {
          if (dom.id == element.parent) {
            break;
          }
        });
      }

      list_node.push({ id: element.id, dom: base });
    });

    treebase.appendChild(base.$el);

    console.log(this.$refs.Joder);
    //console.log();
  }
});
</script>