<script lang="ts">
import { BaseContainer, BaseAnimation } from "@/shared/ui";

import Wave from "../images/wave.png";
import BottomWave from "../images/wave-bottom.png";

import Card_1 from "../images/recipe1.png";
import Card_2 from "../images/recipe2.png";
import Card_3 from "../images/recipe3.png";

export default {
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      Wave,
      BottomWave,
      cards: [
        {
          img: Card_1,
          title: "Berry lemon",
          subtitle:
            "A summery favorite for its skin health benefits and refreshing taste.",
          ingredients: [
            "1/2 scoop Solle<b>Royal</b>",
            "1/2 pkt Solle<b>Excell</b>",
            "20 oz. cold water ",
            "Juice of half a lemon",
            "Ice",
          ],
          directions: "Combine all ingredients and stir well.",
        },
        {
          img: Card_2,
          title: "Regal smoothie bowl",
          subtitle:
            "A great way to start your day or a great midday snack that will give you a great energy boost and help balance hormones while helping you feel full.",
          ingredients: [
            "1/2 cup unsweetened almond milk",
            "1 cup frozen cherries",
            "1 tsp cacao",
            "1 scoop Solle<b>Royal</b>",
            "3 opened capsules of Solle<b>Maca XD®</b>",
          ],
          toppings:
            "<b>Optional Toppings:</b> Handful of granola, berries and/or chocolate chips.",
          directions:
            "Blend together then add toppings. To make as a smoothie, add a half cup of water before blending.",
        },
        {
          img: Card_3,
          title: "The berry royal smoothie",
          subtitle:
            "A great frozen treat that is packed with nutrients that you can enjoy anytime.",
          ingredients: [
            "1 scoop SolleRoyal",
            "8 ounces almond milk",
            "1 frozen banana",
            "6 strawberries, frozen",
            "1/2 cup fresh or frozen blueberries",
            "10 almonds",
            "2-4 ice cubes",
            "Cold water to taste",
          ],
          directions:
            "Blend all ingredients until smooth. Use less liquid and more ice for a thicker consistency.",
        },
      ],
    };
  },
};
</script>

<template>
  <section class="video">
    <div class="video__wrap">
      <BaseContainer>
        <div class="video__content">
          <div class="video__header">
            <h3>Mixing up your Solle<b>Royal</b></h3>
            <div>
              <div class="player">
                <vue-plyr>
                  <div
                    data-plyr-provider="youtube"
                    data-plyr-embed-id="IzmCP9Yd6dc"
                  ></div>
                </vue-plyr>
              </div>
              <div class="directions">
                <div class="directions__header">
                  <BaseAnimation :delay="100">
                    <p class="directions__title">General use directions:</p>
                  </BaseAnimation>
                  <div class="directions__subtitle">
                    <BaseAnimation :delay="200">
                      <p>
                        Add one scoop or packet to 8-16 oz of cold water or milk with ice
                        and mix until smooth. Also works great in smoothies (we recommend
                        combining with the Solle<b>Complete®</b> protein).
                      </p>
                    </BaseAnimation>
                    <BaseAnimation :delay="400">
                      <p>
                        To take hot, mix one scoop in 12-14 oz of hot water with one
                        packet of Solle<b>ReNue®</b> before bed.
                      </p>
                    </BaseAnimation>
                  </div>
                </div>
                <div class="directions__list">
                  <div v-for="(card, index) in cards" :key="index" class="card">
                    <div class="card__wrapper">
                      <div class="card__image">
                        <BaseAnimation variant="opacity" :delay="200">
                          <img :src="card.img" :alt="card.title" />
                        </BaseAnimation>
                      </div>
                      <div class="card__content">
                        <BaseAnimation :delay="100">
                          <p class="card__title">{{ card.title }}</p>
                        </BaseAnimation>
                        <BaseAnimation :delay="200">
                          <p class="card__subtitle" v-html="card.subtitle" />
                        </BaseAnimation>
                        <div class="card__block">
                          <BaseAnimation :delay="300"
                            ><strong>Ingredients:</strong></BaseAnimation
                          >
                          <BaseAnimation :delay="400">
                            <ul>
                              <li
                                v-for="(item, index) in card.ingredients"
                                :key="index"
                                v-html="item"
                              />
                            </ul>
                          </BaseAnimation>
                        </div>
                        <div class="card__block" v-if="card.toppings">
                          <BaseAnimation :delay="500">
                            <p v-html="card.toppings" />
                          </BaseAnimation>
                        </div>
                        <div class="card__block">
                          <BaseAnimation :delay="600">
                            <strong>Directions:</strong>
                          </BaseAnimation>
                          <BaseAnimation :delay="700">
                            <p>{{ card.directions }}</p>
                          </BaseAnimation>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </BaseContainer>
      <div class="video__bg">
        <img :src="Wave" alt="wave" />
        <div></div>
      </div>
    </div>
    <div class="video__wave">
      <img :src="BottomWave" alt="wave" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";
