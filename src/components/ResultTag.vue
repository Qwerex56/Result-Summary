<template>
  <div class="result-tag" :style="`background-color: ${HSLAColor(0.05)}`">
    <img :src="iconSrc" class="result-tag__icon" alt="">
    <p class="result-tag__category" :style="`color: ${HSLAColor()}`">
      <slot name="category"></slot>
    </p>
    <p class="result-tag__score">
      <slot name="score"></slot>
      <span class="result-tag__score--max"> / 100</span>
    </p>
  </div>
</template>


<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Hanken+Grotesk:wght@500;700;800&display=swap');

  $hanken-grotesk: 'Hanken Grotesk', sans-serif;

  .result-tag {
    display: flex;
    align-items: center;
    box-sizing: border-box;

    margin-bottom: 1rem;
    padding: 1rem 0.5rem;
    border-radius: 0.5rem;

    font-family: $hanken-grotesk;
    font-size: 1rem;
    font-weight: 700;

    &__icon {
      margin: 0;
      width: 1rem;
    }

    &__category {
      margin: 0;
      margin-left: 0.5rem;
    }

    &__score {
      margin: 0;
      margin-left: auto;
      &--max {
        color: hsl(241, 100%, 89%);
      }
    }
  }
</style>


<script>
  export default {
    props: {
      bgColor: {
        type: String,
        default: 'red',
      },
      iconSrc: {
        type: String,
      }
    },
    methods: {
      HSLAColor(alpha = 1) {
        let bgColor = '';
        switch (this.bgColor) {
          case 'red':
            bgColor = `hsla(0, 100%, 67%, ${alpha})`;
            break;
          case 'yellow':
            bgColor = `hsla(39, 100%, 56%, ${alpha})`;
            break;
          case 'green':
            bgColor = `hsla(166, 100%, 37%, ${alpha})`;
            break;
          case 'blue':
            bgColor = `hsla(234, 85%, 45%, ${alpha})`;
            break;
          default:
            bgColor = `hsla(0, 100%, 67%, ${alpha})`;
            break;
        }
        return bgColor;
      }
    }
  }
</script>