<template>
  <div v-if="posts.length > 0">
    <h3>Список новостей</h3>
    <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else>Постов пока нет</h2>

</template>

<script>
import PostItem from "./PostItem";

export default {
  components: {
    PostItem
  },
  props: {
    posts: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>

</style>