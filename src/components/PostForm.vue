<template>
    <form action="" @submit.prevent>
      <h2>Создание поста</h2>
      <MyInput
          v-model="post.title"
          placeholder="Название поста"
       />
      <MyInput
          v-model="post.body"
          placeholder="Описание"
      />
      <MyButton
          class="right m-top"
          @click="createPost"
      >
        Добавить пост
      </MyButton>
    </form>
</template>

<script>
export default {
  data(){
    return{
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods:{
    createPost(){
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }

    },
  }
}
</script>

<style scoped>
form{
  display: flex;
  flex-direction: column;
}


</style>