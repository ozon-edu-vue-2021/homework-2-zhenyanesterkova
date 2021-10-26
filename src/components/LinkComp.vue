<template>
  <div class="link" tabindex="1">
      <img width="35px" src="../assets/img/linkIcon.svg" alt="Иконка папки">
      <a v-bind:href="target">
          {{linkName}}
      </a>
  </div>
</template>

<script>
export default {
    name: "LinkComp",
    props: {
        linkName:{
            type: String,
            default: ''
        },
        target:{
            type: String,
            default: '#'
        }
    }
}
</script>

<style scoped>
    .link{
        width: fit-content;
        padding: 5px;
    }
    .link:focus-within {
        background-color: rgb(153, 204, 255, 0.5);
    }     
</style>