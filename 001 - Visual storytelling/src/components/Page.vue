<template>
  <div class="hello">
    <div class="colletion-box-wrapper" :id="msg">
      <div class="colletion-box" :class="{ 'active': isFix }" :style="{ transform: isFix ? `rotate(${getRandomInt(-90, 90)}deg)` : 'rotate(0)' }" >
        <h1>{{ msg }}</h1>
      </div>
    </div> 
    
  </div>
</template>

<script>
export default {
  name: 'Page',
  props: {
    msg: String,
    isFix: Boolean
  },
  methods: {
    getRandomInt(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min) + min); //The maximum is exclusive and the minimum is inclusive
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.hello {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  .colletion-box-wrapper {
    width: 100px;
    height: 100px;
    border: solid 1px orange;
    .colletion-box {
      width: calc(100px - 2px);
      line-height: 100px;
      transition: all 1s;
      h1 {
        margin: 0;
      }
      &.active {
        position: fixed;
        top: 0;
        transform-origin: center;
        transition: all .5s;
      }
    }
    
    
  }
}
</style>
