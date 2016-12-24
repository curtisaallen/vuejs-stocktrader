<template>
<div class="jumbotron">
        <h1>Trade or View your Portfolio</h1>
        <p>You may Save & Load your Data</p>
        <p>click on 'End Day' to begin a new Day!</p>
        <hr />
        <p><b>Your Funds: {{funds | currency}}</b></p>
</div>
</template>
<script>
  export default {
    computed: {
      funds() {
         return this.$store.getters.funds;
      }
    }
  }
</script>
