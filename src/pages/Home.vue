<template>
  <div class="home no-padding-top">
    <CustomNavigation :scrollInstance="locomotive" />
    <div id="locomotive">
      <Section1 class="section" data-scroll />
      <!-- <Section2 class="section" data-scroll  /> -->
      <Section3 class="section" data-scroll />
      <Section4 class="section" data-scroll />
      <!-- <Section5 class="section" data-scroll /> -->
      <Section6 class="section" data-scroll />
      <Section7 class="section" data-scroll />
      <Section8 class="section" data-scroll />
      <Section9 class="section" data-scroll />
      <!-- <Section10 class="section" data-scroll /> -->
      <Section11 class="section" data-scroll />
      <!-- <Section12 class="section" data-scroll /> -->
      <!-- <Section13 class="section" data-scroll /> -->
      <CustomFooter class="section" data-scroll />
    </div>
    <Loading :loading="load" data-scroll />
    <!-- <Navigation /> -->
    <!-- <Indigator :viewIndex="viewIndex" /> -->
    <!-- <full-page ref="fullPage" :options="options" id="fullpage"> -->
    <!-- <vue-lazy-component class="section" id="section1" @init="init">
      <Section1/>
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section2" v-show="false"  >
        <Section2 />
      </vue-lazy-component>
    <vue-lazy-component class="section" id="section3" @init="init">
      <Section3 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section4" @init="init">
      <Section4 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section5" @init="init">
      <Section5 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section6" @init="init">
      <Section6 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section7" @init="init">
      <Section7 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section8" @init="init">
      <Section8 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section9" @init="init">
      <Section9 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section10" @init="init">
      <Section10 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section11" @init="init">
      <Section11 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section12" @init="init">
      <Section12 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section13" @init="init">
      <Section13 />
    </vue-lazy-component>
    
      <vue-lazy-component class="section" id="section2" v-show="false"  >
        <Section2 />
      </vue-lazy-component>

    <vue-lazy-component class="section" id="contact">
      <CustomFooter />
    </vue-lazy-component> -->
    <!-- </full-page> -->

    <!-- <MobileNav /> -->
  </div>
</template>

<script>
// @ is an alias to /src
import $ from "jquery";
import Navigation from "@/layouts/Navigation.vue";
import { isMobile } from "@/utils";
import SideNavigation from "@/layouts/SideNavigation.vue";
import ContactSection from "@/layouts/ContactSection.vue";
import MobileNav from "@/layouts/MobileNav.vue";
import Loading from "@/components/Loading.vue";
import AOS from "@/lib/aos/src/js/aos";

import CustomFooter from "@/layouts/CustomFooter.vue";

// import Indigator from '@/components/Indigator.vue'

import Section1 from "@/projects/pjr/section1.vue";
import Section2 from "@/projects/pjr/section2.vue";
import Section3 from "@/projects/pjr/section3.vue";
import Section4 from "@/projects/pjr/section4.vue";
import Section5 from "@/projects/pjr/section5.vue";
import Section6 from "@/projects/pjr/section6.vue";
import Section7 from "@/projects/pjr/section7.vue";
import Section8 from "@/projects/pjr/section8.vue";
import Section9 from "@/projects/pjr/section9.vue";
import Section10 from "@/projects/pjr/section10.vue";
import Section11 from "@/projects/pjr/section11.vue";
import Section12 from "@/projects/pjr/section12.vue";
import Section13 from "@/projects/pjr/section13.vue";
import LocomotiveScroll from "locomotive-scroll";
import CustomNavigation from "@/layouts/CustomNavigation.vue";

