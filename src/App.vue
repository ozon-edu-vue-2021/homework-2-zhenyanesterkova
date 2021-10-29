<template>
  <div id="app" >
    <div>{{ selectedPath }}</div>
    <folder-comp v-bind="contents" @selected="selectedPath = $event" />      
    </div>
</template>

<script>
import FolderComp from "./components/FolderComp.vue";
import json from "../public/static/node_modules.json";

export default {
  name: "App",
  data() {
    return {
      contents: json,
      selectedPath: "",
    };
  },
  methods: {
    compType(type) {
      switch(type) {
        case "file":
          return "FileComp";
        case "link":
          return "LinkComp";
        case "directory":
          return "FolderComp";
      }
      return null;
    }
  },
  components: {
    FolderComp
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin: 60px 100px 0;
}
img {
  vertical-align: middle;
}
</style>
