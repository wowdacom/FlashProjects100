<template>
  <div>
      <button class="myBtn">{{ currentHeight }}</button>
  </div>
</template>

<script>
export default {
    data () {
        return {
            currentHeight: 0
        }
    },
    mounted () {
        let vm = this
        document.addEventListener("scroll", vm.showScrollHeight)
    },
    methods: {
        showScrollHeight () {
            let rootElement = document.documentElement
            //可以滑的長度等於 總長度 - 第一頻的長度
            let scrollTotal = rootElement.scrollHeight - rootElement.clientHeight
            this.currentHeight = (rootElement.scrollTop / scrollTotal).toFixed(2)
        }
    }
}
</script>

<style>
.myBtn {
    position: fixed;
    bottom: 25px;
    right: 25px;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: none;
    background-color: salmon;
    color: white;
    cursor: pointer;
}
</style>