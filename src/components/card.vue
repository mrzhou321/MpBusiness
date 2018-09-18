<template>
  <div class="container">
    <p class="title">
      {{title}}
    </p>
    <div class="body">
        <span>
          {{desc}}
        </span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'desc']
}
</script>

<style scoped>
.container{
   padding: 20px;
   background-color: chartreuse;
}
.title {
  padding: 10px;
}
.body{
  display: block;
}
</style>
