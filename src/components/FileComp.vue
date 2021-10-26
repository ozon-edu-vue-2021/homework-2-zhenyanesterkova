<template>
  <div>
      <img src="../assets/img/fileIcon.svg" alt="Иконка файла">
      <span>
          {{fileName}}
      </span>
  </div>
</template>

<script>
export default {
    name: "FileComp",
    props: {
        fileName:{
            type: String,
            default: ''
        }
    }
}
</script>