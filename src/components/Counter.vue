<template>
    <h2>{{ customTitle}}</h2>
    <p> {{ counter }} <sup>2</sup>  = {{ SquareCounter }} </p>
    <p data-test-id='counter'> {{ counter }} </p>

    <div class="buttons">
        <button @click="increase()">+1</button>
        <button @click="decrease()">-1</button>
    </div>
</template>

<script>
    export default {
        props:{
           title: String,
           start: {
               type: Number,
               default: 100,
               validator( value ) {
                   return value >= 0
               }
               //required: true
           }
        },
        data() {
           return {
               counter: this.start
           }
        },
        methods: {
           getSquareVal() {
                return this.counter * this.counter
           },
           increase() {
                this.counter++
           },
           decrease () {
                this.counter <= 0 ? 0 : this.counter-- 
           }
       },
       computed: {
           //TODO: Las Propiedades Computadas se guardan en Cache
           SquareCounter() {
     
                return this.counter * this.counter
           },
           customTitle() {
               return this.title || 'Counter'
           }
       }

    }
</script>

<style scopde>

button {
   background-color: #64BB87;
   border-radius: 5px;
   border:1px solid white;
   color:white;
   cursor: pointer;
   margin: 0 5px;
   padding:  5px 15px;
   transition: 0.3s ease-in-out;
}

button:hover {
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;
}

</style>
