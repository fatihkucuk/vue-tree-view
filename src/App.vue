<template>
  <div id="app">
    <TreeView :items="items"></TreeView>
  </div>
</template>

<script>
import TreeView from "./components/TreeView.vue";

export default {
  name: "App",
  components: {
    TreeView
  },
  data: () => {
    return {
      items: [
        {
          id: 1,
          value: "1.0",
          selected: false,
          parentId: null,
          children: [
            {
              id: 2,
              value: "1.1",
              selected: false,
              children: [{ id: 3, value: "1.2", selected: false, children: [] }]
            }
          ]
        },
        {
          id: 4,
          value: "2.0",
          selected: false,
          parentId: null,
          children: [
            {
              id: 5,
              value: "2.1",
              selected: false,
              children: [
                {
                  id: 6,
                  value: "2.2",
                  selected: false,
                  children: [
                    {
                      id: 12,
                      value: "2.0",
                      selected: false,
                      children: [
                        {
                          id: 13,
                          value: "2.1",
                          selected: false,
                          children: [
                            {
                              id: 14,
                              value: "2.2",
                              selected: false,
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
              id: 16,
              value: "2.2",
              selected: false,
              children: [
                {
                  id: 19,
                  value: "2.2",
                  selected: false,
                  children: []
                }
              ]
            },
            {
              id: 17,
              value: "2.2",
              selected: false,
              children: []
            },
            {
              id: 18,
              value: "2.2",
              selected: false,
              children: []
            }
          ]
        },
        {
          id: 7,
          value: "3.0",
          selected: false,
          parentId: null,
          children: [
            {
              id: 8,
              value: "3.1",
              selected: false,
              children: [{ id: 9, value: "3.2", selected: false, children: [] }]
            }
          ]
        }
      ]
    };
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
  margin-top: 60px;
}
</style>
