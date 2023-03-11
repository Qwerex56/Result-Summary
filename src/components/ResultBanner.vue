<template>
  <div class="result-banner">
    <h1 class="result-banner__heading">Your Result</h1>
    <p class="result-banner__overall-score"> {{ getOverallScore }} <br>
      <span class="result-banner__overall-score--max"> of 100</span></p>
    <h1 class="result-banner__greetings">Great</h1>
    <p class="result-banner__description">
      You scored higher than {{ getRankingPosiiton + '%' }} of the people who taken have these tests
    </p>
  </div>
</template>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Hanken+Grotesk:wght@500;700;800&display=swap');

  $hanken-grotesk: 'Hanken Grotesk', sans-serif;
  $light-lavender: hsl(241, 100%, 89%);

  .result-banner {
    display: flex;
    align-items: center;
    flex-direction: column;
    box-sizing: border-box;

    padding: 1.5rem 2.5rem;
    border-radius: 0 0 2rem 2rem;

    background: linear-gradient(hsl(252, 100%, 67%), hsl(241, 81%, 54%));
    color: $light-lavender;

    font-family: $hanken-grotesk;
    text-align: center;
    
    &__heading {
      margin: 0;
    }
    
    &__overall-score {
      max-width: fit-content;
      max-height: fit-content;

      margin: 1rem;
      padding: 3rem;
      border-radius: 50%;

      background: linear-gradient(hsla(256, 72%, 46%, 1), hsla(241, 72%, 46%, 0));
      color: white;

      font-size: 3rem;
      font-weight: 800;
      line-height: 1.36rem;
      vertical-align: middle;
      
      &--max {
        margin: 0rem;
        color: $light-lavender;
        
        font-size: 1rem;
        font-weight: 500;
      }
    }

    &__greetings {
      margin: 0.5rem;

      color: white;
      
      font-weight: 800;
    }
    
    &__description {
      margin-top: 0.5rem;

      color: $light-lavender;
      
      font-size: 1rem;
      font-weight: 700;
    }
  }

  @media screen and (min-width: 800px) {
    .result-banner {
      border-radius: 2rem;
    }
  }

  @media screen and (min-width: 1440px) {
    .result-banner {
      max-width: 400px;
      width: 100%;
      
      border-radius: 2rem;

      &__overall-score {
       margin: auto; 
      }

      &__greetings {
        margin: 0;
      }
    }
  }
</style>

<script>
  import ResultData from "../data/data.json";

  export default {
    computed: {
      getOverallScore() {
        let totalScore = 0;
        ResultData.forEach( (elem) => {
          totalScore += elem.score;
        })
        return totalScore / ResultData.length;
      },
      getRankingPosiiton() {
        let minimumPosition = this.getOverallScore - 10;
        let randPosition = Math.floor(Math.random() * (100 - minimumPosition)) + 1;
        randPosition = 100 - randPosition;
        return randPosition;
      }
    },
  }
</script>