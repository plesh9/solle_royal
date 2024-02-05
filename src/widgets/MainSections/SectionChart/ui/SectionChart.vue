<script lang="ts">
import Vue from "vue";
import { BaseContainer, BaseAnimation } from "@/shared/ui";
import { isTablet } from "@/shared/lib";
import Chart from "../images/chart.png";

export default Vue.extend({
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      Chart,
      isTablet,
    };
  },
});
</script>

<template>
  <section class="chart">
    <BaseContainer>
      <div class="chart__content">
        <div class="chart__header">
          <BaseAnimation :delay="200">
            <h2>As we age, production slows</h2>
          </BaseAnimation>
        </div>
        <BaseAnimation :delay="400">
          <div class="chart__block">
            <div class="chart__image" v-if="!isTablet">
              <img :src="Chart" alt="Chart" />
            </div>
            <div class="chart__info">
              <p>
                Around the age of thirty, collagen production begins to dip. With time,
                production continues to slow, quality lowers, and the collagen break-down
                process accelerates.
              </p>
              <p>
                Women, in particular, experience a significant decrease in production
                following menopause. By the age of 50, it’s estimated that you may have
                lost about 50% of your collagen levels.
              </p>
              <p>Why does this matter? Revisit the previous section!</p>
              <div class="chart__image" v-if="isTablet">
                <img :src="Chart" alt="Chart" />
              </div>
              <a class="chart__link" href="https://www.sollenaturals.com/blog-post/94">
                Learn more
              </a>
            </div>
          </div>
        </BaseAnimation>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.chart {
  &__content {
    @include flexColumn();
    row-gap: toRem(60);

    @media (max-width: $tablet) {
      row-gap: toRem(30);
    }

    @media (max-width: $mobile) {
      row-gap: toRem(18);
    }
  }

  &__header {
    text-align: center;
  }

  &__block {
    display: grid;
    grid-template-columns: 1fr minmax(toRem(524), 1.12fr);
    align-items: center;
    justify-content: space-between;
    gap: toRem(35);

    @media (max-width: $tablet) {
      grid-template-columns: 1fr;
      justify-content: center;
      text-align: center;
    }
  }

  &__image {
    text-align: center;

    & img {
      max-width: toRem(455);
      width: 100%;
      height: auto;
      aspect-ratio: 455 / 274;
      object-fit: contain;
      object-position: center;

      @media (max-width: $mobile) {
        aspect-ratio: 289 / 137;
      }
    }
  }

  &__info {
    @include flexColumn();
    row-gap: toRem(26);

    @media (max-width: $mobile) {
      font-size: toRem(12);
      row-gap: toRem(20);
    }
  }

  &__link {
    @include flexRow(center, center);
    text-align: center;
    color: $pink;
    border: toRem(1) solid $pink;
    border-radius: toRem(4);
    padding: toRem(12.5) toRem(38);
    font-size: toRem(20);
    width: fit-content;
    transition: background-color $transition, color $transition;

    @media (any-hover: hover) {
      &:hover {
        background-color: $pink;
        color: $white;
      }
    }

    @media (max-width: $tablet) {
      margin: 0 auto;
    }

    @media (max-width: $mobile) {
      font-size: toRem(14);
      padding: toRem(9) toRem(29.5);
    }
  }
}
</style>
