<script>

import axios from 'axios';

export default {
    data() {
        return{
            posts: [],
        }
    },
    methods:{
        getPosts(){
            axios.get('http://127.0.0.1:8000/api/posts', {
                params:{

                }
            })
            .then((response) => {
                console.log(response.data.results.data);
                this.posts = response.data.results.data;
            })
            .catch(function (error){
                console.log(error);
            })
        }
    },
    created(){
        this.getPosts();
    }
}

</script>
<template>
    <div class="card"   v-for="post in posts">
        <h2> {{ post.author }}</h2>
        <h3>{{post.title}}</h3>
        <p>{{post.content}}</p>
    </div>
</template>

<style>
@import '../styles/general.scss';

        .card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
            width: 80%;
            margin: auto;
        }


        .card h3 {
            margin: 0;
            padding: 16px 0;
            background-color: #4CAF50;
            color: white;
        }

        .card p {
            padding: 0 16px 16px;
            color: #333;
        }
</style>