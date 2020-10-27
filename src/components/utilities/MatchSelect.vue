<template>
    <CSelect
            :value.sync = "key1"
            :options="eventLists3"
            @update:value="select_match"
    >
    </CSelect>
</template>

<script>

    export default {
        name: 'MatchSelect',
        props: {
            eventLists3: {
                type: Array
            },
            updateItem: {
                type: Function
            },
            index: {
                type: Number
            }
        },
        components: {
        },
        data () {
            return {
                key1: ''
            }
        },
        methods: {
            // Filter
            select_match(val){
                this.updateItem(val, this.index);
            },
        },
        watch: {
            eventLists3(value) {
                alert('hi');
                console.log('eventLists3 value => ', value);
            },
            tableItem(value) {
                console.log('tableItem value => ', value);
            }
        },
        created() {
        }
    }
</script>
<style scoped>

    /* Dashboard Logo */
    .dashboard-logo-wrapper {
        min-width: 300px;
    }
    .dashboard-logo {
        width: 200px;
        display: initial;
        color: #ca2640;
        background-color: rgb(247, 205, 205);
        border: 1px solid red;
        text-align: center;
        font-weight: 500;
        font-size: 2.4em !important;
        margin: 0;
        padding: 0 30px;
    }
    
    /* Filter */
    /* Checkbox of Filter */
    .check-box {
        margin-bottom: 20px;
    }
    .checkbox-group {
        display: flex;
    }
    .checkbox-group .checkbox-sub-group {
        width: 20%;
        flex: 1;
        text-align: left;
    }
    .checkbox-sub-group label {
        align-self: center;
    }
    /* End Checkbox of Filter */
    /* Label */
    label.sub-title {
        color: red;
        font-weight: 600;
        display: block;
    }
    /* End Label */
    /* Input of Filter */
    .odd-filter, .matched-filter {
        display: inline-flex;
        align-items: center;
        justify-content: space-around;
    }
    .odd-filter .form-group, .matched-filter .form-group {
        margin: 0 5px;
    }
    .odd-filter label, .matched-filter label {
        margin: 0;
    }
    /* End Input of Filter */
    /* End Filter */
    
    /* Button */
    .btn-success {
        color: #2b2b2b;
        background-color: #e6eef5;
        border-color: #ebedef;
        font-size: 1.1em;    
        width: 100%;
        min-width: 100px;
        margin-top: 28px!important;
    }
    /* End Button */

</style>

<style>
    .facile{
        float: left;
    }
    .table-cell input{
        max-width: 70px;
    }
    .table-cell{
        background: lightgoldenrodyellow;
        height: 50px;
        border-left: 1px solid lightgray;
    }
    .table td {
        padding: 5px;
    }
    .float-left{
        height: 35px;
    }
    .table th, .table td {
        border-top: 0px solid!important;
        border-bottom: 1px solid lightgray!important;
    }
    .table{
        margin-bottom: 0!important;
        border-bottom: none;
    }
    @media screen and (max-width: 600px) {
        .table-cell input{
            max-width: 44px;
        }
    }
</style>