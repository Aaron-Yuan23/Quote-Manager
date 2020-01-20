<template>
    <div class="container">
        <appHeader :quoteCount="quotes.length":maxQuotes="maxQuotes"></appHeader>
        <app-new-quote @quoteAdded="NewQuote"></app-new-quote>
        <appQuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></appQuoteGrid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alart alert-info">
                    Info: Click on a Quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from "./components/QuoteGrid.vue";
    import NewQuote from "./components/NewQuote.vue";
    import Header from "./components/Header.vue";
    export default {
        data: function(){
           return{
               quotes:[
                   "Just a Quote to see something"
               ],
               maxQuotes: 10,
               
           } 
        },
        methods:{
            NewQuote(quote){
                if(this.quotes.length >= this.maxQuotes){
                    return alert("Please delete Quote first!");
                }
                this.quotes.push(quote);
            },
            deleteQuote(index){
                this.quotes.splice(index, 1);
            }
        },
        components:{
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header,
        }
    }
</script>

<style>
</style>
