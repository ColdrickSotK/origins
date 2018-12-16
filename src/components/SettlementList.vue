<template>
  <div>
    <h1>Your Settlements</h1>
    <div class="container">
      <Settlement
        v-for="settlement in settlements"
        :key="settlement.id"
        :settlement="settlement" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Settlement from "@/components/Settlement.vue"

export default {
  name: "SettlementList",
  components: {
    Settlement
  },
  data: function() {
    return {
      settlements: []
    }
  },
  created () {
    this.getSettlements()
  },
  methods: {
    getSettlements() {
      axios.get('http://localhost:5000/v1/settlement')
        .then(result => {
          this.settlements = result['data']
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
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
    border-radius: 5px

    p
      text-align: left
</style>
