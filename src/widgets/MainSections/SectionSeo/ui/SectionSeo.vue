<script lang="ts">
import { BaseContainer } from "@/shared/ui";
import { isMobile, isTablet } from "@/shared/lib";

import Avatar from "../images/avatar.png";
import Border from "../images/border.png";
import MobileBorder from "../images/border-mobile.png";
import Dots from "../images/dots.png";
import Product from "../images/product.png";

export default {
  components: {
    BaseContainer,
  },
  data() {
    return {
      Avatar,
      Border,
      MobileBorder,
      Dots,
      Product,
      isTablet,
      isMobile,
    };
  },
};
</script>

<template>
  <section class="seo">
    <BaseContainer>
      <div class="seo__wrap">
        <img class="seo__border" :src="Border" alt="Border" v-if="!isTablet" />
        <img class="seo__border" :src="MobileBorder" alt="Border" v-if="isTablet" />
        <div class="seo__dots">
          <img :src="Dots" alt="Dots" />
        </div>
        <div class="seo__product">
          <img :src="Product" alt="Product" />
        </div>
        <div class="seo__content">
          <p class="seo__text">
            When you consider all the amazing variation in collagen produced by our bodies
            for things such as our sight, our posture, our skin and our joint comfort, a
            collagen product derived from a particular animal part just isn’t nearly
            complete enough to meet our needs. Solle<b>Royal</b> is a pure, plant-based
            blend, in royal proportions and selection, that therapeutically meets the
            nutritional needs our body has in order to do what it does best: build,
            rebuild and maintain the best and most beautiful version of ourselves!
          </p>
          <div class="seo__info">
            <img :src="Avatar" alt="Greg Halliday" />
            <p><strong>Greg Halliday</strong> Founder/CEO</p>
          </div>
        </div>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.seo {
  position: relative;
  @include adaptiveValue("padding-bottom", 380, 120, 1300, 767, 1);
  overflow: hidden;

  &__wrap {
    position: relative;
    max-width: toRem(1072);
    width: 100%;
    text-align: center;
    margin: 0 auto;

    @include adaptiveValue("height", 705, 574, 1300, 991, 1);

    @media (max-width: $mobile) {
      max-width: toRem(356);
      height: toRem(601);
    }
  }

  &__product {
    position: absolute;
    left: 0;
    bottom: 0;
    transform: translate(-25%, 60%);

    & img {
      @include adaptiveValue("width", 1053, 600, 1300, 991, 1);
    }

    @media (max-width: $mobile) {
      transform: translate(-25%, 50%);

      & img {
        width: toRem(377);
      }
    }

    @media (max-width: em(500)) {
      transform: translate(-7%, 50%);
    }
  }

  &__content {
    position: relative;
    @include flexColumn(center, center);
    row-gap: toRem(40);
    height: 100%;
    padding: toRem(107);
    z-index: $zIndex_1;
    margin: 0 auto;

    @media (max-width: $pc) {
      row-gap: toRem(24);
    }

    @media (max-width: $tablet) {
      padding: toRem(60);
    }

    @media (max-width: $mobile) {
      row-gap: toRem(18);
      padding: toRem(48) toRem(28);
      justify-content: flex-start;
    }
  }

  &__border {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;

    @media (min-width: $tablet) {
      object-fit: contain;
    }
  }

  &__dots {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: $white;
    width: toRem(276);

    @media (max-width: $mobile) {
      width: toRem(123);

      & img {
        width: toRem(63);
      }
    }
  }

  &__text {
    font-size: toRem(22);
    line-height: 150%; /* 33/22 */

    @media (max-width: $pc) {
      font-size: toRem(20);
    }

    @media (max-width: $mobile) {
      font-size: toRem(14);
    }
  }

  &__info {
    & p {
      & strong {
        display: block;
        font-size: toRem(20);
      }
    }

    @media (max-width: $pc) {
      & img {
        width: toRem(142);
      }
    }

    @media (max-width: $mobile) {
      & img {
        width: toRem(92);
      }

      & p {
        font-size: toRem(10);

        & strong {
          font-size: toRem(12);
        }
      }
    }
  }
}
</style>
