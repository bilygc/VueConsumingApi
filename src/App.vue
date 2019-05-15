<template>
  <div id="app">
    <h1>Busqueda de imagenes Giphy</h1>
    <SearchForm @searchGiphy="searchGiphy" />
    <div v-for="img in imglist" v-bind:key="img.id">
				<a v-bind:href="img.url" target="_blank">
          <img v-bind:src="img.images.preview_gif.url">
        </a>
			</div>
  </div>
</template>

<script>
import SearchForm from "./components/SearchForm.vue";
// import ImgList from "./components/ImgList.vue"
import Axios from 'axios';

export default {
  name: 'app',
  data () {
    return {
      imglist: []
    }
  },
  components: {
    SearchForm,
    // ImgList
  },
  methods: {
    searchGiphy(obj) {

      const name = obj.name;
      const url = "https://api.giphy.com/v1/gifs/search?api_key=n05UITsRAD9pvn9ldvQOEb9go8LMNGZj&q="+name+"&limit=5&offset=0&rating=G&lang=en";

      Axios.
			get(url).
			then((res) => {
        console.log(res.data);
        this.imglist=res.data.data;
			});

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
