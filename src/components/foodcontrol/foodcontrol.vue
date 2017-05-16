<template>
  <div class="food-control">
    <div class="food-decrease" v-show="food.count>0"
         @click="minusFood" transition="move">
      <span class="inner ws-icon-remove_circle_outline"></span>
    </div>
    <div class="food-count" v-show="food.count>0">{{food.count}}</div>
    <div class="food-increase ws-icon-add_circle" @click="addFood"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  import Vue from 'vue';

  export default {
    props: {
      food: {
        type: Object
      }
    },
    methods: {
      addFood(event) {
        if (!event._constructed) {
          return;
        }
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        } else {
          this.food.count++;
        }
      },
      minusFood(event) {
        if (!event._constructed) {
          return;
        }
        if (this.food.count) {
          this.food.count--;
        }
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .food-control
    font-size 0
    .food-decrease
      display inline-block
      padding 6px
      transition all 0.4s linear
      &.move-transition
        opacity 1
        transform translate3D(0, 0, 0)
        .inner
          display inline-block
          color rgb(0, 160, 220)
          font-size 24px
          line-height 24px
          transition all 0.4s linear
          transform rotate(0)
      &.move-enter, &.move-leave
        opacity 0
        transform translate3D(24px, 0, 0)
        .inner
          transform rotate(180deg)
    .food-count
      display inline-block
      vertical-align top
      width 12px
      padding-top 6px
      text-align center
      font-size 10px
      line-height 24px
      color rgb(147, 153, 159)
    .food-increase
      display inline-block
      padding 6px
      color rgb(0, 160, 220)
      font-size 24px
      line-height 24px
</style>
