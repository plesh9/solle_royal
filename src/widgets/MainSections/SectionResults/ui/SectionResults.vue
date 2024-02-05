<script lang="ts">
import Vue from "vue";
import { BaseContainer, BaseAnimation } from "@/shared/ui";
import { isMobile } from "@/shared/lib";

import Hydration from "../images/hydration.png";
import Exercise from "../images/exercise.png";
import Sleep from "../images/sleep.png";
import Alcohol from "../images/alcohol.png";
import Diet from "../images/diet.png";
import Sun from "../images/sun.png";

export default Vue.extend({
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      isMobile,
      cards: [
        {
          title: "Stay hydrated",
          img: Hydration,
        },
        {
          title: "Regular exercise (esp. strength training)",
          img: Exercise,
        },
        {
          title: "Get 7+ hours of sleep",
          img: Sleep,
        },
        {
          title: "Avoid excessive smoking/alcohol",
          img: Alcohol,
        },
        {
          title: "Eat varied, whole foods",
          img: Diet,
        },
        {
          title: "Avoid excessive sun exposure",
          img: Sun,
        },
      ],
    };
  },
});
</script>

<template>
  <section class="results">
    <BaseContainer>
      <div class="results__content">
        <div class="results__header">
          <BaseAnimation :delay="200">
            <h2>Making the most of your results</h2>
          </BaseAnimation>
        </div>
        <div class="results__info">
          <BaseAnimation :delay="400">
            <p>
              While an eventual decrease in collagen production is inevitable, that
              doesn’t mean that nothing you do will make a difference. In fact, it’s quite
              the opposite. Taking Solle<b>Royal</b> regularly is a great place to start!
            </p>
          </BaseAnimation>
          <BaseAnimation :delay="600">
            <p>
              That being said, supplements are not magic; they’re science. And science
              shows that combining therapeutic nutrition WITH healthy lifestyle habits is
              the best way to amplify your results. In addition to taking
              Solle<b>Royal</b>, we recommend integrating as many of the following
              behaviors into your wellness routine.
            </p>
          </BaseAnimation>
        </div>
        <BaseAnimation :delay="800">
          <ul class="results__cards">
            <li class="card" v-for="(card, index) in cards" :key="index">
              <div class="card__image">
                <img :src="card.img" :alt="card.title" />
              </div>
              <p class="card__title">{{ card.title }}</p>
            </li>
          </ul>
        </BaseAnimation>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.results {
  &__content {
    @include flexColumn();
    row-gap: toRem(46);
    padding: toRem(74) toRem(68) toRem(87);
    text-align: center;
    background-color: $parchment_cream;
    border-radius: toRem(20);
    box-shadow: 0 toRem(4) toRem(4) 0 #00000040;

    @media (max-width: $mobile) {
      row-gap: toRem(16);
    }

    @media (max-width: $mobile) {
      padding: toRem(27) toRem(14);
    }
  }

  &__info {
    @include flexColumn();
    row-gap: toRem(46);

    @media (max-width: $mobile) {
      font-size: toRem(10);
      row-gap: toRem(16);
    }
  }

  &__cards {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    column-gap: toRem(8);

    @media (max-width: $tablet) {
      grid-template-columns: repeat(3, 1fr);
      row-gap: toRem(28);
    }
  }
}

.card {
  @include flexColumn(center, center);
  row-gap: toRem(8);

  @media (max-width: $mobile) {
    max-width: toRem(97);
    margin: 0 auto;
  }

  &__image {
    @include flexColumn(flex-end, center);
    min-height: toRem(160);

    & img {
      object-fit: contain;
      object-position: center;
    }

    @media (max-width: $pc) {
      min-height: toRem(115);

      & img {
        max-height: toRem(115);
      }
    }

    @media (max-width: $mobile) {
      min-height: toRem(76);

      & img {
        max-height: toRem(76);
      }
    }
  }

  &__title {
    line-height: 100%;
    max-width: toRem(202);
    margin: 0 auto;

    @media (max-width: $pc) {
      font-size: toRem(14);
    }

    @media (max-width: $mobile) {
      font-size: toRem(8);
    }
  }
}
</style>
