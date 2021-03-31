<template>
  <div class="rating">
    <div class="star-wrapper">
      <table>
        <tr>
          <th class="overline grey--text text--darken-1"><button  @click="onClickStar(1)" class="mib-f">
       WRONG
     </button></th>
          <th class="overline grey--text text--darken-1"><button  @click="onClickStar(2)" class="mib-r">
       RIGHT
       
     </button></th>
        </tr>
      </table>
     
     
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import Learn from "./Learn.vue";

const RatingProps = Vue.extend({
  props: {
    numberOfStars: Number
  }
});

@Component
export default class Rating extends RatingProps {
  numberOfSelectedStar = 0;
  onClickStar(n: number) {
    this.numberOfSelectedStar = n;
    this.$emit("rated", n);
    
  }
  setRating(n: number) {
    this.numberOfSelectedStar = n;
    this.$emit("rated", n, true);
  }
}
</script>

<style scoped>
.rating {
  padding: 0 16px;
  display: flex;
  justify-content: center;
}

.star-wrapper {
  display: flex;
  flex-flow: column;
  flex: 1 1 0;
  max-width: 20vw;
  max-height: 16vh;
}

.invisible {
  visibility: hidden;
}

svg.star {
  stroke-width: 5;
  stroke-linejoin: round;
}
svg.star polygon {
  cursor: pointer;
}
svg.star.filled polygon {
  fill: #fc0;
  stroke: #fc0;
  transition: 0.2s;
}
svg.star polygon {
  fill: #222;
  stroke: #fc0;
  transition: 0.5s;
}

.svg-f {
  fill: #222;
  stroke: rgb(255, 0, 0);
  transition: 0.5s;
}

.svg-r {
  fill: #222;
  stroke: rgb(0, 255, 0);
  transition: 0.5s;
}

.mib-r{
  font-size: 20px;
  color: rgb(124, 253, 142);
}

.mib-f{
  font-size: 20px;
  color: rgb(255, 115, 115);
}
</style>
