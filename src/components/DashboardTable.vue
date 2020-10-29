<template>
    <CDataTable v-if="tableItems.length"
            class="mb-0 table-outline"
            hover
            :items="tableItems"
            :fields="tableFields"
            head-color="light"
            no-sorting
    >
        <template #match="{item, index}">
            <td class="table-cell">
                <MatchSelect 
                    :updateItem="updateItem"
                    :eventLists3="eventLists3"
                    :index="index"
                    :propEventId="propEventId"
                    :item="item"
                    :all="all"
                >
                </MatchSelect>
            </td>
        </template>
        <template #tot="{item}">
            <td class="table-cell text-center">    
                {{item.tot.value}}
            </td>
        </template>
        <template #preodd="{item}">
            <td class="table-cell text-center">    
                {{item.preodd.value}}
            </td>
        </template>
        <template #odd="{item}">
            <td class="table-cell text-center">    
                {{item.odd.value}}
            </td>
        </template>
        <template #back="{item}">
            <td class="table-info text-center">    
                {{item.back.value}}
            </td>
        </template>
        <template #lay="{item}">
            <td class="table-danger text-center">    
                {{item.lay.value}}
            </td>
        </template>
        <template #status="{item}">
            <td class="table-cell text-center">    
                {{item.status.value}}
            </td>
        </template>
        <template #minute="{item}">
            <td class="table-cell text-center">    
                {{item.minute.value}}
            </td>
        </template>
        <template #score="{item}">
            <td class="table-cell text-center">    
                {{item.score.value}}
            </td>
        </template>
        <template #gain="{item}">
            <td class="table-cell text-center">    
                {{item.gain.value}}
            </td>
        </template>
    </CDataTable>
    <div v-else class="d-flex justify-content-center align-items-center">
        <CSpinner
            color="primary"
            style="width:4rem;height:4rem;"
        />
    </div>
</template>

