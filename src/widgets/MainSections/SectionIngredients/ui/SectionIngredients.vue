<script lang="ts">
import { defineComponent } from "vue";
import { BaseContainer, BaseAnimation } from "@/shared/ui";

import Ingredients from "../images/ingredients.png";

export default defineComponent({
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      Ingredients,
    };
  },
});
</script>

<template>
  <section class="ingredients">
    <BaseContainer>
      <div class="ingredients__content">
        <div class="ingredients__header">
          <BaseAnimation :delay="200">
            <h2>Ingredients you can love</h2>
          </BaseAnimation>
        </div>
        <div class="ingredients__info">
          <BaseAnimation :delay="400">
            <p>
              With generic supplements, the nitty gritty details of what collagen is and
              where it comes from tends to be a topic one doesn’t prefer to ponder for too
              long. However, with SolleRoyal, we say ponder away!
            </p>
          </BaseAnimation>
          <BaseAnimation :delay="600">
            <p>
              One of the unique aspects of the SolleRoyal formula is that it is a
              plant-based approach at enhancing collagen production. Instead of providing
              animal-sourced prebuilt collagen peptides, which the body is required to
              break down and recreate, it works by providing the nutritional building
              blocks and co-factors required for the production process, from sources we
              know you’ll love.
            </p>
          </BaseAnimation>
        </div>
        <BaseAnimation :delay="800">
          <div class="ingredients__image">
            <img :src="Ingredients" alt="ingredients" />
          </div>
        </BaseAnimation>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.ingredients {
  &__content {
    @include flexColumn();
    row-gap: toRem(46);
    text-align: center;

    @media (max-width: $mobile) {
      row-gap: toRem(24);
    }
  }

  &__info {
    @include flexColumn();
    row-gap: toRem(24);
    max-width: toRem(1158);
    margin: 0 auto;

    @media (max-width: $mobile) {
      row-gap: toRem(16);
      font-size: toRem(12);
    }
  }

  &__image {
    & img {
      width: 100%;
      aspect-ratio: 1328 / 931;
    }
  }
}
</style>
