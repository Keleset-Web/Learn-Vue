<template>
  <div class="app">
    <h2>Страница с постами</h2>
    <div class="app_btns">
      <MyButton @click="showDialog" class="right">Создать пост</MyButton>
      <MySelect
      v-model="selectedSort"
      :options="sortOptions"
      />
    </div>

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
        v-if="!isPostLoading"
    />
    <div v-else>Идёт загрузка постов....</div>
  </div>
</template>

<script>
import PostForm from "./components/PostForm";
import PostList from "./components/PostList";
import axios from 'axios'

export default {
  components: {
    PostList, PostForm
  },
  data() {
    return {
      posts: [
      ],
      title: '',
      body: '',
      dialogVisible: false,
      isPostLoading: false,
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'По названию'},
        {value: 'body', name: 'По описанию'}
      ]
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
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true;
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
          this.posts = response.data
      }catch (e){
        alert('Ошибка '+ e)
      } finally {
        this.isPostLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPosts()
  },
  watch: {
    selectedSort(newValue){
      console.log(newValue)
      //this.posts.sort((post1,post2) => {
      //  return post1[this.selectedSort]?.localeCompare(post2[this.selectedSort])
      //})
    },
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
.app_btns{
  margin: 15px 0px;
  display: flex;
  justify-content: space-between;
}
</style>