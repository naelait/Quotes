<template>
    <div>
        <h3>Quotes Added</h3>
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100" :style="{width: `${10*numberOfQuotes}%`}">
                {{numberOfQuotes}}/10
            </div>
        </div>
    </div>


</template>
<script>
import { bus } from "../../src/main.js";
export default {
  data: () => {
    return {
      numberOfQuotes: 0
    };
  },
  created() {
    bus.$on("incrementProgress", data => {
      this.numberOfQuotes = data;
    });
    bus.$on("quoteWasDeleted", deleted => {
      this.numberOfQuotes--;
    });
  }
};
</script>
<style>
.progress {
  text-align: center;
}
</style>