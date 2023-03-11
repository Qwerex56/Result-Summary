<template>
  <div class="summary-banner">
    <h1 class="summary-banner__heading">Summary</h1>
    <ResultTag v-for="(resultData, index) in resultData" 
    :key="index"
    :bgColor="resultData.bgColor"
    :iconSrc="resultData.icon"
    >
      <template #category>
        {{ resultData.category }}
      </template>
      <template #score>
        {{ resultData.score }}
      </template>
    </ResultTag>
    <button class="summary-banner__continue">Continue</button>
  </div>
</template>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Hanken+Grotesk:wght@500;700;800&display=swap');

  $hanken-grotesk: 'Hanken Grotesk', sans-serif;

  $dark-gray-blue: hsl(224, 30%, 27%);
  $light-lavender: hsl(221, 100%, 96%);

  .summary-banner {
    display: flex;
    flex-direction: column;
    box-sizing: border-box;

    padding: 2rem;
    
    font-family: $hanken-grotesk;
    font-size: 1rem;

    &__heading {
      margin-bottom: 1rem;

      color: $dark-gray-blue;

      font-size: 1rem;
      font-weight: 700;
    }

    &__continue {
      height: 3.25rem;
      width: 100%;

      border: none;
      border-radius: 100rem;

      background-color: $dark-gray-blue;
      color: $light-lavender;

      font-size: 1rem;
      font-weight: 800;
    }
    &__continue:hover {
      background: linear-gradient(hsl(252, 100%, 67%), hsl(241, 81%, 54%));
    }
  }

  @media screen and (min-width: 1440px) {
    .summary-banner {
      max-width: 500px;
      width: 100%;
    }
  }
</style>

<script>
  import ResultTag from './ResultTag.vue';
  import ResultData from '../data/data.json';

  export default {
    components: {
      ResultTag,
    },
    data() {
      return {
        resultData: ResultData,
      };
    },
  }
</script>