export default {
  name: "home",
  components: {
    Loading,
    // Indigator,
    Navigation,
    //SideNavigation,
    CustomNavigation,
    ContactSection,
    CustomFooter,
    MobileNav,
    Section1,
    Section2,
    Section3,
    Section4,
    Section5,
    Section6,
    Section7,
    Section8,
    Section9,
    Section10,
    Section11,
    Section12,
    Section13,
    locomotive: null,
  },

  data() {
    return {
      isMobile,
      isSide: false,
      load: true,
      // viewIndex: 0,
      // action: {
      //   moveTo: () => {},
      // },

      // indigatorIndex: 0,
      // options: {
      //   menu: "#menu",
      //   anchors: [],
      //   scrollBar: false,
      //   // onLeave: this.onLeave,
      //   //afterLoad: this.afterLoad,
      //   continuousHorizontal: true,
      //   autoScrolling: true,
      //   fitToSection: true,
      //   verticalCentered: false,

      //   navigation: false,
      //   navigationPosition: "left",
      //   slidesNavigation: false,
      //   slidesNavPosition: "top",
      //   lazyLoading: false,
      //   onLeave: function () {
      //     $(".section [data-aos]").each(function () {
      //       $(this).removeClass("aos-animate");
      //     });
      //   },
      //   onSlideLeave: function () {
      //     $(".slide [data-aos]").each(function () {
      //       $(this).removeClass("aos-animate");
      //     });
      //   },
      //   afterSlideLoad: function () {
      //     $(".slide.active [data-aos]").each(function () {
      //       $(this).addClass("aos-animate");
      //     });
      //   },
      //   afterLoad: function () {
      //     $(".section.active [data-aos]").each(function () {
      //       $(this).addClass("aos-animate");
      //     });
      //   },
      // },
    };
  },
  created() {
    // setTimeout(() => {
    //   this.load = false
    // }, 500)
    // window.addEventListener('load', event => {
    // })

    $(document).ready(() => {
      var imagesLoaded = 0;
      var totalImages = $("img").length;

      const allImagesLoaded = () => {
        this.load = false;
      };
      const imageLoaded = () => {
        imagesLoaded++;

        if (imagesLoaded > totalImages * 0.5) {
          allImagesLoaded();
        }
      };
      $("img").each(function (idx, img) {
        $("<img>").on("load", imageLoaded).attr("src", $(img).attr("src"));
      });
    });
  },
  mounted() {
    AOS.init({
      duration: 1000,
    });

    this.locomotive = new LocomotiveScroll({
      el: document.querySelector("#locomotive"),
      smooth: true,
      repeat: true,
      offset: ["45%", "45%"],
      tablet: {
        smooth: false,
        breakpoint: 250,
      },
      smartphone: {
        smooth: false,
      },
      lerp: 0.05,
    });

    this.locomotive.on("scroll", (obj) => {
      $(".is-inview [data-aos]").addClass("aos-animate");
      setTimeout(() => {
        $(".is-inview .divider").removeClass("showin").addClass("showin");
        $(".is-inview .hasdivider").removeClass("showin").addClass("showin");
      }, 2000);
    });

    // let imgs = document.images;

    // [].forEach.call(imgs, function (img) {
    //   if (img.complete) update_();
    //   else img.addEventListener("load", update_, false);
    // });

    const self = this;

    setInterval(() => {
      update_();
    }, 1000);

    function update_() {
      self.locomotive.update();
    }

    this.scrolling();
  },
  methods: {
    init() {
      this.locomotive.update();
    },
    scrolling() {
      let lastScrollTop = 0;
      $(window).on("scroll", function () {
        let st = $(this).scrollTop();
        const el = $(".floating");
        if (st < lastScrollTop) {
          el.removeClass("floating-down").addClass("floating-up");
        } else {
          el.removeClass("floating-up").addClass("floating-down");
        }

        lastScrollTop = st;
      });
    },
  },
};
</script>

<style lang="scss">
@import "../assets/style/variableColor.scss";

.home {
  &::before {
    content: " ";
    position: fixed;
    z-index: -1;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    //background: url("~@/projects/llcs/s1/bg.jpg") center 0 no-repeat;
    background-size: cover;
  }
  &::-webkit-scrollbar {
    display: none;
  }
}

.divider {
  transform: scale(0) !important;
  transition: all 1s !important;
  &.showin {
    transform: scale(1) !important;
  }
}

.hasdivider {
  &:after {
    transform: scale(0) !important;
    transition: all 1s !important;
  }

  &.showin {
    &::after {
      transform: scale(1) !important;
    }
  }
}

.section,
.section .fp-slide,
.section .fp-tableCell {
  will-change: transform, opacity;
}

.fp-left {
  margin-left: 12px;
}
//間隔
#fp-nav ul li,
.fp-slidesNav ul li {
  margin: 24px 0 !important;
}

#fp-nav {
  z-index: 9999 !important;
}

//基礎顏色
#fp-nav ul li a span,
.fp-slidesNav ul li a span {
  width: 14px !important;
  height: 14px !important;
  margin: 0 !important;
  background: #fff !important;
  filter: drop-shadow(0 0 3px rgba(0, 0, 0, 0.2));
}
//Active顏色
#fp-nav ul li a.active span,
#fp-nav ul li:hover a.active span,
.fp-slidesNav ul li a.active span,
.fp-slidesNav ul li:hover a.active span {
  background: #fff000 !important;
}

@media only screen and (max-width: 767px) {
  .home {
    &::before {
      //background-image: url("~@/projects/llcs/s1/bg_mo.jpg");
    }
  }
  .fp-left {
    display: flex;
    margin: 0 !important;
    left: 50% !important;
    top: 0 !important;
    width: 80vw;
    transform: translate(-53%, 20px) !important;
  }

  #fp-nav ul li,
  .fp-slidesNav ul li {
    margin: 0 !important;
  }

  #fp-nav ul {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    left: 0;
    justify-content: space-around;
  }
}
</style>
