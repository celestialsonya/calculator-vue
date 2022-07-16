
<template>

  <div class="bth_input">
    <button class="getPostsBtn" @click="fetchPosts">get posts</button>
    <button class="getPostsBtn" @click="addPost">add posts</button>
    <input v-bind:value="title" @input="title = $event.target.value" type="text">
  </div>

  <div class="posts">
    <ul v-for="post in posts">
      <li class="post">

        {{ post.id }} | {{ post.title }}
        <div class="buttons">
          <button @click="() => deletePost(post.id)">delete</button>
          <button>mark</button>
        </div>

      </li>
    </ul>
  </div>

</template>

<script>
  export default {
    data(){
      return {
        posts: [],
        title: ""
      }
    },
    methods: {
      fetchPosts(){
        if (this.posts.length){
          return this.posts
        }
        fetch("https://jsonplaceholder.typicode.com/posts")
            .then(res => res.json())
            .then(post => this.posts = post)
      },
      deletePost(id){
        this.posts = this.posts.filter(post => post.id !== id)
      },
      addPost(){
        this.fetchPosts()
        const newPost = {
          id: this.posts.length + 1,
          title: this.title
        }
        this.posts.push(newPost)
        return posts
      }
    }
  }
</script>

<style>

  .getPostsBtn{
    padding: 0.6rem 0.7rem 0.6rem 0.7rem;
    margin-right: 0.5rem;
    border: none;
    background-color: rgba(215, 187, 245, 0.75);
  }

  button{
    padding: 0.5rem 0.5rem 0.5rem 0.5rem;
    margin-left: 0.5rem;
    border: none;
    background-color: rgb(255, 219, 219);
  }

  input{
    width: 15rem;
    height: 1.2rem;
    outline: none;
    border: none;
    padding: 0.5rem 0.5rem 0.5rem 0.5rem;
    background-color: rgba(203, 218, 248, 0.75);
  }

  .post{
    display: flex;
    width: fit-content;
    justify-content: center;
    align-items: center;
  }

</style>