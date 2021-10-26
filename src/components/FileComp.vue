<template>
  <div @click="select" :class="{selected} " class="file">
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
    },
    data(){
        return{
            selected: false,
        }
    },
    methods: {
        select(){
            this.selected = !this.selected;
        }
    },
}
</script>

<style scoped>
    .selected{
        background-color: rgb(153, 204, 255, 0.5);;
    }
    .file{
        width: fit-content;
        padding: 5px;
    }
        
</style>