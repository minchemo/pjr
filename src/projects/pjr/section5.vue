<template>
  <div class="section5" >
    <div class="intro hasdivider" data-aos="fade-up">
      <h2>擁有高度的中山北路<br />收藏無價的風景之作</h2>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import "@/assets/style/function.scss";
/* 螢幕尺寸標準 */
.section5 {
  height: 100vh;
  background-image: url("../pjr/s5/bg.jpg");
  background-size: cover;
  overflow: hidden;
  position: relative;
  .intro {
    position: absolute;
    left: size(180);
    top: size(180);
    h2 {
      color: #267f98;
      font-size: size(60);
      font-weight: 600;
      line-height: 1.4;
      letter-spacing: size(2);
      font-family: "Noto Serif TC", Noto Sans TC, serif;
    }
    &::after {
      content: "";
      position: absolute;
      width: size(1000);
      height: 1px;
      background-color: #009be4;
      right: 0;
      bottom: -#{size(30)};
    }
  }
}
/* 平板尺寸 */
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) {
}

/* 手機尺寸 */
@media only screen and (max-width: 767px) {
  .section5 {
    height: size-m(667);
    background-image: url("../pjr/s5/bg-mo.jpg");
    background-size: cover;

    .intro {
      top: size-m(70);
      position: absolute;
      left: 0;
      width: 100%;
      text-align: center;
      h2 {
        color: #267f98;
        font-size: size-m(25);
        font-weight: 600;
        line-height: 1.4;
        letter-spacing: size-m(2);
        font-family: "Noto Serif TC", Noto Sans TC, serif;
      }
      &::after {
        content: unset;
      }
    }
  }
}

// 避免內容電腦過渡平板時，設計未考量的調整
@media only screen and (min-width: 1025px) and (max-width: 1199.98px) {
}

// 避免過度到 1280 x 720 時，設計未考量的調整
@media only screen and (min-width: 1025px) and (max-width: 1280px) {
}
</style>

<script>
// @ is an alias to /src
import { isMobile } from "@/utils";

export default {
  name: "section5",
  data() {
    return {
      isMobile,
    };
  },
};
</script>
