<template>
    <div>
        <heading class="mb-6">Price Tracker</heading>
        <h3>Rates</h3>
        <br/>
        <p >USD : {{rates.USD}}</p>
        <p >GBP : {{rates.GBP}}</p>
        <p >EUR  : {{rates.EUR}}</p>

    </div>
</template>

<script>
export default {
    mounted() {
        //
        this.fetchApiData();
    },

    data:function(){
        return {
            "test":"test data",
            "rates":""
        }

    },

    methods:{

        fetchApiData(){
            fetch("https://api.exchangeratesapi.io/latest?base=INR", {
                "method": "GET",
                "headers": {
                    "Accept":"*/*"
                }
            })
            .then(response => { 
                if(response.ok){
                    return response.json()    
                } else{
                    alert("Server returned " + response.status + " : " + response.statusText);
                }                
            })
            .then(response => {
                this.rates = response.rates
                console.log(response);
            })
            .catch(err => {
                console.log(err);
            });
        }
    }

}
</script>

<style>
/* Scoped Styles */
</style>
