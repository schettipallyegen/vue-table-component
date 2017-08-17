<template>
    <div>
        <div v-if=tableData.length>
            <h1> Table Here </h1>
            <table>
                <tr>
                    <th v-for="(name, index) in tableHeaders" :key="index"> {{name}}</th>
                    <th>Action</th>
                </tr>
                <tr v-for="(tRow, index) in tableData" :key="index">
                    <td v-for="(tData, index) in tRow" :key="index">{{tData}}</td>
                    <td class="action" @click="removeLeagueMember(index)"> Remove </td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
    import _ from 'lodash';
    
    export default {
        props: ['tableData', 'tableHeaders'],
        methods: {
            removeLeagueMember(index) {
                this.tableData.splice(index, 1);
            }
        }
    }
</script>

<style lang="scss">
    .action {
        color: blue;
        cursor: pointer;
    }
    
    table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        width: 100%;
    }
    
    td,
    th {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
    }
    
    tr:nth-child(even) {
        background-color: #dddddd;
    }
</style>
