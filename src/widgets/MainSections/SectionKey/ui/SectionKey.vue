<script lang="ts">
import { defineComponent } from "vue";
import { BaseContainer, BaseAnimation, DiamondIcon } from "@/shared/ui";
import { isMobile } from "@/shared/lib";

import Wave from "../images/wave.png";
import Bg from "../images/bg.png";
import MobileBg from "../images/bg-mobile.png";

import Skin from "../images/skin.png";
import Taste from "../images/taste.png";
import Mood from "../images/mood.png";
import Hair from "../images/hair.png";
import Protein from "../images/protein.png";
import Catalysts from "../images/catalysts.png";

export default defineComponent({
  components: {
    BaseContainer,
    DiamondIcon,
    BaseAnimation,
  },
  setup() {
    return {
      Wave,
      Bg,
      MobileBg,
      isMobile,
      cards: [
        {
          title: "Radiant skin",
          icon: Skin,
          text:
            "Experience a healthy glow that will have everyone asking you for your secret",
        },
        {
          title: "Regal taste",
          icon: Taste,
          text: "Mixed super fruit flavor that is fit for a king or queen",
        },
        {
          title: "Improved mood",
          icon: Mood,
          text:
            "With mood-lifting herbs like moringa and butterfly pea, you can't help but smile",
        },
        {
          title: "Youthful hair",
          icon: Hair,
          text: "Thicker, fuller, longer hair. Every day is a good hair day!",
        },
        {
          title: "Protein",
          icon: Protein,
          text:
            "Amino acids necessary for collagen production from easily assimilated plant sources",
        },
        {
          title: "Key Catalysts",
          icon: Catalysts,
          text:
            "Nutrients like hyaluronic acid, biotin and vitamins A, C, D & E, to enhance collagen production",
        },
      ],
      list: [
        "skin",
        "bones + ligaments",
        "arteries",
        "hair",
        "tendons",
        "intestinal lining",
        "nails",
        "muscles",
        "eyes",
        "joints",
        "organs",
        "cartilage",
      ],
    };
  },
});
</script>

<template>
  <section class="key">
    <div class="key__image">
      <img :src="Wave" alt="wave" />
    </div>
    <div class="key__wrapper">
      <BaseContainer>
        <div class="key__header">
          <h2>Key benefits</h2>
        </div>
        <div class="key__content">
          <ul class="key__cards">
            <li class="card" v-for="(card, index) in cards" :key="index">
              <BaseAnimation :delay="index * 300">
                <div class="card__content">
                  <div class="card__icon">
                    <img :src="card.icon" :alt="card.title" />
                  </div>
                  <span class="card__title">{{ card.title }}</span>
                  <p class="card__subtitle">{{ card.text }}</p>
                </div>
              </BaseAnimation>
            </li>
          </ul>
          <div class="block">
            <div class="block__content">
              <BaseAnimation :delay="200">
                <h2 class="block__title">Collagen - it’s not just a skin thing</h2>
              </BaseAnimation>
              <div class="block__text">
                <BaseAnimation :delay="400">
                  <p>
                    When it comes to collagen, we often hear messages like, “drink
                    collagen to fix your wrinkly skin; don’t you dare let those wrinkles
                    show!”
                  </p>
                </BaseAnimation>

                <BaseAnimation :delay="600">
                  <p>Okay fine, we’re being a little dramatic, but you get the gist.</p>
                </BaseAnimation>

                <BaseAnimation :delay="800">
                  <p>
                    And while it’s true that
                    <strong>
                      collagen can help you repair and prevent wrinkles, that’s far from
                      all it does.
                    </strong>
                    A holistic perspective of collagen reveals its large and small roles
                    in maintaining the health and strength of all of the following:
                  </p>
                </BaseAnimation>
              </div>
              <div class="block__wrap">
                <BaseAnimation :delay="1000">
                  <ul class="block__list">
                    <li class="block__item" v-for="(item, index) in list" :key="index">
                      <DiamondIcon />
                      <span>{{ item }}</span>
                    </li>
                  </ul>
                </BaseAnimation>
              </div>
            </div>
          </div>
        </div>
      </BaseContainer>
      <div class="key__bg">
        <img :src="Bg" alt="background" v-if="!isMobile" />
        <img :src="MobileBg" alt="background" v-if="isMobile" />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.key {
  position: relative;
  overflow: hidden;

  &__image {
    & img {
      width: 100%;
      aspect-ratio: 1532 / 84;
      object-fit: cover;
      object-position: top center;
    }
  }

  &__wrapper {
    position: relative;
    padding-top: toRem(44);
    background-color: $parchment_cream;
  }

  &__bg {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 100%;

    & img {
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 100%;
      max-height: toRem(502);
      object-fit: cover;
      object-position: center;

      @media (max-width: $pc) {
      }

      @media (max-width: $mobile) {
        // max-height: toRem(584);
      }

      @media (max-width: $mobileSmall) {
        max-height: toRem(584);
      }
    }
  }

  &__header {
    text-align: center;
  }

  &__content {
    position: relative;
    z-index: $zIndex_1;
    margin-top: toRem(65);

    @media (max-width: $mobile) {
      margin-top: toRem(32);
    }
  }

  &__cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    row-gap: toRem(60);
    column-gap: toRem(24);

    @media (max-width: $mobile) {
      gap: toRem(24);
    }

    @media (max-width: $mobileSmall) {
      grid-template-columns: repeat(2, 1fr);
    }
  }
}
.card {
  &__content {
    max-width: toRem(322);
    text-align: center;
    margin: 0 auto;
  }

  &__icon {
    @include flexColumn(center, flex-end);
    min-height: toRem(135);

    @media (max-width: $mobile) {
      min-height: toRem(54);

      & img {
        max-width: toRem(75);
        max-height: toRem(54);
      }
    }
  }

  &__title {
    display: block;
    font-size: toRem(20);
    font-weight: 500;
    margin-top: toRem(16);

    @media (max-width: $mobile) {
      font-size: toRem(12);
      margin-top: toRem(10);
    }
  }

  &__subtitle {
    font-size: toRem(14);
    margin-top: toRem(10);
    line-height: 100%;

    @media (max-width: $mobile) {
      font-size: toRem(8);
      max-width: toRem(137);
      margin: toRem(5) auto 0;
    }
  }
}

.block {
  padding: toRem(128) 0 toRem(137);

  @media (max-width: $mobile) {
    padding: toRem(44) 0 toRem(65);
  }

  &__content {
    margin: 0 auto;
    max-width: toRem(1111);
    box-shadow: toRem(1) toRem(4) toRem(5.5) 0 #2e293040;
    background-color: $white;
    border-radius: toRem(20);
    padding: toRem(67) toRem(82);

    @media (max-width: $mobile) {
      padding: toRem(26);
      text-align: center;
    }
  }

  &__text {
    margin-top: toRem(32);
    @include flexColumn();
    row-gap: toRem(24);

    @media (max-width: $mobile) {
      margin-top: toRem(24);
      row-gap: toRem(16);
      font-size: toRem(12);
    }
  }

  &__wrap {
    margin-top: toRem(28);

    @media (max-width: $mobile) {
      margin-top: toRem(20);
    }
  }

  &__list {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    row-gap: toRem(12);

    @media (max-width: $mobile) {
      font-size: toRem(12);
      text-align: left;
    }

    @media (max-width: $mobileSmall) {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  &__item {
    @include flexRow(center);
    column-gap: toRem(4);
    font-weight: 300;

    & svg {
      color: $pink;
    }
  }
}
</style>
