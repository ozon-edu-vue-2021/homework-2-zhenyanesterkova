<template>
  <div class="file" tabindex="1">
      <img width="35px" src="../assets/img/fileIcon.svg" alt="Иконка файла">
      <span>
          {{fileName}}
      </span>
  </div>
</template>

<script>
export default {
    fileName: "FileComp",
    props: {
        fileName:{
            type: String,
            default: ''
        }
    }
}
</script>

<style scoped>
    .file{
        width: fit-content;
        padding: 5px;
        cursor: pointer;
    }
    .file:focus-within {
        background-color: rgb(153, 204, 255, 0.5);
    }    
</style>