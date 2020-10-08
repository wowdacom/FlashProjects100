<template>
  <div id="app">
    <Page :isFix="isFix[0]" msg="Page1" />
    <Page :isFix="isFix[1]" msg="Page2" />
    <Page :isFix="isFix[2]" msg="Page3" />
    <Page :isFix="isFix[3]" msg="Page4" />
    <Page :isFix="isFix[4]" msg="Page5" />
    <GoTop></GoTop>
    <!-- memo
    參考資料:
    https://css-tricks.com/how-to-make-an-unobtrusive-scroll-to-top-button/

    可以改善的地方
    改用 requestanimationframe 處理 scroll
    https://developer.mozilla.org/zh-TW/docs/Web/API/Document/scroll_event
    
    改用 IntersectionObserver
    https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API -->

  </div>
</template>

<script>
import Page from "./components/Page.vue";
import GoTop from "./components/GoTop.vue";

export default {
  name: "App",
  components: {
    Page,
    GoTop,
  },
  data() {
    return {
      currentHeight: 0,
      isFix: [false, false, false, false, false],
    };
  },
  mounted() {
    let vm = this;
    document.addEventListener("scroll", vm.handleFixed);
  },
  methods: {
    handleFixed() {
      let rootElement = document.documentElement;
      let pageElement = document.querySelector(`#Page1`);
      let pageElement2 = document.querySelector(`#Page2`);
      let pageElement3 = document.querySelector(`#Page3`);
      let pageElement4 = document.querySelector(`#Page4`);
      let pageElement5 = document.querySelector(`#Page5`);
      if (pageElement.offsetTop - rootElement.scrollTop < 0) {
        this.$set(this.isFix, 0, true);
      } else {
        this.$set(this.isFix, 0, false);
      }
      if (pageElement2.offsetTop - rootElement.scrollTop < 0) {
        this.$set(this.isFix, 1, true);
      } else {
        this.$set(this.isFix, 1, false);
      }
      if (pageElement3.offsetTop - rootElement.scrollTop < 0) {
        this.$set(this.isFix, 2, true);
      } else {
        this.$set(this.isFix, 2, false);
      }
      if (pageElement4.offsetTop - rootElement.scrollTop < 0) {
        this.$set(this.isFix, 3, true);
      } else {
        this.$set(this.isFix, 3, false);
      }
      if (pageElement5.offsetTop - rootElement.scrollTop < 0) {
        this.$set(this.isFix, 4, true);
      } else {
        this.$set(this.isFix, 4, false);
      }
    },
  },
};
</script>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100vh;
  padding-bottom: 100vh;
  background-image: linear-gradient(
    #d16ba5,
    #e17497,
    #eb828b,
    #ee9183,
    #eda280,
    #f1ad7d,
    #f3b97b,
    #f3c67b,
    #f8d273,
    #fbdf6b,
    #f9ec64,
    #f4fb5f
  );
  position: relative;
}
</style>
