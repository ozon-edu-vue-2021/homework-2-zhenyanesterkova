<template>
  <div class="file" tabindex="1" ref="file">
      <img width="35px" src="../assets/img/fileIcon.svg" alt="Иконка файла">
      <span>
          {{name}}
      </span>
  </div>
</template>

<script>
export default {
    name: "FileComp",
    inheritAttrs: false,
    props: {
        name:{
            type: String,
            default: ''
        }
    },
    methods: {
        focus (){
            this.$refs.file.focus()
        }
    },
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
        outline: none;
    }    
</style>