<template>
  <div id="app">
    <TreeViewContainer
      :items="items"
      @selected-item-change="onChangeSelectedItem($event)"
    ></TreeViewContainer>
  </div>
</template>

<script>
import TreeViewContainer from "./components/TreeViewContainer.vue";

import { v1 as uuidv1 } from "uuid";

export default {
  name: "App",
  components: {
    TreeViewContainer
  },
  data: () => {
    return {
      items: [
        {
          id: uuidv1(),
          value: "this item has very long name like this",
          selected: false,
          parentId: null,
          children: [
            {
              id: uuidv1(),
              value: "item",
              selected: false,
              parentId: 1,
              children: [
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: [
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: [
                        {
                          id: uuidv1(),
                          value: "item",
                          selected: false,
                          parentId: 2,
                          children: []
                        }
                      ]
                    },
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: []
                    },
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: [
                        {
                          id: uuidv1(),
                          value: "item",
                          selected: false,
                          parentId: 2,
                          children: []
                        }
                      ]
                    }
                  ]
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: [
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: []
                    },
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: []
                    }
                  ]
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: [
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: []
                    }
                  ]
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: [
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 2,
                      children: [
                        {
                          id: uuidv1(),
                          value: "item",
                          selected: false,
                          parentId: 2,
                          children: []
                        },
                        {
                          id: uuidv1(),
                          value: "item",
                          selected: false,
                          parentId: 2,
                          children: []
                        },
                        {
                          id: uuidv1(),
                          value: "item",
                          selected: false,
                          parentId: 2,
                          children: [
                            {
                              id: uuidv1(),
                              value: "item",
                              selected: false,
                              parentId: 2,
                              children: []
                            }
                          ]
                        }
                      ]
                    }
                  ]
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: []
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: []
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: []
                },
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 2,
                  children: []
                }
              ]
            }
          ]
        },
        {
          id: uuidv1(),
          value: "item",
          selected: false,
          parentId: null,
          children: [
            {
              id: uuidv1(),
              value: "item",
              selected: false,
              parentId: 4,
              children: [
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 5,
                  children: [
                    {
                      id: uuidv1(),
                      value: "item",
                      selected: false,
                      parentId: 6,
                      children: [
                        {
                          id: uuidv1(),
                          value: "item",
                          selected: false,
                          parentId: 12,
                          children: [
                            {
                              id: uuidv1(),
                              value: "item",
                              selected: false,
                              parentId: 13,
                              children: []
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            },
            {
              id: uuidv1(),
              value: "item",
              selected: false,
              parentId: 4,
              children: [
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 16,
                  children: []
                }
              ]
            },
            {
              id: uuidv1(),
              value: "item",
              selected: false,
              parentId: 4,
              children: []
            },
            {
              id: uuidv1(),
              value: "item",
              selected: false,
              parentId: 4,
              children: []
            }
          ]
        },
        {
          id: uuidv1(),
          value: "item",
          selected: false,
          parentId: null,
          children: [
            {
              id: uuidv1(),
              value: "item",
              selected: false,
              parentId: 7,
              children: [
                {
                  id: uuidv1(),
                  value: "item",
                  selected: false,
                  parentId: 8,
                  children: []
                }
              ]
            }
          ]
        }
      ]
    };
  },
  methods: {
    onChangeSelectedItem(item) {
      console.log(item.value);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
