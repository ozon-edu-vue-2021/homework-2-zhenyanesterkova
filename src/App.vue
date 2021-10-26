<template>
  <div id="app">
    <folder-comp
      :folderName = folders.name
      contents = {}
    />
    <file-comp
      fileName = 'file'
    />
    <link-comp
      linkName = 'link'
    />
    
  </div>
</template>

<script>
import FolderComp from './components/FolderComp.vue';
import FileComp from './components/FileComp.vue';
import LinkComp from './components/LinkComp.vue';
import json from '../public/static/node_modules.json'

export default {
  name: 'App',
  data() {
    return{
      folders: json
    }
  },
  // methods: {
  //   initfolders(){

  //   }
  // },
  components: {
    FolderComp,
    FileComp,
    LinkComp
  }
}
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
img{
  vertical-align: middle;
}
</style>
