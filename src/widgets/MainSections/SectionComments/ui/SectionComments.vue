<script lang="ts">
import Vue from "vue";
import Swiper from "swiper";
import { Navigation, Autoplay } from "swiper/modules";
import { BaseContainer, BaseRating } from "@/shared/ui";
import Background from "../images/Background.png";
import { isMobile } from "@/shared/lib";

interface IComment {
  text: string;
  name: string;
  status: string;
}

export default Vue.extend({
  components: {
    BaseContainer,
    BaseRating,
  },
  data() {
    return {
      isMobile,
      Background,
      COMMENTS: [
        {
          text:
            "“Solle Royal is a wonderful product. It has help stabilize my mood. I used to have so much anxiety, but this product has helped me lessen that so much. I love the variety of the ingredients and the taste is wonderful. I love that is plant based and does not contain lactose. I highly recommend this product.”",
          name: "Nancy A.",
          status: "Verified Customer",
        },
        {
          text:
            "“This product is absolutely my favorite, MY lines around the eyes diminished, over all skin is firmer and looking in the mirror I look younger.”",
          name: "Dasha C.",
          status: "Verified Customer",
        },
        {
          text:
            "“My hair was thinning and I was in a panic. Angela suggested this product Solle Royal and it’s been thicker ever since! Just love the taste as well”",
          name: "Ruthanne A.",
          status: "Verified Customer",
        },
        {
          text:
            "“My hair, nails, and skin have all improved since I have started this product.”",
          name: "Judy W.",
          status: "Verified Customer",
        },
        {
          text:
            "“It has helped me to restore my gut as well as with stabilizing & strengthening my tendons on my legs. It surely also benefits my stomach lining , and keeping a good pH balance.”",
          name: "Christian G.",
          status: "Verified Customer",
        },
      ] as IComment[],
      swiperOptions: {
        modules: [Navigation, Autoplay],
        loop: true,
        speed: 1000,
        slidesPerView: 1,
        spaceBetween: 24,
        autoplay: {
          delay: 10000,
          disableOnInteraction: true,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        breakpoints: {
          767: {
            slidesPerView: 3,
            spaceBetween: 24,
          },
          991: {
            slidesPerView: 3,
            spaceBetween: 30,
          },
        },
      },
    };
  },
  mounted() {
    new Swiper(this.$refs.swiper, this.swiperOptions);
  },
});
</script>

<template>
  <section class="comments">
    <div class="comments__wrapper">
      <BaseContainer>
        <v-row no-gutters class="comments__header">
          <v-col>
            <h3>What people are saying about Solle<b>Royal</b></h3>
          </v-col>
        </v-row>
        <div class="comments__content">
          <div class="comments__swiper swiper" ref="swiper">
            <div class="swiper-wrapper">
              <div class="swiper-slide" v-for="(comment, index) in COMMENTS" :key="index">
                <div class="comment" outlined>
                  <p class="comment__text">{{ comment.text }}</p>
                  <div class="comment__block">
                    <p class="comment__name">{{ comment.name }}</p>
                    <div class="comment__status">{{ comment.status }}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <button class="swiper-button-prev">
            <svg
              width="31"
              height="52"
              viewBox="0 0 31 52"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M27.4688 48.9766L4.23695 26.2299L26.9836 2.99825"
                stroke="currentColor"
                stroke-width="6"
                stroke-linecap="round"
              />
            </svg>
          </button>
          <button class="swiper-button-next">
            <svg
              width="31"
              height="52"
              viewBox="0 0 31 52"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M27.4688 48.9766L4.23695 26.2299L26.9836 2.99825"
                stroke="currentColor"
                stroke-width="6"
                stroke-linecap="round"
              />
            </svg>
          </button>
        </div>
      </BaseContainer>
      <div class="comments__bg">
        <img :src="Background" alt="background" />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.comments {
  position: relative;
  overflow: hidden;

  &__wrapper {
    background-color: $pink;
    position: relative;
    padding: toRem(124) 0;
    overflow: hidden;

    @media (max-width: $mobile) {
      padding: toRem(45) 0;
    }
  }

  &__header {
    position: relative;
    text-align: center;
    z-index: $zIndex_1;

    @media (max-width: $mobile) {
      max-width: toRem(472);
      margin: 0 auto;
    }
  }

  &__content {
    position: relative;
    margin-top: toRem(80);

    @media (max-width: $tablet) {
      margin-top: toRem(30);
    }
  }

  &__swiper {
    padding: toRem(8) 0;
    @media (max-width: em($maxWidthContainer)) {
      margin: 0 $paddingContainerMinus;
      padding: toRem(4) $paddingContainer;
    }
  }

  &__bg {
    position: absolute;
    right: 0;
    bottom: -10%;

    @media (max-width: $mobile) {
      right: auto;
      left: 0;
      bottom: 0;

      & img {
        transform: scale(-1, 1);
        width: toRem(164);
        max-height: toRem(383);
        object-fit: contain;
        object-position: right;
      }
    }

    @media (max-width: $mobileSmall) {
      & img {
        max-height: toRem(333);
      }
    }
  }
}
.comment {
  border: none;
  position: relative;
  @include flexColumn(center, center);
  text-align: center;
  row-gap: toRem(15);
  background-color: $white;
  border-radius: toRem(30) toRem(30) toRem(30) 0;
  box-shadow: 2px 4px 4px 0px #bcbab180;
  height: toRem(303);
  overflow-y: auto;
  padding: toRem(24) toRem(48);
  @include adaptiveValue("height", 350, 530, 1350, 991, 1);

  @media (max-width:$tablet){
    @include adaptiveValue("height", 400, 530, 991, 767, 1);
  }

  @media (max-width: $tablet) {
    padding: toRem(24) toRem(14);
  }

  @media (max-width: $mobile) {
    height: toRem(220);
    max-width: toRem(400);
    margin: 0 auto;
  }

  &__text {
    font-size: toRem(18);

    @media (max-width: $tablet) {
      font-size: toRem(16);
    }

    @media (max-width: $mobile) {
      font-size: toRem(12);
      line-height: 150%; /* 18/12 */
    }
  }

  &__name {
    font-weight: 600;
    font-size: toRem(12);
    line-height: 150%; /* 18/12 */

    @media (max-width: $mobile) {
      font-size: toRem(10);
    }
  }

  &__status {
    font-size: toRem(12);
    line-height: 150%; /* 18/12 */

    @media (max-width: $mobile) {
      font-size: toRem(8);
    }
  }
}

.swiper-button-prev,
.swiper-button-next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  display: block;
  color: $white;
  margin: 0 toRem(24);
  z-index: $zIndex_1;
  transition: opacity $transition;

  @media (any-hover: hover) {
    &:hover {
      opacity: 0.8;
    }
  }

  @media (max-width: em($maxWidthContainer)) {
    display: none;
  }
}

.swiper-button-prev {
  right: 100%;
}
.swiper-button-next {
  left: 100%;

  & svg {
    transform: scale(-1, 1);
  }
}
</style>
