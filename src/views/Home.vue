<template>
  <div class="home">
    <SettlementList/>
  </div>
</template>

<script>
import SettlementList from "@/components/SettlementList.vue"

export default {
  name: "home",
  components: {
    SettlementList
  }
}
</script>
