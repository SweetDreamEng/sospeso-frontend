<template>
    <CDataTable
            class="mb-0 table-outline"
            hover
            :items="tableItems"
            :fields="tableFields"
            head-color="light"
            no-sorting
    >
        <td slot="mode" slot-scope="{item}">
            <div>{{item.mode.name}}</div>
        </td>
        <td slot="match" slot-scope="{item}" class="table-cell">
            <MatchSelect></MatchSelect>
        </td>
        <td slot="tot-match" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>
        </td>
        <td slot="pre-odd" slot-scope="{item}" class="table-cell">
            <div>{{item.medio.value}}</div>

        </td>
        <td slot="odd" slot-scope="{item}" class="table-cell">
            <div>{{item.elevato.value}}</div>

        </td>
        <td slot="back" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>

        </td>
        <td slot="lay" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>

        </td>
        <td slot="status" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>

        </td>
        <td slot="minute" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>

        </td>
        <td slot="score" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>

        </td>
        <td slot="gain-losses" slot-scope="{item}" class="table-cell">
            <div>{{item.facile.value}}</div>

        </td>
        <td slot="facile" slot-scope="{item}" class="table-cell">
            <div class="clearfix">
                <div class="float-left">
                    <CInput type="number" min="-1" :value="item.facile.value" @click="mode = item.mode.name" @update:value="saveTable1" class="facile"></CInput>
                </div>
            </div>
        </td>
        <td
            slot="medio"
            slot-scope="{item}"
            class="table-cell"
        >
            <div class="float-left">
                <CInput v-if="item.mode.name != 'Special %' && item.mode.name != 'Special min'" type="number" min="-1" :value="item.medio.value" @click="mode = item.mode.name" @update:value="saveTable2" class="facile"></CInput>
            </div>
        </td>
        <td slot="elevato" slot-scope="{item}" class="table-cell">
            <div class="float-left">
                <CInput v-if="item.mode.name != 'Special %' && item.mode.name != 'Special min'" type="number" min="-1" :value="item.elevato.value" @click="mode = item.mode.name" @update:value="saveTable3" class="facile"></CInput>
                <span v-if="item.mode.name != 'Special %' && item.mode.name != 'MG' && item.mode.name != 'Special min'" style="position: relative; top: 6px; left: 4px;">%</span>
            </div>
        </td>
    </CDataTable>
</template>

<script>
    import MatchSelect from "./utilities/MatchSelect";
    export default {
        name: 'DashboardTable',
        components: {
            MatchSelect
        },
        data () {
            return {
                tableItems: [
                    {
                        mode: { name: 'GN'},
                        facile: { value: 10},
                        medio:{value: 20},
                        elevato:{value: 30},
                    },
                    {
                        mode: { name: 'GT'},
                        facile: { value: 3},
                        medio:{value: 5},
                        elevato:{value: 10},
                    },
                    {
                        mode: { name: 'MG'},
                        facile: { value: 10},
                        medio:{value: 30},
                        elevato:{value: 60},
                    },
                    {
                        mode: { name: 'SLN'},
                        facile: { value: 30},
                        medio:{value: 60},
                        elevato:{value: 91},
                    },
                    {
                        mode: { name: 'SLT'},
                        facile: { value: 9},
                        medio:{value: 15},
                        elevato:{value: 30},
                    },
                    {
                        mode: { name: 'Special %'},
                        facile: { value: 10},
                        medio:{value: 0},
                        elevato:{value: 0},
                    },
                    {
                        mode: { name: 'Special min'},
                        facile: { value: 45},
                        medio:{value: 0},
                        elevato:{value: 0},
                    }
                ],
                tableFields: [
                    { key: 'match', label:  'Match'},
                    { key: 'tot-match', label:  'Tot. Matched'},
                    { key: 'pre-odd', label:  'Pre Odd'},
                    { key: 'odd', label:  'Odd'},
                    { key: 'back', label:  'Back', _classes: 'table-info'},
                    { key: 'lay', label:  'Lay', _classes: 'table-danger'},
                    { key: 'status', label:  'Status'},
                    { key: 'minute', label:  'Minute'},
                    { key: 'score', label:  'Score'},
                    { key: 'gain-losses', label:  'Gain/Losses%'},
                ],
            }
        }
    }
</script>

<style scoped>

</style>