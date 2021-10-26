<template>
  <div>
    <div @click="openFolder" class="folder">
      <img src="../assets/img/FolderIcon.svg" alt="Иконка папки" />
      <span>
        {{ name }}
      </span>
    </div>
    <div class="contents" v-if="opened">
      <div v-for="content in contents" :key="content.name">
        <folder-comp
          v-if="content.type === 'directory'"
          :name="content.name"
          :contents="content.contents"
        />
        <file-comp v-if="content.type === 'file'" :fileName="content.name" />
        <link-comp v-if="content.type === 'link'" :linkName="content.name" :target="content.target"/>
      </div>
    </div>
  </div>
</template>

<script>
import FileComp from "./FileComp.vue";
import LinkComp from "./LinkComp.vue";

export default {
  name: "FolderComp",
  props: {
    name: {
      type: String,
      default: "",
    },
    contents: {
      type: Array,
      default: () => {
        return [];
      },
    },
  },
  data() {
    return {
      opened: false,
    };
  },
  methods: {
    openFolder() {
      this.opened = !this.opened;
    },
  },
  components: {
    FileComp,
    LinkComp,
  },
};
</script>

<style scoped>
    .contents{
        padding-left: 30px;
    }
    .folder{
        width: fit-content;
        padding: 5px;
        cursor: pointer;
    }
</style>