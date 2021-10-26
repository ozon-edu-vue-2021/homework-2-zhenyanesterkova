<template>
  <div id="app">
      <folder-comp
        v-if="contents.type === 'directory'"
        :name="contents.name"
        :contents="contents.contents"
      />
      <file-comp v-if="contents.type === 'file'" fileName="contents.name" />
      <link-comp v-if="contents.type === 'link'" linkName="contents.name" />
    </div>
</template>

<script>
import FolderComp from "./components/FolderComp.vue";
import FileComp from "./components/FileComp.vue";
import LinkComp from "./components/LinkComp.vue";
import json from "../public/static/node_modules.json";

export default {
  name: "App",
  data() {
    return {
      contents: json,
    };
  },
  components: {
    FolderComp,
    FileComp,
    LinkComp,
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
