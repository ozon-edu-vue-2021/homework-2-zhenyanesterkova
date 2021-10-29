<template>
  <div>
    <div
      @click="openFolder"
      class="folder"
      tabindex="1"
      ref="folder"
      @keydown.enter="openFolder"
      @focus.stop="$emit('selected', name)"
    >
      <img src="../assets/img/FolderIcon.svg" alt="Иконка папки" />
      <span>
        {{ name }}
      </span>
    </div>
    <div class="contents" v-if="opened">
      <component
        v-for="(content, i) in contents"
        :key="content.name"
        :is="compType(content.type)"
        @keydown.down.native.stop="focusNext(i)"
        @keydown.up.native.stop="focusPrev(i)"
        @endFolder="focusNextSibling(i)"
        @focus.native.stop="emitPath(i)"
        @selected="updatePath($event)"
        v-bind="content"
        ref="contents"
      />
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
    focusNext(i) {
      let current = this.$refs.contents[i];
      if (current.$attrs.type === "directory" && current.opened) {
        current.$refs.contents[0].focus();
      } else if (i < this.$refs.contents.length - 1) {
        this.$refs.contents[i + 1].focus();
      } else {
        this.$emit("endFolder");
      }
    },
    focusPrev(i) {
      if (i > 0) {
        this.$refs.contents[i - 1].focus();
      } else {
        this.focus();
      }
    },
    focus() {
      this.$refs.folder.focus();
    },
    compType(type) {
      switch (type) {
        case "file":
          return "FileComp";
        case "link":
          return "LinkComp";
        case "directory":
          return "FolderComp";
      }
      return null;
    },
    focusNextSibling(i) {
      if (i < this.$refs.contents.length - 1) {
        this.$refs.contents[i + 1].focus();
      } else {
        this.$emit("endFolder");
      }
    },
    emitPath(i) {
      this.$emit("selected", `${this.name}/${this.$refs.contents[i].name}`);
    },
    updatePath(path) {
      this.$emit("selected", `${this.name}/${path}`);
    },
  },
  components: {
    FileComp,
    LinkComp,
  },
};
</script>

<style scoped>
.contents {
  padding-left: 30px;
}
.folder {
  width: fit-content;
  padding: 5px;
  cursor: pointer;
}
.folder:focus-within {
  outline: 1px dashed grey;
}
</style>