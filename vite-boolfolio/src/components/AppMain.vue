<script>
import axios from 'axios';
import CardPost from './CardPost.vue';

export default {
    name: 'AppMain',
        components: {
            CardPost
    },
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
    <CardPost />
</template>

<style>
@import '../styles/general.scss';
</style>
