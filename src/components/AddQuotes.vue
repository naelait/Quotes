<template>
    <div>
        <p>Quote</p>
        <textarea cols="70" rows="4" v-model="quote"></textarea>
        <button class="btn btn-primary" v-if="nbr < 10 && quote" @click="addQuote">Add new quote</button>
    </div>
</template>
<script>
import { bus } from "../../src/main.js";
export default {
  data: () => {
    return {
      quote: null,
      nbr: 0
    };
  },
  created() {
    bus.$on("quoteWasDeleted", deleted => {
      this.nbr--;
    });
  },
  methods: {
    addQuote() {
      if (this.nbr >= 10) {
        alert("You cant post more then 10 quotes");
        this.nbr = 10;
      } else {
        this.nbr++;
        bus.$emit("incrementProgress", this.nbr);
        bus.$emit("addQuote", this.quote);
      }
    }
  }
};
</script>
<style scoped>
div {
  width: 50%;
  margin: 0 auto;
}
textarea {
  resize: none;
}
</style>