<script setup>

</script>

<template>
    <div class="main">
        <div class="header">
            <h1>NameList</h1>
        </div>
        <table>
            <tbody>
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
                <tr>
                    <td>Winston Churchill</td>
                    <td>95</td>
                    <td>X</td>
                </tr>
                <tr>
                    <td>James Cage</td>
                    <td>39</td>
                    <td>X</td>
                </tr>
            </tbody>
        </table>
        <div class="button-container">
            <div class="add-container">
                <button id="add">+ Add</button>
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
    width: 90%;
}

td:nth-child(2) {
    width: 6%;
}

td:nth-child(3) {
    width: 4%;
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
    margin-top: 50px;
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