<script>
export default {
    name: "WelcomeMessageComponent",
    data() {
        return {
            message: 'Hello World! Mark',
            count:0,
            c:0,
            f:32,
            firstNum:"",
            secondNum:"",
            firstName:"",
            lastName:"",
            address:"",
            notes:"",


        }
    },
    methods:{
        setC(e, c =+ e.target.value){
            this.c = c
            this.f = c * (9 / 5) + 32
        },
        setF(e, f =+ e.target.value){
            this.f = f
            this.f = (f - 32) * (5 / 9)
        }

    }
}
</script>
<template>
    <h1>{{ message }}</h1>
    <p>This is counter functions {{ count }}</p>
    <button @click = "count++">Click</button>

    <p>Temperature Converter</p>
    <input type="number"  v-model.number="firstNum">
    Celsius = 
    <input type="number"  v-model.number="secondNum">
    Fahrenheit
    <br>
    <span> Result {{ firstNum + secondNum }}</span>

    <div class="row">
        <div class="col-md-6">
            
            <p><input v-model="firstName" placeholder="Enter your First Name" /></p>
            <p><input v-model="lastName" placeholder="Enter your Last Name"></p>
            <p><input v-model="address" placeholder="Enter your Address"></p>
            <p><textarea v-model="notes" placeholder="Enter any additional notes"></textarea></p>
            
        </div>
        <div class="col-md-6">
            <p>Please Review Your Informations</p>
            <p>Your Name: {{ firstName}} {{ lastName }}</p>
            <p>Address: {{ address }}</p>
            <p style="white-space:pre-line;">Note: {{ notes }}</p>


        </div>
    </div>
</template>