<template>
  <div class="link" tabindex="1" ref="file">
      <img width="35px" src="../assets/img/linkIcon.svg" alt="Иконка папки">
      <a v-bind:href="target">
          {{name}}
      </a>
  </div>
</template>

<script>
export default {
    name: "LinkComp",
    props: {
        name:{
            type: String,
            default: ''
        },
        target:{
            type: String,
            default: '#'
        }
    },
    methods: {
        focus (){
            this.$refs.file.focus();
        }
    },
}
</script>

<style scoped>
    .link{
        width: fit-content;
        padding: 5px;
        cursor: pointer;
    }
    .link:focus-within {
        background-color: rgb(153, 204, 255, 0.5);
        outline: none;
    }     
</style>