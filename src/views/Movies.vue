<template>
  <div class="movies">
    <div class="movies" id="posters">
        <div v-for="(item, index) in items"  :key="items[index].id" class="poster" id="spiritedaway">
            <a class="posterimage" v-bind:href="item.link " v-bind:key="item.link" target="_blank">
              <img class="posterimage" v-bind:src="require(`@/assets/images/`+ item.image)" alt="Spirited Away (2000) Poster">
              <div class="title">{{ item.title }}</div>
            </a>
        </div>
    </div>
    <div id="posts">
      <div v-for="(post) in posts" :key="post.id" class="post">
        <div class="title">ID: {{ post.id }} - {{ post.title }}</div>
      </div>
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  data() {
    return {
      posts:{},
      items: [
        { 
          title: 'Spirited Away (2000)',
          image: 'spirited-away-poster.jpg',
          link: 'https://letterboxd.com/film/spirited-away/', 
          id:"1"
        },
        { 
          title: 'Paris, Texas (1984)',
          image: 'paris-texas-poster.jpg',
          link: 'https://letterboxd.com/film/paris-texas/', 
          id:"2"
        },
        { 
          title: 'Blue Velvet (1986)',
          image: 'blue-velvet-poster.jpg',
          link: 'https://letterboxd.com/film/blue-velvet/', 
          id:"3"
        },
        { 
          title: 'Black Christmas (1974)',
          image: 'black-christmas-poster.jpg',
          link: 'https://letterboxd.com/film/black-christmas/', 
        id:"4"
       }
      ]
    }
  },
  methods:{
    getPosts() {
      axios.get('https://jsonplaceholder.typicode.com/todos').then((response) => {
      console.log(response.data)
      this.posts = response.data;
      console.log(this.posts);
      })
    }
  },
  mounted () {
    this.getPosts()
  }
}
</script>


<style>
body {
    height: 450px;
    background-color: #14181c;
}

#posters {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    flex-direction:row;
}

.poster {
    flex-shrink: 0;
    align-self: center;
    margin-left: 10px;
    margin-right: 10px;
    margin-top: 65px;
    width: 230px;
    height: 345px;
    transition: 0.5s;
}

.poster:hover {
    transform: translateY(-10px);
    box-shadow: 0px 0px 20px rgb(0, 0, 0);
    text-shadow: 0px 0px 12px #7E90A3;
}

@font-face {
    font-family: Luxurious Roman;
    src: url(../assets/fonts/LuxuriousRoman-Regular.ttf);
}

.title {
    flex-shrink: 0;
    align-self: center;
    margin: 10px;
    font-family: Luxurious Roman;
    color: #8C9CAD;
    text-align: center;
}

.posterimage {
    width: inherit;
    height: inherit;
    text-decoration: none;
}

@media (max-width: 600px) {  

    .poster {
        margin-top: 15px;
        width: 160px;
        height: auto;
    }

}
</style>