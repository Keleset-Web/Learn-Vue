<template>
  <div class="post">
    <div><strong>Название:</strong>{{ post.title }}</div>
    <div>Описание: {{ post.body }}</div>
    <div class="post_btns">
      <my-button
          class="right"
          @click="$emit('remove', post)"
      >
        Удалить
      </my-button>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    post: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.post {
  padding: 15px;
  border: 4px darkgreen solid;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>