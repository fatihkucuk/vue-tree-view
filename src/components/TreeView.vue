<template>
  <div style="position:relative">
    <ul class="item-list" :style="{ 'margin-top': this.marginTop + 'px' }">
      <li
        :ref="item.id"
        class="item-list-item"
        :style="getListItemStyle"
        v-for="item of items"
        :key="item.id"
        @click="toggleItem(item)"
      >
        {{ item.value }}
      </li>
    </ul>

    <TreeView
      v-if="
        selectedItem &&
          selectedItem.children &&
          selectedItem.children.length > 0
      "
      :items="selectedItem.children"
      :marginTop="computedMarginTop"
    ></TreeView>
  </div>
</template>

<script>
import TreeView from "../components/TreeView";
export default {
  name: "TreeView",
  components: {
    TreeView
  },
  created() {},
  mounted() {},
  data: () => {
    return {
      selectedItem: null,
      listItemHeight: 18,
      listItemPadding: 20,
      listItemBorder: 1,
      listWidth: 200
    };
  },
  props: {
    items: Array,
    marginTop: Number
  },
  methods: {
    toggleItem(item) {
      item.selected = !item.selected;

      if (item.selected) {
        this.items.forEach(element => {
          if (element.id != item.id) {
            this.selectedItem = null;
            element.selected = false;
          }
        });
        this.$nextTick(() => {
          this.selectedItem = this.copy(item);
        });
      } else {
        this.selectedItem = null;
      }
    },
    copy(item) {
      return JSON.parse(JSON.stringify(item));
    }
  },
  computed: {
    listItemTotalHeight() {
      if (this.selectedItem && this.selectedItem.id == 1) {
        return `
        height: ${this.listItemHeight +
          this.listItemPadding * 2 +
          this.listItemBorder}px;
        `;
      }
      return "";
    },
    getListItemStyle() {
      return `
        height: ${this.listItemHeight}px;
        padding: ${this.listItemPadding}px;
        border: ${this.listItemBorder}px solid;
        `;
    },
    computedMarginTop() {
      if (
        this.selectedItem &&
        this.selectedItem.children &&
        this.selectedItem.children.length > 0
      ) {
        let computedMarginTop = this.$refs[this.selectedItem.id][0].offsetTop;
        if (this.selectedItem.parentId === null) {
          computedMarginTop--;
        }
        return computedMarginTop;
      }
      return 0;
    }
  },
  watch: {}
};
</script>

<style>
.item-list {
  list-style-type: none;
  float: left;
  min-width: 200px;
  padding: 0;
  margin-top: 0;
}
.item-list-item {
  border-top: none !important;
  text-align: center;
  cursor: pointer;
  user-select: none;
}
.item-list-item:first-child {
  border-top: 1px solid !important;
  text-align: center;
}
</style>
