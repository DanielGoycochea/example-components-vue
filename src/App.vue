<template>
  <div class="container">
    <Header
    :quoteCount="quotes.length"
    :maxQuotes="maxQuotes"
    ></Header>
    <newQuote @quoteAdded ="newQuote"></newQuote>
    <QuoteGrid 
      :quotes='quotes'
      @quoteDeleted="deleteQuote"
      ></QuoteGrid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          info: Click on a Quote to delete it!
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import QuoteGrid from './components/QuoteGrid.vue'
import newQuote from './components/newQuote.vue'
import Header from './components/Header.vue'

export default {
  data: function () {
    return {
      quotes:[
        'just a Quote to see something'
      ],
      maxQuotes: 10
    }
  },
  methods:{
    newQuote: function (quote){
      if (this.quotes.length>= this.maxQuotes){
        return alert(' borra una para continuar')
      }
      this.quotes.push(quote)
    },
    deleteQuote: function (index) {
      this.quotes.splice(index,1)
    }
  },
  components:{
    QuoteGrid,
    newQuote,
    Header
  }
}
</script>
<style scoped>

</style>