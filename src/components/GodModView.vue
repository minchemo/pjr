<template>
  <div class="GodModView with-mask">
    <div class="view" ref="view">
      <img ref="viewImg" class="view-img" v-lazy :temp="bgUrl" alt="" />
      <img class="view-hand" ref="viewHand" v-lazy :temp="swipeUrl" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "@/assets/style/function.scss";
.GodModView {
  .view {
    height: size(1080);
    width: 100%;
    overflow: hidden;

    .view-hand {
      position: absolute;
      width: size(120);
      z-index: 1;
      right: size(400);
      top: size(150);
      pointer-events: none;
      transform: translateX(0);
      animation: move 2s alternate-reverse infinite ease-in-out;

      @keyframes move {
        from {
          transform: translateX(0);
        }
        to {
          transform: translateX(-50%);
        }
      }
    }
    .view-img {
      height: 100%;
      max-width: unset;
    }
  }
}

@media only screen and (max-width: 767px) {
  .GodModView {
    .view {
      height: size-m(667);
      overflow: hidden;
      .view-hand {
        position: absolute;
        width: 100px;
        z-index: 1;
        top: 25%;
        left: 50%;
        transform: translate(-50%, 0%);
        pointer-events: none;
      }
      .view-img {
        height: 100%;
      }
      //.view-img{height: 100%;}
    }
  }
}
</style>

<script>
import { isMobile } from "@/utils";
import interact from "interactjs";
import BScroll from "@better-scroll/core";

export default {
  name: "GodModView",
  data() {
    return {
      isMobile,
      autoScrollView: true, //是否自動調整鳥瞰圖至建案位置 (手機板)
      autoScrollViewOffset: 150, //自動調整偏移微調
      viewAspectRatioPercentage: isMobile ? "150" : "46.82", // 鳥瞰圖比例 高÷寬×100
      bgUrl: require("@/projects/pjr/s6/bg.jpg"), //置換圖片路徑即可
      swipeUrl: !isMobile
        ? require("@/projects/pjr/s6/hand.png")
        : require("@/projects/pjr/s6/hand-mo.png"), //置換圖片路徑即可
    };
  },
  methods: {
    getScreenHeight() {
      return "220";
      const width = $(window).width();
      const height = $(window).height();
      const ratio = (height / width) * 100;
      return ratio;
    },
    scrollView() {
      const self = this;
      const el = this.$refs.view;
      const imgEl = this.$refs.viewImg;
      const handEl = this.$refs.viewHand;
      const offset = this.autoScrollViewOffset;

      $(imgEl).on("load", () => {
        const scrollTarget = this.autoScrollView
          ? (el.scrollWidth - $(window).width()) / 2 + offset
          : false;

        let bs = new BScroll(this.$refs.view, {
          scrollX: true,
          scrollY: true,
          disableTouch: false,
          bindToWrapper: true,
          eventPassthrough: 'vertical',
          bounce: false,
        });
        bs.scrollTo(bs.maxScrollX / 2, 500);

        setTimeout(() => {
          $(el).one("scroll", () => {
            if (self.isMobile) return;
            $(handEl).fadeOut();
          });
        }, 100);
      });
    },
    setViewBgHeight() {
      const targetHeight = $(".GodModView .view").outerHeight(true);
      if (isMobile) {
        $(".GodModView .view .view-img").height(targetHeight);
      }
    },
    onResize() {
      $(window).on("resize", (e) => {
        this.setViewBgHeight();
      });
    },
    dragMoveListener(event) {
      $(".view-hand").hide();
      var target = event.target;
      var x = (parseFloat(target.getAttribute("data-x")) || 0) + event.dx;
      var y = (parseFloat(target.getAttribute("data-y")) || 0) + event.dy;
      target.style.transform = "translate(" + x + "px, " + y + "px)";

      target.setAttribute("data-x", x);
      target.setAttribute("data-y", y);
    },
  },
  mounted() {
    //this.getScreenHeight();
    this.setViewBgHeight();
    this.onResize();
    this.scrollView();
  },
};
</script>