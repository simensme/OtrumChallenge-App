<script setup>
import { ref } from 'vue';

// Mock-up DB for names before I create backend
const people = ref([
    { name: 'George Bush', age: 25 },
    { name: 'Max Derby', age: 36 },
    { name: 'Barrack Obama', age: 50 },
    { name: 'Winston Churchill', age: 95 },
    { name: 'James Cage', age: 39 },
]);

const newPerson = ref({
    name: '',
    age: '',
});

const addPerson = () => {
    if (newPerson.value.name && newPerson.value.age) {
        people.value.push({ ...newPerson.value });
        newPerson.value.name = '';
        newPerson.value.age = '';
    }
};


</script>

<template>
    <div class="main">
        <div class="header">
            <h1>NameList</h1>
        </div>
        <table>
            <tbody>
                <tr v-for="(person, index) in people" :key="index">
                    <td>{{ person.name }}</td>
                    <td>{{ person.age }}</td>
                    <td>X</td>
                </tr>
                <tr>
                    <td><input class="input-field" v-model="newPerson.name" placeholder="Name" /></td>
                    <td><input class="input-field" v-model="newPerson.age" placeholder="Age" /></td>
                </tr>
            </tbody>
        </table>
        <div class="button-container">
            <div class="add-container">
                <button @click="addPerson">+ Add</button>
            </div>
            <div class="reload-save-container">
                <button id="reload">Reload</button>
                <button id="save">Save</button>
            </div>
        </div>
    </div>
</template>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

html {
    background: rgb(227, 227, 227);
    box-sizing: border-box;
}

body {
    min-height: 100vh;
    font-family: 'Roboto', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0;
    padding: 0;
}

.main {
    width: 38%;
    margin: 0 auto;
}

/* Title */
.header {
    background-color: #909090;
    color: #fff;
    text-align: center;
    border-radius: 20px;
    width: 96%;
    margin: 0 auto;
}

h1 {
    padding: 10px;
}

/* Table Content */
table {
    border-spacing: 10px;
    width: 100%;
    table-layout: fixed;
}

tbody {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
    background-color: #f9f9f9;
}

td {
    border: 3px solid #299026;
    padding: 14px;
    white-space: nowrap;
}

td:first-child {
    width: 87%;
}

td:nth-child(2) {
    width: 9%;
}

td:nth-child(3) {
    width: 4%;
}

/* Input-field */
.input-field {
    width: 100%;
    margin: 0;
    box-sizing: border-box;
    outline: none;
    border: none; 
    padding: 0; 
    background-color: transparent; 
    font-family: 'Roboto', sans-serif;
    font-size: inherit; 
}

/* Buttons */
.button-container {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
}

.add-container,
.reload-save-container {
    text-align: center;
}

.add-container {
    margin-left: 5px;
}

.reload-save-container {
    display: flex;
    gap: 10px;
    justify-content: flex-end;
    margin-top: 55px;
    margin-right: 5px;
}

button {
    padding: 10px;
    margin: 5px;
    cursor: pointer;
    font-family: 'Roboto', sans-serif;
    font-size: 18px;
    color: #000000;
    background: #ffffff;
    padding: 10px 20px;
    border: solid #2fab1f 3px;
    text-decoration: none;
    position: relative;
}

button:hover {
    background: rgb(199, 199, 199);
}

button:active {
    bottom: -2px;
    right: -2px;

}
</style>