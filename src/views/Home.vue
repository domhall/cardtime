<template>
  <div class="home">
    <h1>What's the date?</h1>
    <DateDisplay />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import DateDisplay from "@/components/DateDisplay.vue"; // @ is an alias to /src

@Component({
  components: {
    DateDisplay,
  },
})
export default class Home extends Vue {}
</script>
