<template>
  <div class="dialog" v-if="show" @click="hideDialog">
  <div @click.stop class="dialogContent">
    <slot></slot>
  </div>
  </div>
</template>

<script>
export default {
  name: "MyDialog",
  props: {
    show: {
      type: Boolean,
      default:false
    }
  },
  methods:{
    hideDialog(){
      this.$emit('update:show', false)
    }
  }
}
</script>

<style scoped>
.dialog{
  top:0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0,0,0, 0.5);
  position: fixed;
  display: flex;
}
.dialogContent{
  padding: 15px;
  margin: auto;
  background-color: white;
  border-radius: 8px;
  min-height: 100px;
  min-width: 300px;
}
</style>