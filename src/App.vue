<template>
  <div class="container">
    <div class="row">
      <app-quote-bar :quotes="quotes"></app-quote-bar>
    </div>
    <div class="row">
     <div v-if="tooManyQuotes" class="col-sm-4 alert alert-danger" role="alert">
       <button type="button">
         <span aria-hidden="true">&times;</span>
         <span class="sr-only">Close</span>
       </button>
       <strong style="text-align: center">Holy guacamole!</strong> You're at maximum quotes.
     </div>
    </div>
      <app-new-quote @quoteAdded="newQuote"></app-new-quote>
      <app-quote-grid :quotes="quotes" @quoteDeleted="destroyQuote"></app-quote-grid>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'
import QuoteBar from './components/QuoteBar.vue'

export default {

  data() {
    return {
      quotes: [],
      maxQuotes: 10,
      tooManyQuotes: false
    };
  },
  methods: {
    destroyQuote(index) {
      console.log(index)
      this.quotes.splice(index, 1)
      if (this.tooManyQuotes >= 10) {
        this.tooManyQuotes = true
      } else {
        this.tooManyQuotes = false;
      }
    },
    newQuote(quote) {
      if (this.quotes.length < this.maxQuotes) {
        this.quotes.push(quote)
      } else {
        this.tooManyQuotes = true;
      }
    }
  },
  components: {
      appQuoteGrid: QuoteGrid,
      appNewQuote: NewQuote,
      appQuoteBar: QuoteBar
  }
};
</script>

<style>
</style>
