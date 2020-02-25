<template>
  <div>
    <div class="search">
      <span> number Of joke </span>
      <input type="number" v-model="countJoke"/>
      <input type="button" value="Search" @click="oncrickCount">
    </div>
    <div class="content">
      <showJoke 
        v-if="this.joke"
        :Joke="this.joke"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import showJoke from '../components/showJoke'

export default {
  components:{
    showJoke
  },
  data () {
    return {
      joke : [],
      countJoke: 10
    }
  },
  methods: {
    async getJoke (num) {
      let data = await axios.get('http://api.icndb.com/jokes/random/'+num)
      this.joke = data.data.value
      console.log(this.joke)
    },
    oncrickCount(){
      this.getJoke(this.countJoke)
      window.location.href('joke')
    }
  },
  mounted(){
    this.getJoke(this.countJoke)
  }
}
</script>

<style>
.search{
  text-align: right;
  padding: 50px;
  padding-bottom: 20px;
}
.content{
  padding: 50px;
}
</style>
