<template>
    <div class="quote-container">
        <div v-for="quote in quoteArray" class="quote"  @click="removeQuote(quote)">
            <p>{{quote}}</p>
        </div>
    </div>

</template>
<script>
import { bus } from "../../src/main.js";

export default {
  data: () => {
    return {
      quoteArray: []
    };
  },
  created() {
    bus.$on("addQuote", data => {
      if (data) {
        this.quoteArray.push(data);
      }
    });
  },
  methods: {
    removeQuote(quote) {
      let index = this.quoteArray.indexOf(quote);
      this.quoteArray.splice(index, 1);
      bus.$emit("quoteWasDeleted");
    }
  }
};
</script>
<style scoped>
p {
  font-family: "Arizonia";
  font-size: 36px;
  line-break: 40px;
}
.quote {
  border: 1px solid grey;
  box-shadow: 1px 1px 1px #ccc;
  padding: 5px;
  margin: 5px;
  overflow: auto;
  width: 270px;
  word-wrap: break-word;
  height: fit-content;
  text-align: center;
}
.quote:hover {
  background-color: red;
  opacity: 0.5;
}
.quote-container {
  display: flex;
  flex-wrap: wrap;
}
</style>