<template>
  <div class="background">
    <main>
      <blockquote>
        我明白了，拥有强大力量人的最大的弱点就是力量本身。
        <footer>-
          <cite>
            武藤游戏 &laquo;游戏王&raquo;
          </cite>
        </footer>
      </blockquote>
    </main>
    <div class="path">
      <h1>YGO</h1>
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
    </div>
    <img
      @mousemove="handleMouseMove('cartoon-left', $event)"
      @mouseenter="handleHoverOn"
      @mouseleave="handleHoverOff"
      ref="cartoon-left"
      :class="classObject"
      class="cartoon-left"
      src="//oymcd876b.bkt.clouddn.com/cartoon_left.jpg"
      alt="cartoon_left"/>
    <img
      @mousemove="handleMouseMove('cartoon-right', $event)"
      @mouseenter="handleHoverOn"
      @mouseleave="handleHoverOff"
      ref="cartoon-right"
      class="cartoon-right"
      :class="classObject"
      src="//oymcd876b.bkt.clouddn.com/cartoon_right.jpg"
      alt="cartoon_right"/>
  </div>
</template>

<script>
import './MainScreen.scss';
export default {
  name: 'MainScreen',
  data () {
    return {
      isHover: false,
      isLeft: false,
      isTop: false
    };
  },
  computed: {
    classObject: function () {
      return {
        'cartoon-go-right': this.isLeft && this.isHover,
        'cartoon-go-left': !this.isLeft && this.isHover,
        'cartoon-go-down': this.isTop && this.isHover,
        'cartoon-go-top': !this.isTop && this.isHover
      };
    }
  },
  methods: {
    handleMouseMove: function (ref, e) {
      const {pageX, pageY} = e;
      const element = this.$refs[ref];
      const { left, right, top, bottom } = element.getBoundingClientRect();
      const isLeft = pageX > left && pageX < (right - left) / 2 + left;
      const isTop = pageY > top && pageY < (bottom - top) / 2 + top;
      this.isLeft = isLeft;
      this.isTop = isTop;
    },
    handleHoverOn: function () {
      this.isHover = true;
    },
    handleHoverOff: function () {
      this.isHover = false;
    }
  }
};
</script>