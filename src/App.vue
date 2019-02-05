<template>
    <section class="mainPage">
        <form class="viewMode">
            <h1>Calculator</h1>
            <input v-model="result"></input>
        </form>
        <section class="btnNumbers">
            <button v-on:click="getResult(1)" class="btn">1</button>
            <button v-on:click="getResult(2)" class="btn">2</button>
            <button v-on:click="getResult(3)" class="btn">3</button>
            <button v-on:click="getResult(4)" class="btn">4</button>
            <button v-on:click="getResult(5)" class="btn">5</button>
            <button v-on:click="getResult(6)" class="btn">6</button>
            <button v-on:click="getResult(7)" class="btn">7</button>
            <button v-on:click="getResult(8)" class="btn">8</button>
            <button v-on:click="getResult(9)" class="btn">9</button>
            <button v-on:click="getResult('.')" class="btn">.</button>
            <button v-on:click="getResult(0)" class="btn">0</button>
            <button v-on:click="deleteLastSymbol()" class="btn">&#8592;</button>
        </section>
        <section class="btnMethods">
            <button v-on:click="getResult('+')" class="btn">&#43;</button>
            <button v-on:click="getResult('-')" class="btn">&#45;</button>
            <button v-on:click="getResult('*')" class="btn">&#42;</button>
            <button v-on:click="getResult('/')" class="btn">&#247;</button>
            <button v-on:click="getSqrt()" class="btn">&#8730;</button>
            <button v-on:click="getPow(1)" class="btn">^2</button>
            <button v-on:click="getResult('(')" class="btn">&#40;</button>
            <button v-on:click="getResult(')')" class="btn">&#41;</button>
            <button v-on:click="totalGetResult()" class="btn">&#61;</button>
        </section>
    </section>
</template>

<script>
export default {
    data () {
        return {
            result: ''
        }
    },
    methods:{
        getResult: function(btnVal){
            this.result += '' + btnVal;
        },
        deleteLastSymbol: function(){
            if (this.result.length !== undefined){
            this.result = this.result.slice(0, this.result.length-1);
        } else{
            this.result = '';
        }
        },
        totalGetResult: function() {
            this.result = eval(this.result)
            console.log(this.result)
        },
        getSqrt: function() {
            this.result = 'Math.sqrt('+this.result+')'
            this.totalGetResult()
        },
        getPow: function() {
            this.result = 'Math.pow('+this.result+','+2+')'
            this.totalGetResult()
        }

    }
}
</script>

<style>
body{
    background-color: #5d5c61;
    font-family: 'Roboto', sans-serif;
}
.viewMode{
    display: grid;
    justify-content: center;
}
h1{
    display: flex;
    justify-content: center;
    max-width: 900px;
    color: #85dcbb;
    font-size: 36px;
}
input{
    margin-bottom: 25px;
    padding: 5px;
    width: 400px;
    height: 50px;
    font-size: 18px;
    border: 2px solid #04060f;
    background-color: #ebf2ea;
    border-radius: 10px;
    outline: 0;
}
.btnNumbers{
    display: grid;
    justify-content: center;
    grid-template-columns: 100px 100px 100px;
    grid-column-gap: 10px;
    grid-row-gap: 10px;
    margin-bottom: 50px;
}
.btn{
    border: 2px solid #04060f;
    background-color: #ebf2ea;
    font-size: 18px;
    border-radius: 10px;
    height: 50px;
    outline: 0;
}
.btn:active{
    background-color: #04060f;
    color: #ebf2ea;
}
.btnMethods{
    display: grid;
    justify-content: center;
    grid-template-columns: 50px 50px 50px 50px 50px 50px 50px 50px 50px;
    grid-column-gap: 10px;
}
</style>
