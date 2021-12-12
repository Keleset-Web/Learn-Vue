<template>
  <div class="app">
    <h2>Страница с постами</h2>
    <MyButton @click="showDialog" class="right">Создать пост</MyButton>
    <MyDialog
        v-model:show="dialogVisible"
    >
      <post-form
          @create="addPost"
      />
    </MyDialog>
    <post-list
        :posts="posts"
        @remove="removePost"
    />
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import MyDialog from "./components/UI/MyDialog";
import MyButton from "./components/UI/MyButton";

export default {
  components: {
    MyButton,
    MyDialog,
    PostList, PostForm
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'Пост 1', body: 'Описание поста 1'},
        {id: 2, title: 'Пост 2', body: 'Описание поста 2'},
        {id: 3, title: 'Пост 3', body: 'Описание поста 3'},
        {id: 4, title: 'Пост 4', body: 'Описание поста 4'},
      ],
      title: '',
      body: '',
      dialogVisible: false
    }
  },
  methods: {
    addPost(post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    }
  }
}
</script>

<style>
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}


.app {
  padding: 15px;
}
</style>