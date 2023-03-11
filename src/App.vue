<template>
  <div class="summary-component">
    <ResultBanner></ResultBanner>
    <SummaryBanner/>
  </div>
</template>


<style lang="scss">
  body {
    margin: 0;
    align-items: center;
    display: flex;
    flex-direction: column;

    height: 100vh;
  }
  
  .summary-component {
    display: flex;
    flex-direction: column;
  }

  @media screen and (min-width: 800px) {
    body {
      justify-content: center;
    }

    .summary-component {
      flex-direction: column;
    }
  }

  @media screen and (min-width: 1440px) {
    .summary-component {
      flex-direction: row;
    }
  }
</style>

<script>
  import SummaryBanner from "./components/SummaryBanner.vue";
  import ResultBanner from "./components/ResultBanner.vue";

  export default {
    components: {
      SummaryBanner,
      ResultBanner,
    }
  }
</script>
