<template>
  <div class="container mx-auto ">
        <img class="bg fixed top-0 left-0 w-full h-full" src="../assets/bg.jpg" alt="" style="z-index: -1;">
        <h1 class="title">
            NUMBERS<span>API</span>
        </h1>
        <p class="text text-white">
            An API for interesting facts about numbers
        </p>
        <p class="text-sm text-white">(If you want to get information about the day, fill in the input as follows (m / d))</p>
        <div class="rounded-lg w-1/2">
            <div class="card px-2 rounded-tl-lg rounded-tr-lg bg-blue-800 flex items-center">
                <h3 class="card-title p-2 text-blue-200">
                    numbersapi.com/
                </h3>
                <input class="input text-blue-200 rounded-tr-lg w-full -ml-2 border-blue-600 focus:border-blue-200 bg-blue-600 hover:bg-blue-700 focus:bg-blue-700" type="text" v-model="query" @keypress.enter="search">
            </div>
            <p class="card__text border-blue-800 border-4 bg-blue-400 py-8 px-4 text-sticky rounded-bl-lg rounded-br-lg text-white">
                {{ results }}
            </p>
            <p class="text-white text-right">If read another information click ENTER↩ again!</p>
        </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
    data(){
        return{
            url_base: 'http://numbersapi.com/',
            results: 'Please Enter number ↑',
            query: '',
            show: false
        }
    },
    methods: {
        search(){
            axios
            .get(`${this.url_base}${this.query}`)
            .then((response) => {
            this.results = response.data;
            })
            .catch((e) => {
            console.log(e);
            });
        }
    }
}
</script>

<style>
    .title{
        text-shadow: #cce4f4 0px 0px 10px, #cce4f4 0 0 60px;
        color: #02273f;
        text-transform: uppercase;
        font-family: "Lucida Grande", "Lucida Sans", "Helvetica", sans-serif;
        font-weight: bold;
        font-size: 5em;
    }
    .title span{
        text-shadow: #02273f 0px 0px 10px;
        color: #cce4f4;
        font-family: inherit;
        font-weight: normal;
        font-size: inherit;
    }
    .text{
        text-shadow: #02273f 0px 0px 5px;
        margin: 0px;
        font-size: 1.6em;
        font-style: italic;
    }
    .input{
        outline: none;
        border-left: 0;
    }
</style>