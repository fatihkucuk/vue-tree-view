<template>
  <div class="tree-view-container">
    <TreeView
      :items="items"
      @selected-item-change="onChangeSelectedItem($event)"
    ></TreeView>
  </div>
</template>
<script>
import TreeView from "../components/TreeView";

export default {
  name: "TreeViewContainer",
  components: {
    TreeView
  },
  props: {
    items: Array,
    marginTop: Number
  },
  methods: {
    onChangeSelectedItem(selectedItem) {
      this.$emit("selected-item-change", selectedItem);
    }
  }
};
</script>

<style scoped>
.tree-view-container {
  width: 100%;
  height: 100%;
  overflow-x: auto;
  overflow-y: auto;
}
</style>
