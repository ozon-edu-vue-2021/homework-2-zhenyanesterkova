<template>
  <div>
    <div>
      <img src="../assets/img/FolderIcon.svg" alt="Иконка папки" />
      <span>
        {{ folderName }}
      </span>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "FolderComp",
  props: {
    folderName: {
      type: String,
      default: "",
    },
    // contents: {
    //   type: Object,
    //   default: () => {
    //     let folderName = 'def';
    //     let contents = {};
    //     return {folderName, contents}
    //   },
    // },
  },
};
</script>