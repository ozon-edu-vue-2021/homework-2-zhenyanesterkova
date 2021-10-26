<template>
  <div>
    <div>
      <img src="../assets/img/FolderIcon.svg" alt="Иконка папки" />
      <span>
        {{ contents.name }}
      </span>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "FolderComp",
  props: {
    contents: {
      type: Object,
      default: () => {
        return {}
      },
    },
  },
};
</script>