<template>
  <div class="tech">
    <h1>Tech Tree</h1>
    <div class="container">
      <div class="card" v-for="(spec, name) in techs" :key="name">
        <img :src="'http://localhost:5000/' + spec['icon']"  v-if="'icon' in spec"/>
        <h2>{{ spec['display-name'] }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      techs: {}
    }
  },
  created () {
    this.getTechTree()
  },
  methods: {
    getTechTree() {
      axios.get('http://localhost:5000/v1/tech')
        .then(result => {
          this.techs = result['data']
        })
    }
  }
}
</script>

<style lang="sass" scoped>
.container
  display: flex
  flex-wrap: wrap
  margin: 0 15%

  .card
    padding: 20px
    margin: 10px
    background-color: #fff
    flex: 0 0 calc(25% - 60px)
    box-shadow: 0 2px 2px rgba(0, 0, 0, 0.12)

    p
      text-align: left
</style>


