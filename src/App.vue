<template>
    <div id="app">
        <h1>MontyHall Problem VueJs</h1>
        <div class="form">
            <div v-if="!started">
                <label for="portsAmount">How many doors?</label>
                <input type="number" id="portsAmount" size="3" v-model.number="portsAmount">
            </div>

            <div v-if="!started">
                <label for="selectedPort">Which door you choose?</label>
                <input type="number" id="selectedPort" size="3" v-model.number="selectedPort">
            </div>

            <button v-if="!started" @click="started = true">Start</button>

            <button v-if="started" @click="started = false">Start Over</button>
        </div>
        <div class="doors" v-if="started">
            <div v-for="i in portsAmount" :key="i">
                <MyDoor :hasGift="i === selectedPort" :number="i" />
            </div>
        </div>
    </div>
</template>

<script>
import MyDoor from './components/MyDoor.vue';

export default {
    name: 'App',
    components: { MyDoor },
    data: function () {
        return {
            started: false,
            portsAmount: 3,
            selectedPort: null
        }
    }
}
</script>

<style>
* {
    box-sizing: border-box;
    font-family: "Montserrat", sans-serif;
}

body {
    margin: 0;
    color: #fff;
    background: linear-gradient(to right, #3FB27F, #22303d);
}

#app {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1 {
    border: 1px solid #000;
    background-color: #0004;
    padding: 10px;
    margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    margin-bottom: 40px;
}

.form,
.form input,
.form button {
    margin-bottom: 10px;
    font-size: 1.5rem;
    cursor: pointer;
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

input {
    width: 15%;
    margin-left: 10px;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}
</style>