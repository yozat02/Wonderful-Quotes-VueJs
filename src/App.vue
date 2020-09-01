<template>
    <div class="container">
        <appHeader :max="max" :quoteCounter="quotes.length"></appHeader>
        <appNewQupte @addNewQuote="newQuote"></appNewQupte>
        <appQuoteGrid :quotes="quotes" @deleteQuote="deleteQuote"></appQuoteGrid>
        <div class="row" >
        <div class="col-sm-12 center-text">
            <div class="alert alert-info">Info: Click on a quote to delete it!</div>
        </div>
    </div>
    </div>
      
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue' ;
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';
    export default {
        data: function(){
            return {
                max: 10,
                quotes: ['Just a quote to test']
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQupte : NewQuote,
            appHeader : Header
        },
        methods:{
             newQuote(quote){
                 if(this.quotes.length == 10){
                     return alert('Please delete a quote first !')
                 }
                this.quotes.push(quote) ;
            },
            deleteQuote(index){
                this.quotes.splice(index,1)
            }
        }
    }
</script>

<style>
</style>
