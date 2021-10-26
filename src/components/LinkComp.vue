<template>
  <div>
      <img src="../assets/img/linkIcon.svg" alt="Иконка папки">
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