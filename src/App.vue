<template>
  <h1 class="text-center">Ciao</h1>
  <i class="fa fa-solid fa-home"></i>
  <ul>
    <li  v-for="post in posts" :key="post.id">
       {{ post.title }}
    </li>
  </ul>

  <main>
    <router-view> </router-view>
  </main>
</template>

<script>
import {store} from './store';
import axios from 'axios';
  export default {
    name: 'App',
    data(){
      return{
        store,
        posts:[]
      }
    },
    methods:{
      getAllPosts(){
        axios.get(this.store.ApiBaseUrl+'/posts').then((res) => {
          // console.log(res.data)
          this.posts = res.data.results;

        });
      }
    },
    mounted(){
      this.getAllPosts()
    }
  }
</script>

<style lang="scss" scoped>

</style>