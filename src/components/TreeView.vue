<template>
  <div class="container" :style="{ width: this.containerWidth }">
    <ul class="item-list" :style="{ 'margin-top': this.marginTop + 'px' }">
      <li
        class="item-list-item"
        :ref="item.id"
        :style="getListItemStyle"
        :key="item.id"
        v-for="item of items"
        :title="item.value"
        @mouseenter="toggleItem(item)"
        @click="selectItem($event, item)"
      >
        {{ item.value }}
        <span
          v-if="item.children && item.children.length > 0"
          class="arrow-right"
        ></span>
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
      @selected-item-change="onChangeSelectedItem($event)"
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
  mounted() {
    window.addEventListener("click", this.windowClicked);
  },
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
      const self = this;
      setTimeout(() => {
        if (self.selectedItem) {
          if (self.selectedItem.id != item.id) item.selected = !item.selected;
        } else {
          item.selected = !item.selected;
        }
        if (item.selected) {
          self.deselectAllItems(item.id);
          self.$nextTick(() => {
            self.selectedItem = self.copy(item);
          });
        } else {
          self.selectedItem = null;
        }
      }, 250);
    },
    copy(item) {
      return JSON.parse(JSON.stringify(item));
    },
    windowClicked() {
      if (this.selectedItem) this.deselectAllItems();
    },
    deselectAllItems(exceptThisId = null) {
      this.items.forEach(element => {
        if (exceptThisId) {
          if (element.id != exceptThisId) {
            element.selected = false;
          }
        } else {
          element.selected = false;
        }
      });
      this.selectedItem = null;
    },
    selectItem(event, item) {
      if (item.children.length === 0) {
        this.$emit("selected-item-change", item);
      } else {
        event.preventDefault();
        event.stopPropagation();
      }
    },
    onChangeSelectedItem(selectedItem) {
      this.$emit("selected-item-change", selectedItem);
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
        border: ${this.listItemBorder}px solid #d1d1d1;
        `;
    },
    computedMarginTop() {
      if (
        this.selectedItem &&
        this.selectedItem.children &&
        this.selectedItem.children.length > 0
      ) {
        let computedMarginTop = this.$refs[this.selectedItem.id][0].offsetTop;
        let index = 1;

        if (computedMarginTop > 0) {
          index = Math.ceil(computedMarginTop / 60 + 1);
        }
        computedMarginTop = (index - 1) * 60 - (index - 1);

        return computedMarginTop;
      }
      return 0;
    },
    containerWidth() {
      return "";
    }
  },
  watch: {}
};
</script>

<style scoped>
.container {
  position: relative;
}
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
  position: relative;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  width: 180px;
}
.item-list-item:first-child {
  border-top: 1px solid #d1d1d1 !important;
  text-align: center;
}
.arrow-right {
  position: absolute;
  right: 2px;
  width: 0;
  height: 0;
  top: 50%;
  transform: translate(-50%, -50%);
  border-top: 6px solid transparent;
  border-bottom: 6px solid transparent;
  border-left: 6px solid #aaa;
}
</style>
