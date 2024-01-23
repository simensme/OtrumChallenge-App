<script setup>
import { ref, onMounted } from 'vue';

const people = ref([]);
const newPerson = ref({
    name: '',
    age: '',
});

const isValidAge = age => {
    if (age <= 130) {
        return !isNaN(age) && parseInt(age, 10) >= 0;
    }
};

const isDuplicateName = name => {
    return people.value.some(person => person.name === name);
};

const addPerson = async () => {
    const trimmedName = newPerson.value.name.trim();
    if (trimmedName && isValidAge(newPerson.value.age)) {
        if (!isDuplicateName(trimmedName)) {
            const response = await fetch('http://localhost:8080/name-list', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    name: trimmedName,
                    age: parseInt(newPerson.value.age, 10),
                }),
            });
            if (response.ok) {
                fetchPeople();
                newPerson.value.name = '';
                newPerson.value.age = '';
            } else {
                console.error('Error adding person:', response.statusText);
            }
        } else {
            alert('Name already exsists, please enter a different name');
        }
    } else {
        alert('Please enter a valid age');
    }
};

const deletePerson = async (index) => {
    const deletedPerson = people.value[index];
    await new Promise((resolve) => setTimeout(resolve, 0));
    if (deletedPerson) {
        const response = await fetch(`http://localhost:8080/name-list/${index}`, {
            method: 'DELETE',
        });
        if (response.ok) {
            people.value.splice(index, 1);
        } else {
            console.error('Error deleting person:', response.statusText);
        }
    } else {
        console.error('Invalid person data or missing ID.');
    }
};

const fetchPeople = async () => {
    try {
        const response = await fetch('http://localhost:8080/name-list');
        const data = await response.json();
        people.value = data.map((person) => ({ ...person }));
    } catch (err) {
        console.error('Error fetching data:', err);
    }
};

const reload = () => {
    fetchPeople();
    window.location.reload(true);
};

onMounted(() => {
    fetchPeople();
});

</script>
<template>
    <div class="main">
        <div class="header">
            <h1>NameList</h1>
        </div>
        <table>
            <tbody>
                <tr v-for="(person, index) in people" :key="index">
                    <td>
                        <input class="input-field" v-model="person.name" />
                    </td>
                    <td>
                        <input class="input-field" v-model="person.age" />
                    </td>
                    <td class="delete-button" @click="deletePerson(index)">X</td>
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
                <button @click="reload">Reload</button>
                <button>Save</button>
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

/* Buttons for deleting a particular person */
.delete-button {
    padding: 10px;
    margin: 5px;
    cursor: pointer;
    font-family: 'Roboto', sans-serif;
    font-size: 18px;
    padding: 10px 20px;
    text-decoration: none;
    position: relative;
}

.delete-button:hover {
    background: rgb(199, 199, 199);
}

.delete-button:active {
    bottom: -2px;
    right: -2px;
}
</style>