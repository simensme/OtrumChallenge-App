<script setup>

</script>

<template>
    <div class="header">
        <h1>Navneliste</h1>
    </div>

    <div>
        <table>
            <thead class="item-list">
                <tr>
                    <th class="navn-column">Navn</th>
                    <th class="alder-column">Alder</th>
                    <th class="x-column">Slett</th>
                </tr>
            </thead>
            <tbody class="item-list">
                <tr>
                    <td>George Bush</td>
                    <td>25</td>
                    <td>X</td>
                </tr>
                <tr>
                    <td>Max Derby</td>
                    <td>36</td>
                    <td>X</td>
                </tr>
                <tr>
                    <td>Barrack Obama</td>
                    <td>50</td>
                    <td>X</td>
                </tr>
            </tbody>
        </table>
    </div>

    <div class="add-container">
        <button id="save">Add</button>
    </div>

    <div class="reload-save-container">
        <button id="reload">Reload</button>
        <button id="save">Save</button>
    </div>
</template>

<style>
body {
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}
h1 {
    margin: 0;
}

.header {
    background-color: #a9a9a9;
    color: #fff;
    text-align: center;
    border-radius: 10px;
    padding: 10px;

}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
}

th,
td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
}

th {
    background-color: #333;
    color: #fff;
}

.navn-column {
    width: 60%;
    /* Adjust the width for the "Navn" column */
}

.alder-column,
.x-column {
    width: 20%;
    /* Adjust the width for the "Alder" and "X" columns */
}

.item-list {
    background-color: #f9f9f9;
}

.add-container,
.reload-save-container {
    margin-top: 20px;
    text-align: center;
}

button {
    padding: 10px;
    margin: 5px;
    cursor: pointer;
}

#reload {
    background-color: #4285f4;
    color: #fff;
}

#save {
    background-color: #34a853;
    color: #fff;
}
</style>