.video {
  overflow: hidden;
  &__header {
    text-align: center;
  }

  &__wrap {
    position: relative;

    min-height: 1000px;
  }

  &__content {
    position: relative;
    z-index: $zIndex_1;
  }

  &__bg {
    position: absolute;
    bottom: 0;
    left: 0;
    height: 85%;
    width: 100%;

    & > img {
      width: 100%;
      aspect-ratio: 1518 / 103;
    }

    & > div {
      background-color: #eceade;
      width: 100%;
      height: 100%;
    }

    @media (max-width: $mobileSmall) {
      height: 93%;
    }
  }

  &__wave {
    & img {
      width: 100%;
      aspect-ratio: 1124 / 124;
      object-fit: cover;
      object-position: bottom center;
    }
  }
}

.player {
  position: relative;
  max-width: toRem(1034);
  margin: 0 auto;
  border-radius: toRem(8);
  overflow: hidden;
  margin-top: toRem(80);
  aspect-ratio: 1034 / 539;

  @media (max-width: $mobile) {
    margin-top: toRem(30);
  }

  @media (max-width: $mobileSmall) {
    aspect-ratio: 359 / 187;
  }
}

.directions {
  margin: toRem(25) auto 0;
  max-width: toRem(1007);
  width: 100%;

  &__header {
    @include flexColumn();
    row-gap: toRem(8);
    text-align: left;
    max-width: toRem(887);

    @media (max-width: $mobile) {
      row-gap: toRem(4);
    }
  }

  &__title {
    font-size: toRem(24);
    font-weight: 600;

    @media (max-width: $mobile) {
      font-size: toRem(12);
    }
  }

  &__subtitle {
    @include flexColumn();
    row-gap: toRem(8);

    @media (max-width: $mobile) {
      & p {
        font-size: toRem(10);
        line-height: 150%;
      }
    }
  }

  &__list {
    @include flexColumn();
    row-gap: toRem(124);
    width: 100%;
    margin-top: toRem(80);

    @media (max-width: $tablet) {
      row-gap: toRem(66);
      margin-top: toRem(63);
    }

    @media (max-width: $mobile) {
      row-gap: toRem(36);
      margin-top: toRem(33);
    }
  }
}

.card {
  width: 100%;
  position: relative;
  padding-right: toRem(112);
  display: flex;
  flex-direction: column;
  align-items: flex-end;

  @media (max-width: $pc) {
    padding-right: toRem(80);
  }

  @media (max-width: $mobile) {
    padding-right: toRem(40);
  }

  &__wrapper {
    position: relative;
    border-radius: toRem(20);
    background-color: #f6f5ef;
    padding: toRem(50) toRem(80);
    box-shadow: 0px 3px 4px 2px #bcbab185;
    width: 100%;
    text-align: left;
    max-width: toRem(853);

    @media (max-width: $pc) {
      padding: toRem(38) toRem(32);
    }

    @media (max-width: $mobile) {
      padding: toRem(28) toRem(22);
    }
  }

  &__content {
    position: relative;
    z-index: $zIndex_1;
    @include flexColumn();
    row-gap: toRem(20);

    & p {
      line-height: 150%;
    }

    @media (max-width: $mobile) {
      row-gap: toRem(10);
    }
  }

  &__title {
    font-size: toRem(36);
    max-width: toRem(420);
    line-height: 125%; /* 45/36 */
    font-weight: 600;

    @media (max-width: $mobile) {
      font-size: toRem(16);
      max-width: toRem(200);
    }

    @media (max-width: $mobileSmall) {
      max-width: toRem(154);
    }
  }

  &__subtitle {
    max-width: toRem(420);

    @media (max-width: $mobile) {
      font-size: toRem(10);
      max-width: toRem(200);
    }
    @media (max-width: $mobileSmall) {
      max-width: toRem(154);
    }
  }

  &__block {
    max-width: toRem(476);

    @media (max-width: $mobile) {
      font-size: toRem(10);
    }
  }

  &__image {
    position: absolute;
    right: 0;
    top: 0;
    transform: translate(30%, -20%);
    z-index: $zIndex_1;

    @media (max-width: $pc) {
      & img {
        width: toRem(384);
      }
    }

    @media (max-width: $tablet) {
      & img {
        width: toRem(284);
      }
    }

    @media (max-width: $mobile) {
      & img {
        width: toRem(184);
      }
    }

    @media (max-width: em(365)) {
      & img {
        width: toRem(124);
      }
    }
  }
}
</style>
<style lang="scss">
.plyr__video-embed iframe,
.plyr__poster {
  transform: translateY(-5px);
}
</style>
