<template>
  <div @click="select" :class="{selected} " class="link">
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
        background-color: rgb(153, 204, 255, 0.5);
    }
    .link{
        width: fit-content;
        padding: 5px;
    }
        
</style>