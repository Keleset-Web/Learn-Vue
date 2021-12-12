<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'MyButton'
}
</script>

<style scoped>
.btn{
  background: none;
  padding: 10px 15px;
  color: teal;
  border: 1px solid darkgreen;
}
.btn.right{
  align-self: flex-end;
}
.btn.m-top{
  margin-top: 15px;
}
</style>