<script>
    import MatchSelect from "./utilities/MatchSelect";
    export default {
        name: 'DashboardTable',
        props:  {
            eventLists3: {
                type: Array
            },
            competitionList: {
                type: Array
            },
            mainList: {
                type: Array
            },
            eventLists: {
                type: Array
            },
            prematchOddList: {
                type: Array
            },
            eventFlag: {
                type: Boolean
            },
            clickEventValue: {
                type: String
            }
        },
        components: {
            MatchSelect
        },
        data () {
            return {
                tableItems: [],
                eventListsLength: 0,
                tableFields: [],
                eventId: 0,
                propEventId: 0,
                childEventLists: [],
                all: false,
                selectionId: '',
                marketIds: []
            }
        },
        methods : {
            updateItem(val, index) {
                this.select_match(val);
                this.tableItems[index].tot.value = '€' + this.total_matched;
                this.tableItems[index].preodd.value = this.prematchOdd;
                this.tableItems[index].back.value = this.back;
                this.tableItems[index].lay.value = this.lay;
                this.tableItems[index].status.value = this.status;
                if (this.timeRecord.includes('undefined')) {
                    this.tableItems[index].minute.value = 'Unknown';
                } else {
                    this.tableItems[index].minute.value = this.timeRecord;
                }
                this.tableItems[index].score.value = this.scoreOne + this.scoreTwo;
                this.tableItems[index].gain.value = this.percent_text2;

                if (!this.marketIds.includes(this.marketId)) {
                    this.marketIds.push(
                        {
                            'index': index,
                            'market': this.marketId
                        });
                }
            },
            select_match(val){
                this.key = '0'
                if(val == ''){
                    return
                }
                this.selectedArray = val.split(',')
                this.selectedValue = val
                if(this.selectedArray[0] != '0'){
                    this.eventId = this.selectedArray[0]
                    this.marketId =''
                    this.selectionId =''
                    this.lay =''
                    this.back =''
                    this.total_matched = 0
                    this.back_matched = 0
                    this.lay_matched = 0
                    this.scoreOne =''
                    this.scoreTwo =''
                    this.status =''
                    this.marketStatus =''
                    this.timeRecord=''

                    let self = this
                    let competitionNode = this.competitionList.filter(function(item) {
                        return item.eventId == self.eventId;
                    });

                    if(competitionNode.length > 0){
                        this.competitionName = "Competition >> " + competitionNode[0].competitions[0].name
                    }else{
                        this.competitionName = 'Competition >> N/D'
                    }

                    for(let i = 0; i < this.mainList.length; i++){
                        let eventValue = this.mainList[i]
                        if(eventValue.eventId == this.eventId){

                            if(eventValue.score){
                                let scoreDetail = eventValue.score
                                this.scoreOne = scoreDetail.home.score + ' - '
                                this.scoreTwo = scoreDetail.away.score
                            }
                            else{
                                this.scoreOne =''
                                this.scoreTwo =''
                            }
                            if(eventValue.status){
                                this.status = 'Live'
                                this.timeRecord = eventValue.timeElapsed + "'"
                            }
                            else if(!eventValue.status){
                                this.status = 'Coming Up'
                                this.timeRecord =''
                            }
                            if(eventValue.inPlayMatchStatus == 'FirstHalfEnd'){
                                this.timeRecord = 'HT'
                            }
                        }
                    }
                }

                if(this.selectedArray[0] == '0'){

                    let eventId = parseInt(this.selectedArray[1])
                    let marketType = this.selectedArray[2]
                    let team = parseInt(this.selectedArray[3])
                    let runnerNo = parseInt(this.selectedArray[6])

                    //----------------------------classic_part--------------------------------
                    if(marketType == 'MATCH_ODDS'){
                        if(team == '0'){
                            if(runnerNo == '0'){
                                this.classic_match = '- 1 - Back'
                            }
                            else{
                                this.classic_match = '- 1 - Lay'
                            }
                        }
                        else if(team == '1'){
                            if(runnerNo == '0'){
                                this.classic_match = '- 2 - Back'
                            }
                            else{
                                this.classic_match = '- 2 - Lay'
                            }
                        }
                        else if(team == '2'){
                            if(runnerNo == '0'){
                                this.classic_match = '- X - Back'
                            }
                            else{
                                this.classic_match = '- X - Lay'
                            }
                        }
                    }
                    else if(marketType == 'OVER_UNDER_05'){
                        if(team == '1'){
                            if(runnerNo == '0'){
                                this.classic_match = '- O 0.5 - Back'
                            }
                            else{
                                this.classic_match = '- O 0.5 - Lay'
                            }
                        }
                    }
                    else if(marketType == 'OVER_UNDER_15'){
                        if(team == '0'){
                            if(runnerNo == '0'){
                                this.classic_match = '- U 1.5 - Back'
                            }
                            else{
                                this.classic_match = '- U 1.5 - Lay'
                            }
                        }
                        else{
                            if(runnerNo == '0'){
                                this.classic_match = '- O 1.5 - Back'
                            }
                            else{
                                this.classic_match = '- O 1.5 - Lay'
                            }
                        }
                    }
                    else if(marketType == 'OVER_UNDER_25'){
                        if(team == '0'){
                            if(runnerNo == '0'){
                                this.classic_match = '- U 2.5 - Back'
                            }
                            else{
                                this.classic_match = '- U 2.5 - Lay'
                            }
                        }
                        else{
                            if(runnerNo == '0'){
                                this.classic_match = '- O 2.5 - Back'
                            }
                            else{
                                this.classic_match = '- O 2.5 - Lay'
                            }
                        }
                    }
                    else if(marketType == 'OVER_UNDER_35'){
                        if(team == '0'){
                            if(runnerNo == '0'){
                                this.classic_match = '- U 3.5 - Back'
                            }
                            else{
                                this.classic_match = '- U 3.5 - Lay'
                            }
                        }
                    }

                    //------------------------------------------------------------------------

                    this.eventId =eventId

                    let self = this
                    let competitionNode = this.competitionList.filter(function(item) {
                        return item.eventId == self.eventId;
                    });

                    if(competitionNode.length > 0){
                        this.competitionName = "Competition >> " + competitionNode[0].competitions[0].name
                        this.oddUrl = competitionNode[0].competitions[0].name.toLowerCase()
                        this.oddUrl = this.oddUrl.replace(" ", "-")

                        let eventNode = this.mainList.filter(function(item) {
                            return item.eventId == eventId;
                        });
                        if(eventNode){
                            this.oddUrl = this.oddUrl + "/" + eventNode[0].name.toLowerCase()
                            this.oddUrl = 'https://www.betfair.com/exchange/plus/en/football/' + this.oddUrl.replace(" ", "-") + '-betting-' + this.eventId
                        }
                    }else{
                        this.competitionName = 'Competition >> N/D'
                    }

                    let eventNode = this.mainList.filter(function(item) {
                        return item.eventId == eventId;
                    });

                    if(eventNode.length < 1){
                        return
                    }
                    //---------------score----------------
                    if(eventNode[0].score){
                        let scoreDetail = eventNode[0].score
                        this.scoreOne = scoreDetail.home.score + ' - '
                        this.scoreTwo = scoreDetail.away.score
                    }
                    else{
                        this.scoreOne =''
                        this.scoreTwo =''
                    }

                    if(eventNode[0].status){
                        this.status = 'Live'
                        this.timeRecord = eventNode[0].timeElapsed + "'"
                    }
                    else if(!eventNode[0].status){
                        this.status = 'Coming Up'
                        this.timeRecord =''
                    }
                    if(eventNode[0].inPlayMatchStatus == 'FirstHalfEnd'){
                        this.timeRecord = 'HT'
                    }

                    //----------------------------------------
                    let marketNode = eventNode[0].markets.filter(function(item) {
                        return item.marketType == marketType;
                    });
                    if(marketNode.length < 1){
                        return
                    }

                    if(marketNode[0].state){
                        if(marketNode[0].state.status == 'SUSPENDED'){
                            this.marketStatus = 'SUSPENDED'
                        }
                        else if(marketNode[0].state.status == "CLOSED"){
                            this.marketStatus = 'CLOSED'
                        }
                        else if(marketNode[0].state.status == "OPEN"){
                            this.marketStatus =''
                        }
                    }
                    this.marketId = marketNode[0].marketId

                    this.total_matched = marketNode[0].totalMatched
                    let runnerNode = marketNode[0].runners[team]

                    this.selectionId = runnerNode.selectionId
                    if(eventNode[0].status){
                        for(let u = 0; u < this.prematchOddList.length; u++){
                            let c1 =  this.marketId
                            let c2 =  this.prematchOddList[u].marketId
                            if(c1 == c2){
                                let runnerlists = this.prematchOddList[u].runners[team]
                                if(runnerNo == 0 && runnerlists.exchange && runnerlists.exchange.availableToBack){
                                    this.prematchOdd = runnerlists.exchange.availableToBack[0].price
                                }

                                if(runnerNo == 1 && runnerlists.exchange.availableToBack[0].price){
                                    this.prematchOdd = runnerlists.exchange.availableToBack[0].price
                                }

                            }
                        }

                        if(!runnerNode.exchange){
                            return
                        }
                        if(runnerNode.exchange.availableToBack){
                            this.back = runnerNode.exchange.availableToBack[0].price
                            this.back_matched = runnerNode.exchange.availableToBack[0].size
                        }
                        else{
                            this.back =
                                this.back_matched = 0
                        }
                        if(runnerNode.exchange.availableToLay){
                            this.lay = runnerNode.exchange.availableToLay[0].price
                            this.lay_matched = runnerNode.exchange.availableToLay[0].size
                        }
                        else{
                            this.lay =
                                this.lay_matched = 0
                        }

                    }
                    else{
                        if(!runnerNode.exchange){
                            return
                        }
                        if(runnerNode.exchange.availableToBack){
                            this.back = runnerNode.exchange.availableToBack[0].price
                            if(runnerNo == 0){
                                this.prematchOdd = this.back
                            }
                            this.back_matched = runnerNode.exchange.availableToBack[0].size
                        }
                        else{
                            this.back =''
                            if(runnerNo == 0){
                                this.prematchOdd = this.back
                            }
                            this.back_matched = 0
                        }
                        if(runnerNode.exchange.availableToLay){
                            this.lay = runnerNode.exchange.availableToLay[0].price
                            if(runnerNo == 1){
                                this.prematchOdd = this.lay
                            }
                            this.lay_matched = runnerNode.exchange.availableToLay[0].size
                        }
                        else{
                            this.lay =''
                            if(runnerNo == 1){
                                this.prematchOdd = this.lay
                            }
                            this.lay_matched = 0
                        }
                    }
                    this.odd_calc(0)
                    this.stake_calc(0)
                }
            },
            odd_calc(val){
                this.calc_odd = this.prematchOdd;
                this.calc_stake = 100;
                
                if(this.calc_odd != 0 && this.calc_stake != 0 && this.eventId != 0){
                    if(parseInt(this.selectedArray[6]) == 0){
                        this.max_profit = (this.calc_odd * this.calc_stake - this.calc_stake).toFixed(2)
                        this.max_lose = this.calc_stake
                        this.guad_max = this.max_profit
                        if(this.lay == '' || this.lay == 0){
                            this.guad_att = 0
                        }
                        else{
                            this.guad_att = (this.calc_odd * this.calc_stake/parseFloat(this.lay) -  this.calc_stake).toFixed(2)
                        }

                        if(this.guad_att > 0){
                            this.guad_att = (this.guad_att * (100 - this.bookmarkerFee)/100).toFixed(2)
                        }

                        if(this.guad_max != 0){
                            if(this.guad_att >= 0){
                                this.currentPercent = (100*this.guad_att/this.guad_max).toFixed(2)
                            }
                            else{
                                this.currentPercent = (100*this.guad_att/this.calc_stake).toFixed(2)
                            }
                        }
                        else{
                            this.currentPercent = 0
                        }
                        if(this.currentPercent > 0){
                            this.percentTextColor = '#20a052'
                            this.percentTextColor1 = '#20a052'
                            this.percentBackgroundColor = '#d8e4bc'
                            this.percentBackgroundColor1 = '#d8e4bc'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG == ''){
                                MG = '0'
                            }
                            if(this.riskTrading == 'easy'){
                                if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].facile.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].facile.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].facile.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].facile.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'medium'){
                                if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].medio.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].medio.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].medio.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].medio.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'risky'){
                                if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].elevato.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].elevato.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].elevato.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].elevato.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }

                        }
                        else if(this.currentPercent < 0){
                            this.percentTextColor = '#b80101'
                            this.percentTextColor1 = '#b80101'
                            this.percentBackgroundColor = '#ffc7ce'
                            this.percentBackgroundColor1 = '#ffc7ce'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG =='' ){
                                MG = '0'
                            }

                            if(this.riskTrading == 'easy'){
                                if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent < this.adminTable[0].facile.SLN * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent < this.adminTable[0].facile.SLT * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'medium'){
                                if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent < this.adminTable[0].medio.SLN * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent < this.adminTable[0].medio.SLT * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'risky'){
                                if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent < this.adminTable[0].elevato.SLN * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent < this.adminTable[0].elevato.SLT * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }

                        }
                    }
                    else{
                        this.max_lose = (this.calc_odd * this.calc_stake - this.calc_stake).toFixed(2)
                        this.max_profit = this.calc_stake
                        this.guad_max = this.calc_stake
                        if(this.back == '' || this.back == 0){
                            this.guad_att = 0
                        }
                        else{
                            this.guad_att = ( this.calc_stake - this.calc_odd * this.calc_stake/parseFloat(this.back)).toFixed(2)
                        }

                        if(this.guad_att > 0){
                            this.guad_att = (this.guad_att * (100 - this.bookmarkerFee)/100).toFixed(2)
                        }

                        if(this.guad_max != 0){
                            if(this.guad_att >= 0){
                                this.currentPercent = (100*this.guad_att/this.guad_max).toFixed(2)
                            }
                            else{
                                this.currentPercent = (100*this.guad_att/(this.calc_odd * this.calc_stake - this.calc_stake)).toFixed(2)
                            }
                        }
                        else{
                            this.currentPercent = 0
                        }
                        if(this.currentPercent > 0){
                            this.percentTextColor = '#20a052'
                            this.percentTextColor1 = '#20a052'
                            this.percentBackgroundColor = '#d8e4bc'
                            this.percentBackgroundColor1 = '#d8e4bc'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG =='' ){
                                MG = '0'
                            }

                            if(this.riskTrading == 'easy'){
                                if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].facile.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].facile.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].facile.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].facile.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'medium'){
                                if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].medio.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].medio.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].medio.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].medio.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'risky'){
                                if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].elevato.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].elevato.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].elevato.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].elevato.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }

                        }
                        else if(this.currentPercent < 0){
                            this.percentTextColor = '#b80101'
                            this.percentTextColor1 = '#b80101'
                            this.percentBackgroundColor = '#ffc7ce'
                            this.percentBackgroundColor1 = '#ffc7ce'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG =='' ){
                                MG = '0'
                            }
                        }
                    }
                }
                else{
                    this.max_profit = 0
                    this.max_lose = 0
                    this.guad_max = 0
                    this.percent_text2 = 'Insert Odd and Stake'
                    this.guad_att = 0
                    this.percentTextColor = '#20a052'
                    this.percentTextColor1 = '#20a052'
                    this.percentBackgroundColor = '#d8e4bc'
                    this.percentBackgroundColor1 = '#d8e4bc'
                }
            },
            stake_calc(val){
                this.calc_stake = 100;
                if(this.calc_odd != 0 && this.calc_stake != 0 && this.eventId != 0){
                    if(parseInt(this.selectedArray[6]) == 0){
                        this.max_profit = (this.calc_odd * this.calc_stake - this.calc_stake).toFixed(2)
                        this.max_lose = this.calc_stake
                        this.guad_max = this.max_profit
                        if(this.lay == '' || this.lay == 0){
                            this.guad_att = 0
                        }
                        else{
                            this.guad_att = (this.calc_odd * this.calc_stake/parseFloat(this.lay) -  this.calc_stake).toFixed(2)
                        }

                        if(this.guad_att > 0){
                            this.guad_att = this.guad_att * (100 - this.bookmarkerFee)/100
                        }

                        if(this.guad_max != 0){
                            if(this.guad_att >= 0){
                                this.currentPercent = (100*this.guad_att/this.guad_max).toFixed(2)
                            }
                            else{
                                this.currentPercent = (100*this.guad_att/this.calc_stake).toFixed(2)
                            }
                        }
                        else{
                            this.currentPercent = 0
                        }
                        if(this.currentPercent > 0){
                            this.percentTextColor = '#20a052'
                            this.percentTextColor1 = '#20a052'
                            this.percentBackgroundColor = '#d8e4bc'
                            this.percentBackgroundColor1 = '#d8e4bc'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG =='' ){
                                MG = '0'
                            }
                            if(this.riskTrading == 'easy'){
                                if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].facile.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].facile.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].facile.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].facile.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'medium'){
                                if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].medio.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].medio.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].medio.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].medio.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'risky'){
                                if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == false && this.tradingMode == false && this.currentPercent > this.adminTable[0].elevato.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == false && this.currentPercent > this.adminTable[0].elevato.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent > this.adminTable[0].elevato.GN){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent > this.adminTable[0].elevato.GT){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }

                        }
                        else if(this.currentPercent < 0){
                            this.percentTextColor = '#b80101'
                            this.percentTextColor1 = '#b80101'
                            this.percentBackgroundColor = '#ffc7ce'
                            this.percentBackgroundColor1 = '#ffc7ce'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG == ''){
                                MG = '0'
                            }

                            if(this.riskTrading == 'easy'){
                                if(parseInt(MG) > this.adminTable[0].facile.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent < this.adminTable[0].facile.SLN * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].facile.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent < this.adminTable[0].facile.SLT * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'medium'){
                                if(parseInt(MG) > this.adminTable[0].medio.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent < this.adminTable[0].medio.SLN * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].medio.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent < this.adminTable[0].medio.SLT * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }
                            else if(this.riskTrading == 'risky'){
                                if(parseInt(MG) > this.adminTable[0].elevato.MG && this.stopLoss == true && this.tradingMode == false && this.currentPercent < this.adminTable[0].elevato.SLN * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                                else if(parseInt(MG) > this.adminTable[0].elevato.MG && this.tradingMode == true && this.stopLoss == true && this.currentPercent < this.adminTable[0].elevato.SLT * (-1)){
                                    this.percentTextColor1 = '#000'
                                    this.percentBackgroundColor = '#ffc000'
                                    this.percent_text1 = 'Cash Out Now! '
                                }
                            }

                        }

                    }
                    else{
                        this.max_lose = (this.calc_odd * this.calc_stake - this.calc_stake).toFixed(2)
                        this.max_profit = this.calc_stake
                        this.guad_max = this.calc_stake
                        if(this.back == '' || this.back == 0){
                            this.guad_att = 0
                        }
                        else{
                            this.guad_att = ( this.calc_stake - this.calc_odd * this.calc_stake/parseFloat(this.back)).toFixed(2)
                        }

                        if(this.guad_att > 0){
                            this.guad_att = this.guad_att * (100 - this.bookmarkerFee)/100
                        }

                        if(this.guad_max != 0){
                            if(this.guad_att >= 0){
                                this.currentPercent = (100*this.guad_att/this.guad_max).toFixed(2)
                            }
                            else{
                                this.currentPercent = (100*this.guad_att/(this.calc_odd * this.calc_stake - this.calc_stake)).toFixed(2)
                            }
                        }
                        else{
                            this.currentPercent = 0
                        }
                        if(this.currentPercent > 0){
                            this.percentTextColor = '#20a052'
                            this.percentTextColor1 = '#20a052'
                            this.percentBackgroundColor = '#d8e4bc'
                            this.percentBackgroundColor1 = '#d8e4bc'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG =='' ){
                                MG = '0'
                            }
                        }
                        else if(this.currentPercent < 0){
                            this.percentTextColor = '#b80101'
                            this.percentTextColor1 = '#b80101'
                            this.percentBackgroundColor = '#ffc7ce'
                            this.percentBackgroundColor1 = '#ffc7ce'
                            this.percent_text1 = 'Current Profit:'
                            this.percent_text2 = this.currentPercent.toString() + '%'

                            let timeRecord = this.timeRecord
                            let MG = timeRecord.substring(0, timeRecord.length)

                            if(MG =='' ){
                                MG = '0'
                            }
                        }
                    }
                }
                else{
                    this.max_profit = 0
                    this.max_lose = 0
                    this.guad_max = 0
                    this.percent_text1 =
                        this.percent_text2 = 'Insert Odd and Stake'
                    this.guad_att = 0
                    this.percentTextColor = '#20a052'
                    this.percentTextColor1 = '#20a052'
                    this.percentBackgroundColor = '#d8e4bc'
                    this.percentBackgroundColor1 = '#d8e4bc'
                }
            },
        },
        watch: {
            eventLists3(Lists) {
                this.eventListsLength = Lists.length - 1;
                this.tableFields = [
                    { key: 'match', label:  `Match (${this.eventListsLength})`, _classes: 'table-warning'},
                    { key: 'tot', label:  'Tot. Matched', _classes: 'table-warning'},
                    { key: 'preodd', label:  'Pre Odd', _classes: 'table-warning'},
                    { key: 'odd', label:  'Odd', _classes: 'table-warning'},
                    { key: 'back', label:  'Back', _classes: 'table-info'},
                    { key: 'lay', label:  'Lay', _classes: 'table-danger'},
                    { key: 'status', label:  'Status', _classes: 'table-warning'},
                    { key: 'minute', label:  'Minute', _classes: 'table-warning'},
                    { key: 'score', label:  'Score', _classes: 'table-warning'},
                    { key: 'gain', label:  'Gain/Losses%', _classes: 'table-warning'}
                ]
                for (let i=0; i<this.eventListsLength; i++) {
                    this.tableItems.push(
                        {
                            tot: {value: null},
                            preodd: {value: null},
                            odd: {value: null},
                            back: {value: null},
                            lay: {value: null},
                            status: {value: null},
                            minute: {value: null},
                            score: {value: null},
                            gain: {value: null},
                        }
                    )
                }
            },
            eventFlag(event) {
                if (this.eventListsLength == 0) {
                    return
                }
                if (this.clickEventValue == 'all') {
                    this.all = true;
                    this.eventLists3.forEach((element, index) => {
                        if (element.value)
                            this.updateItem(element.value, index-1);
                    });
                } else if (this.clickEventValue == 'clear') {
                    this.marketIds = []
                    this.all = false;
                    for (let event of this.eventLists3) {
                        for (const item of this.tableItems) {
                            item.tot.value = '';
                            item.preodd.value = '';
                            item.back.value = '';
                            item.lay.value = '';
                            item.status.value = '';
                            item.minute.value = '';
                            item.score.value = '';
                            if (this.percent_text1) {
                                item.gain.value = '';
                            } else if (this.percent_text2) {
                                item.gain.value = '';
                            }
                        }
                    }
                } else {
                    console.log(this.tableItems);
                    this.all = false;
                    for (let event of this.eventLists3) {
                        for (const item of this.tableItems) {
                            item.tot.value = '';
                            item.preodd.value = '';
                            item.back.value = '';
                            item.lay.value = '';
                            item.status.value = '';
                            item.minute.value = '';
                            item.score.value = '';
                            if (this.percent_text1) {
                                item.gain.value = '';
                            } else if (this.percent_text2) {
                                item.gain.value = '';
                            }
                        }
                    }
                }
            }
        },
        created() {
            let self = this
            this.sockets.listener.subscribe('UpdateOdds', (data) => {
                this.marketIds.forEach(element => {
                    for (let i = 0; i < data.length; i++) {
                        if(element.market == data[i].marketId){
                            self.odd_calc(this.calc_odd)
                            let selections = data[i].runners;
                            if(data[i].state.status == 'SUSPENDED'){
                                this.marketStatus = 'SUSPENDED'
                            }
                            else if(data[i].state.status == "CLOSED"){
                                this.marketStatus = 'CLOSED'
                            }
                            else if(data[i].state.status == "OPEN"){
                                this.marketStatus =''
                            }
                            if(selections[0].exchange.availableToBack){
                                self.back = selections[0].exchange.availableToBack[0].price ||''
                                self.back_matched = selections[0].exchange.availableToBack[0].size || 0
                            }
                            else{
                                self.back =''
                                self.back_matched = 0
                            }

                            if(selections[0].exchange.availableToLay){
                                self.lay = selections[0].exchange.availableToLay[0].price ||''
                                self.lay_matched = selections[0].exchange.availableToLay[0].size || 0
                            }
                            else{
                                self.lay =''
                                self.lay_matched = 0
                            }
                            self.total_matched = (data[i].state.totalMatched).toFixed(1);

                            this.tableItems[element.index].tot.value = self.total_matched;
                            this.tableItems[element.index].back.value = self.back;
                            this.tableItems[element.index].lay.value = self.lay;
                        }
                    }
                });
            });
            
            this.sockets.listener.subscribe('UpdateScore', (data) => {

                for(let i = 0 ; i < self.mainList.length ; i++){
                    if(self.mainList[i].eventId == data.eventId){
                        self.mainList[i].inPlayMatchStatus = data.inPlayMatchStatus
                        self.mainList[i].score = data.score
                        self.mainList[i].timeElapsed = data.timeElapsed
                        self.mainList[i].status = data.status
                        self.mainList[i].updateDetails = data.updateDetails
                        if(data.status == 'IN_PLAY'){
                            for(let j = 0; j < this.eventLists.length; j++){
                                let value = this.eventLists[j].value
                                let liveArray = value.split(',')
                                if(data.eventId == liveArray[0]){
                                    let str = this.eventLists[j].label
                                    if(str.includes(' - Live') == false){
                                        this.eventLists[j].label = this.eventLists[j].label + ' - Live'
                                    }
                                }
                                if(data.eventId == liveArray[1]){
                                    let str = this.eventLists[j].label
                                    if(str.includes(' - Live') == false){
                                        this.eventLists[j].label = this.eventLists[j].label + ' - Live'
                                    }
                                }
                            }
                        }
                        else{
                            for(let j = 0; j < this.eventLists.length; j++){
                                let value = this.eventLists[j].value
                                let liveArray = value.split(',')
                                if(data.eventId == liveArray[0]){
                                    let str = this.eventLists[j].label
                                    if(str.includes(' - Live') == true){
                                        this.eventLists[j].label.replace(' - Live', )
                                    }
                                }
                            }
                            for(let j = 0; j < this.eventLists.length; j++){
                                let value = this.eventLists[j].value
                                let liveArray = value.split(',')
                                if(data.eventId == liveArray[1]){
                                    let str = this.eventLists[j].label
                                    if(str.includes(' - Live') == true){
                                        this.eventLists[j].label.replace(' - Live', )
                                    }
                                }
                            }
                        }
                    }
                }

                if(self.eventId ==  data.eventId){
                    self.timeRecord = data.timeElapsed
                    self.status = data.status
                    if(data.status == 'IN_PLAY'){
                        self.status = 'Live - '
                        this.scoreOne = data.score.home.score + " -"
                        this.scoreTwo = data.score.away.score
                        this.timeRecord = data.timeElapsed+ "'"
                    }
                    else if(!data.status){
                        self.status = 'Coming Up'
                        this.scoreOne =''
                        this.scoreTwo =''
                        this.timeRecord =''
                    }
                    if(data.inPlayMatchStatus == 'FirstHalfEnd'){
                        this.timeRecord = "HT"
                    }
                }
            });
        }
    }
</script>

<style scoped>
    .form-group {
        margin-bottom: 0px;
    }
</style>