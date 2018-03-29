<template>
  <div>
    <h1> User page </h1>
    {{$route.params.id}}
    <ul>
        <li v-for="post in posts" :key="post.id">
            {{post.title}}
        </li>
    </ul>
  </div>
</template>

<script>
    import axios from "axios";
    export default {
        data() {
            return{
                posts: []
            }
        },
        created() {
            console.log("created");
            axios.get( "https://jsonplaceholder.typicode.com/posts", {
                params: {
                    userId: this.$route.params.id
                }
            }).then( (response) => {
                this.posts = response.data;
            })
        },
        mounted() {
            console.log("mounted");
        },
        distroyed() {
            console.log("distroyed");
        }
  }
</script>