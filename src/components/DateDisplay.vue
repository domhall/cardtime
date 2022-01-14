<template>
  <p>{{ getDateAsCards() }}</p>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class DateDisplay extends Vue {
  daysPassed(current: Date): number {
    const previous = new Date(current.getFullYear(), 0, 1);
    return Math.ceil(
      (current.getTime() - previous.getTime()) / (1000 * 60 * 60 * 24)
    );
  }

  getDateAsCards(): string {
    const currentDate = new Date();
    const daysInYear = this.daysPassed(currentDate) - 1;
    console.log("=========DOM-Debug-days=========: ", daysInYear);
    if (daysInYear === 365) {
      return "Black Joker";
    }
    if (daysInYear === 366) {
      return "White Joker";
    }
    const month = Math.floor(daysInYear / (364 / 13));
    const day = daysInYear % 7;
    const week = Math.ceil((daysInYear % (364 / 13)) / 7);
    console.log("=========DOM-Debug-day=========: ", day);
    console.log("=========DOM-Debug-week=========: ", week);
    console.log("=========DOM-Debug-month=========: ", month);
    const weekMap = ["Spades", "Clubs", "Hearts", "Diamonds"];
    const dayMap = [
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
      "Sunday",
    ];
    const monthMap = [
      "Ace",
      "Two",
      "Three",
      "Four",
      "Five",
      "Six",
      "Seven",
      "Eight",
      "Nine",
      "Ten",
      "Jack",
      "Queen",
      "King",
    ];
    return `${dayMap[day]}, the ${monthMap[month]} of ${
      weekMap[week]
    } ${currentDate.getFullYear()}`;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
