<template>
    <div class="container">
        <app-header></app-header>
        <app-addquotes></app-addquotes>
        <app-quote></app-quote>
    </div>
</template>

<script>
import Header from "./components/Header.vue";
import AddQuotes from "./components/AddQuotes.vue";
import Quote from "./components/Quote.vue";

export default {
  components: {
    "app-header": Header,
    "app-addquotes": AddQuotes,
    "app-quote": Quote
  }
};
</script>

<style>

</style>
