<template>
    <div>
        <CCard>
            <CCardHeader>
                <CRow>
                    <CCol xs="12" sm="6" md="6" class="dashboard-logo-wrapper">
                        <label class="dashboard-logo">Dashboard</label>
                    </CCol>
                </CRow>
                <CRow class="mt-3">
                    <CCol xs="12" sm="12" md="5">
                        <div class="filter-container">
                            <label class="sub-title">
                                General Filters:
                            </label>
                            <div class="checkbox-group">
                                <div class="checkbox-sub-group">
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter1"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            1
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter2"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            x
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter3"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            2
                                        </template>
                                    </CInputCheckbox>
                                </div>
                                <div class="checkbox-sub-group">
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter4"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            O 0.5
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter5"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            O 1.5
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter6"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            O 2.5
                                        </template>
                                    </CInputCheckbox>
                                </div>
                                <div class="checkbox-sub-group">
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter7"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            U 2.5
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter8"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            U 3.5
                                        </template>
                                    </CInputCheckbox>
                                </div>
                                <div style="width: 25%; flex: 1; ">
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter9"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            Back
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter10"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            Lay
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter11"
                                    >
                                        <template #label>
                                            Double Tips
                                        </template>
                                    </CInputCheckbox>
                                </div>
                                <div style="width: 15%; flex: 1;">
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter12"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            Cup
                                        </template>
                                    </CInputCheckbox>
                                    <CInputCheckbox class="check-box"
                                                    @update:checked="select_filter13"
                                                    :checked = "true"
                                    >
                                        <template #label>
                                            Week
                                        </template>
                                    </CInputCheckbox>
                                </div>
                            </div>
                        </div>
                    </CCol>
                    <CCol xs="12" sm="8" md="4">
                        <div class="filter-wrapper">
                            <label class="sub-title">Odd Filters:</label>
                            <div class="odd-filter">
                                <label>min:</label>
                                <CInput type="number" :value="this.oddMin" @update:value="odd_min" class="odd-filter-inputbox"></CInput>
                                <label>max:</label>
                                <CInput type="number" :value="this.oddMax" @update:value="odd_max" class="odd-filter-inputbox"></CInput>
                            </div>
                            <label class="sub-title mt-2">Matched Filters:</label>
                            <div class="matched-filter">
                                <label>min:</label>
                                <CInput type="number" :value="this.matchedMin" @update:value="matched_min" class="odd-filter-inputbox"></CInput>
                                <label>max:</label>
                                <CInput type="number" :value="this.matchedMax" @update:value="matched_max" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </CCol>
                    <CCol xs="12" sm="4" md="3">
                        <CButton color="success">Refresh</CButton>
                        <CButton color="success">Clear</CButton>
                    </CCol>
                </CROW>
            </CCardHeader>
            <CCardBody>
                <CRow>
                    <CCol md="12">
                        <DashboardTable></DashboardTable>
                    </CCol>
                </CRow>
            </CCardBody>
        </CCard>
    </div>
</template>

<script>

    import DashboardTable from "./../../../components/DashboardTable";

    export default {
        name: 'NavDashboard',
        components: {
            DashboardTable
        },
        data () {
            return {
                eventLists: [],
                filterQuery: ['- 1 -','- X -','- 2 -','- Over 0.5','- Over 1.5','- Over 2.5','- Under 2.5','- Under 3.5'],
                predictionStatus: true
            }
        },
        methods: {
            // Filter
            select_filter1(val){
                console.log('ok: ', this.eventLists);
                if(val == true){
                    this.filterQuery.push('- 1 -')
                }
                else{
                    let index = this.filterQuery.indexOf('- 1 -');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter2(val){
                if(val == true){
                    this.filterQuery.push('- X -')
                }
                else{
                    let index = this.filterQuery.indexOf('- X -');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter3(val){
                if(val == true){
                    this.filterQuery.push('- 2 -')
                }
                else{
                    let index = this.filterQuery.indexOf('- 2 -');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter4(val){
                if(val ==  true){
                    this.filterQuery.push('- Over 0.5')
                }
                else{
                    let index = this.filterQuery.indexOf('- Over 0.5');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter5(val){
                if(val == true){
                    this.filterQuery.push('- Over 1.5')
                }
                else{
                    let index = this.filterQuery.indexOf('- Over 1.5');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter6(val){
                if(val == true){
                    this.filterQuery.push('- Over 2.5')
                }
                else{
                    let index = this.filterQuery.indexOf('- Over 2.5');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter7(val){
                if(val == true){
                    this.filterQuery.push('- Under 2.5')
                }
                else{
                    let index = this.filterQuery.indexOf('- Under 2.5');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter8(val){
                if(val ==  true){
                    this.filterQuery.push('- Under 3.5')
                }
                else{
                    let index = this.filterQuery.indexOf('- Under 3.5');
                    if (index > -1) {
                        this.filterQuery.splice(index, 1);
                    }
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter9(val){
                if(val == true){
                    this.backFilter = true
                }
                else{
                    this.backFilter = false
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter10(val){
                if(val == true){
                    this.layFilter = true
                }
                else{
                    this.layFilter = false
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter11(val){
                if(val == true){
                    this.doubleTips = true
                }
                else{
                    this.doubleTips = false
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter12(val){
                if(val == true){
                    this.cupFilter = true
                }
                else{
                    this.cupFilter = false
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            select_filter13(val){
                if(val == true){
                    this.weekFilter = true
                }
                else{
                    this.weekFilter = false
                }
                if(this.predictionStatus ==  true){
                    this.filter1(this.filterQuery)
                }
            },
            filter1(filterArray){
                this.predictionList = []
                this.predictionList[0] = {'value': '', 'label': 'Select Match'}
                if(filterArray.length < 1){
                    this.eventLists = this.predictionList
                    return
                }
                else{
                    for(let j = 1 ; j < this.predictionList.length; j++){
                        let prediction = this.predictionList[j].label.toString()
                        let value = this.predictionList[j].value
                        for(let i = 0 ; i < filterArray.length; i++){
                            if(filterArray[i] == '- 1 -'){
                                if(prediction.includes('- 1 -') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- X -'){
                                if(prediction.includes('- X -') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- 2 -'){
                                if(prediction.includes('- 2 -') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- Over 0.5'){
                                if(prediction.includes('- Over 0.5') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- Over 1.5'){
                                if(prediction.includes('- Over 1.5') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- Over 2.5'){
                                if(prediction.includes('- Over 2.5') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- Under 2.5'){
                                if(prediction.includes('- Under 2.5') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                            else if(filterArray[i] == '- Under 3.5'){
                                if(prediction.includes('- Under 3.5') == true){
                                    this.predictionList.push({'value': value, 'label':prediction})
                                }
                            }
                        }
                    }
                    if(this.backFilter == false){
                        let predictions =this.predictionList.filter(function(item) {
                            return !item.label.includes('Back');
                        });
                        this.predictionList = predictions
                    }
                    if(this.layFilter == false){
                        let predictions =this.predictionList.filter(function(item) {
                            return !item.label.includes('Lay');
                        });
                        this.predictionList = predictions
                    }
                    //---------excluded filter-------------
                    for(let i = 0; i < this.predictionList.length ; i++){
                        console.log(this.predictionList[i])
                        if(this.predictionList[i].value.split(',')[2] != 'MATCH_ODDS'){
                            let self = this
                            let predictions =this.predictionList.filter(function(item) {
                                return item.value.split(',')[1] == self.predictionList[i].value.split(',')[1] && item.value.split(',')[2] == self.predictionList[i].value.split(',')[2];
                            });
                            if(predictions.length > 1){
                                for(let j = 0 ; j < predictions.length; j++){
                                    let index = this.predictionList.indexOf(predictions[j]);
                                    if (index > -1) {
                                        i = i - 1
                                        this.predictionList.splice(index, 1);
                                    }
                                }
                            }
                            let predictions1 =this.predictionList.filter(function(item) {
                                return item.value.split(',')[1] == self.predictionList[i].value.split(',')[1] && self.predictionList[i].value.split(',')[2] != 'MATCH_ODDS';
                            });
                            let pp = 0
                            let pp1 = 0
                            for(let j = 0 ; j < predictions1.length ; j++){
                                if(predictions1[j].value.split(',')[2] == 'OVER_UNDER_35' && predictions1[j].value.split(',')[3] == '0'){
                                    pp = 1
                                }
                                if(predictions1[j].value.split(',')[2] == 'OVER_UNDER_25' && predictions1[j].value.split(',')[3] == '1'){
                                    pp1 = 1
                                }
                            }
                            if(pp == 1 && pp1 == 1){
                                for(let j = 0 ; j < predictions1.length ; j++) {
                                    if(predictions1[j].value.split(',')[2] == 'OVER_UNDER_25' || predictions1[j].value.split(',')[2] == 'OVER_UNDER_35'){
                                        let index = this.predictionList.indexOf(predictions1[j]);
                                        if (index > -1) {
                                            i = i - 1
                                            this.predictionList.splice(index, 1);
                                        }
                                    }
                                }
                                console.log('predictions1=>', predictions1)
                            }
                        }
                        else{
                            let self = this
                            let predictions =this.predictionList.filter(function(item) {
                                return item.value.split(',')[1] == self.predictionList[i].value.split(',')[1] && item.value.split(',')[2] == self.predictionList[i].value.split(',')[2];
                            });
                            if(predictions.length > 1){
                                console.log('excluded check===>', predictions)
                                let check001 = 0
                                let check002 = 0
                                let check003 = 0
                                let check004 = 0
                                for(let c = 0 ; c < predictions.length ; c++){
                                    if(predictions[c].label.includes('1 - Lay')){
                                        check001 = 1
                                    }
                                    if(predictions[c].label.includes('2 - Lay')){
                                        check002 = 1
                                    }
                                    if(predictions[c].label.includes('X - Back')){
                                        check003 = 1
                                    }
                                    if(predictions[c].label.includes('X - Lay')){
                                        check004 = 1
                                    }
                                }
                                if((check001 === 1 && check002 === 1) || ((check003 === 1) && (check001 === 1 || check002 === 1)) || (check003 === 1 && check004 === 1)){
                                    for(let j = 0 ; j < predictions.length; j++){
                                        console.log('predictions===>',predictions[j])
                                        let index = this.predictionList.indexOf(predictions[j]);
                                        if (index > -1) {
                                            i = i - 1
                                            this.predictionList.splice(index, 1);
                                        }
                                    }
                                }
                            }
                        }
                    }
                    //-------------------------------------
                    if(this.cupFilter == false){
                        for(let i = 1 ; i < this.predictionList.length; i++){
                            let p_value = this.predictionList[i].value
                            let com_label = p_value.split(',')
                            let com_eventId =  com_label[1]
                            let competition = this.competitionList.filter(function(item) {
                                return item.eventId == com_eventId;
                            });
                            let competitionLabel = competition[0].competitions[0].name
                            let check = 0
                            for(let k = 0; k < this.cupList.length; k++){
                                if(competitionLabel.includes(this.cupList[k]) == true){
                                    check = 1
                                }
                            }
                            if(check == 1){
                                let index = this.predictionList.indexOf(this.predictionList[i]);
                                if (index > -1) {
                                    i = i - 1
                                    this.predictionList.splice(index, 1);
                                }
                            }
                        }
                    }
                    if(this.weekFilter ==  false){
                        console.log('prediction_list_check===>',this.predictionList)
                        // let predictions =this.predictionList.filter(function(item) {
                        //     return parseInt(item.value.split(',')[5]) > parseInt(item.value.split(',')[4]);
                        // });
                        for(let n = 1 ; n < this.predictionList.length ; n++){
                            let p_val = this.predictionList[n].value.split(',')[7].trim()
                            let val1 = parseInt(this.predictionList[n].value.split(',')[4])
                            let val2 = parseInt(this.predictionList[n].value.split(',')[5])
                            console.log('value is just these =>', p_val, val1, val2)
                            if(p_val == 'Perde da' || p_val == 'Perde in casa da' || p_val == 'Pareggia fuori da'){
                                console.log('value is just these =>', p_val)
                                let index = this.predictionList.indexOf(this.predictionList[n]);
                                if (index > -1) {
                                    n = n - 1
                                    this.predictionList.splice(index, 1);
                                }
                            }
                            else if(p_val != 'Non vince da' && p_val != 'Non pareggia da' && p_val != 'Non perde da' && p_val != 'Non perde in casa da' && p_val != 'Non vince fuori da' && p_val != 'Non pareggia fuori da'){
                                if(val1 > val2){
                                    let index = this.predictionList.indexOf(this.predictionList[n]);
                                    if (index > -1) {
                                        n = n - 1
                                        this.predictionList.splice(index, 1);
                                    }
                                }
                            }
                            else{
                                console.log(this.predictionList)
                            }
                        }
                    }
                    if(this.doubleTips ==  false){
                        let eventArray = []
                        for(let d = 0 ; d < this.predictionList.length; d++){
                            eventArray[d] = this.predictionList[d].value.split(',')[1]
                        }
                        eventArray = Array.from(new Set (eventArray))
                        for(let d = 0 ; d < eventArray.length; d++){
                            let predictions = this.predictionList.filter(function(item) {
                                return item.value.split(',')[1] == eventArray[d] && item.value.split(',')[2] == 'MATCH_ODDS';
                            });
                            if(predictions.length > 1){
                                let predictions1 = predictions.filter(function(item) {
                                    return item.value.split(',')[3] == '2';
                                });
                                if(predictions1.length > 0){
                                    for(let g = 0 ; g < predictions.length ; g++){
                                        if(predictions[g].value.split(',')[3] != '2'){
                                            let index = this.predictionList.indexOf(predictions[g]);
                                            if (index > -1) {
                                                g = g - 1
                                                this.predictionList.splice(index, 1);
                                            }
                                        }
                                    }
                                }
                                if(predictions.length > 1){
                                    let predictions1 = predictions.filter(function(item) {
                                        return item.value.split(',')[3] == '2' && item.value.split(',')[6] == '0';
                                    });
                                    if(predictions1.length > 0){
                                        for(let g = 0 ; g < predictions.length ; g++){
                                            if(predictions[g].label.includes('1 - Lay') == true || predictions[g].label.includes('2 - Lay') == true){
                                                let index = this.predictionList.indexOf(predictions[g]);
                                                if (index > -1) {
                                                    g = g - 1
                                                    this.predictionList.splice(index, 1);
                                                }
                                            }
                                        }
                                        let index = this.predictionList.indexOf(predictions1[0]);
                                        if (index > -1) {
                                            this.predictionList.splice(index, 1);
                                        }
                                    }
                                }
                            }
                        }
                    }
                    if(this.doubleTips ==  true){
                        let eventArray = []
                        for(let d = 0 ; d < this.predictionList.length; d++){
                            eventArray[d] = this.predictionList[d].value.split(',')[1]
                        }
                        eventArray = Array.from(new Set (eventArray))
                        for(let d = 0 ; d < eventArray.length; d++){
                            let predictions = this.predictionList.filter(function(item) {
                                return item.value.split(',')[1] == eventArray[d] && item.value.split(',')[2] == 'MATCH_ODDS';
                            });
                            if(predictions.length > 1){
                                let predictions1 = predictions.filter(function(item) {
                                    return item.value.split(',')[3] == '2' && item.value.split(',')[6] == '0';
                                });
                                if(predictions1.length > 0){
                                    for(let g = 0 ; g < predictions.length ; g++){
                                        if(predictions[g].label.includes('1 - Lay') == true || predictions[g].label.includes('2 - Lay') == true){
                                            let index = this.predictionList.indexOf(predictions[g]);
                                            if (index > -1) {
                                                g = g - 1
                                                this.predictionList.splice(index, 1);
                                            }
                                        }
                                    }
                                    let index = this.predictionList.indexOf(predictions1[0]);
                                    if (index > -1) {
                                        this.predictionList.splice(index, 1);
                                    }
                                }
                            }
                        }
                    }
                    if(this.predictionStatus == true){
                        //-----------------------total_matched_money--------------------------
                        for(let p = 1; p < this.predictionList.length; p++){
                            let eventId = this.predictionList[p].value.split(',')[1]
                            let marketType = this.predictionList[p].value.split(',')[2]
                            let eventNode = this.mainList.filter(function(item) {
                                return item.eventId == eventId;
                            });
                            let marketNode = eventNode[0].markets.filter(function(item) {
                                return item.marketType == marketType;
                            });
                            console.log('marketNode===>', marketNode, marketType)
                            if(marketNode.length > 0){
                                if(marketNode[0].totalMatched < this.matchedMin || marketNode[0].totalMatched > this.matchedMax){
                                    let index = this.predictionList.indexOf(this.predictionList[p]);
                                    if (index > -1) {
                                        p = p - 1
                                        this.predictionList.splice(index, 1);
                                    }
                                }
                            }
                            else{
                                // let index = this.predictionList.indexOf(this.predictionList[p]);
                                // if (index > -1) {
                                //     p = p - 1
                                //     this.predictionList.splice(index, 1);
                                // }
                            }
                        }
                        //---------------------------odd_filter----------------------------
                        for(let p = 1 ; p < this.predictionList.length; p++){
                            let eventId = this.predictionList[p].value.split(',')[1]
                            let marketType = this.predictionList[p].value.split(',')[2]
                            let marketNo = parseInt(this.predictionList[p].value.split(',')[3])
                            let runnerNo = parseInt(this.predictionList[p].value.split(',')[6])
                            let predictionLabel = this.predictionList[p].label
                            let eventNode = this.mainList.filter(function(item) {
                                return item.eventId == eventId;
                            });
                            let marketNode = eventNode[0].markets.filter(function(item) {
                                return item.marketType == marketType;
                            });
                            console.log('marketNode===>', marketNode[0])
                            if(marketNode[0]){
                                if(!marketNode[0].runners){
                                    return
                                }
                                if(predictionLabel.includes(' - Live') == true){
                                    for(let h = 0  ; h < this.prematchOddList.length ;  h++){
                                        if(this.prematchOddList[h].marketId == marketNode[0].marketId){
                                            console.log('great!!', marketNode[0].marketId)
                                            if(this.prematchOddList[h].runners[marketNo].exchange){
                                                if(runnerNo == '0'){
                                                    if(this.prematchOddList[h].runners[marketNo].exchange.availableToBack){
                                                        let backOdds = parseFloat(this.prematchOddList[h].runners[marketNo].exchange.availableToBack[0].price)
                                                        if(this.marketId == marketNode[0].marketId){
                                                            this.prematchOdd = backOdds
                                                        }
                                                        if(backOdds < parseFloat(this.oddMin) || backOdds > parseFloat(this.oddMax)){
                                                            let index = this.predictionList.indexOf(this.predictionList[p]);
                                                            if (index > -1) {
                                                                p = p - 1
                                                                this.predictionList.splice(index, 1);
                                                            }
                                                        }
                                                    }
                                                }
                                                else {
                                                    if(this.prematchOddList[h].runners[marketNo].exchange.availableToLay){
                                                        let layOdds = parseFloat(this.prematchOddList[h].runners[marketNo].exchange.availableToLay[0].price)
                                                        if(this.marketId == marketNode[0].marketId){
                                                            this.prematchOdd = layOdds
                                                        }
                                                        if(layOdds < parseFloat(this.oddMin) || layOdds > parseFloat(this.oddMax)){
                                                            let index = this.predictionList.indexOf(this.predictionList[p]);
                                                            if (index > -1) {
                                                                p = p - 1
                                                                this.predictionList.splice(index, 1);
                                                            }
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                                else{
                                    if(marketNode[0].runners[marketNo].exchange){
                                        if(runnerNo == '0'){
                                            if(marketNode[0].runners[marketNo].exchange.availableToBack){
                                                let backOdds = parseFloat(marketNode[0].runners[marketNo].exchange.availableToBack[0].price)
                                                if(backOdds < parseFloat(this.oddMin) || backOdds > parseFloat(this.oddMax)){
                                                    let index = this.predictionList.indexOf(this.predictionList[p]);
                                                    if (index > -1) {
                                                        p = p - 1
                                                        this.predictionList.splice(index, 1);
                                                    }
                                                }
                                            }
                                        }
                                        else {
                                            if(marketNode[0].runners[marketNo].exchange.availableToLay){
                                                let layOdds = parseFloat(marketNode[0].runners[marketNo].exchange.availableToLay[0].price)
                                                if(layOdds < parseFloat(this.oddMin) || layOdds > parseFloat(this.oddMax)){
                                                    let index = this.predictionList.indexOf(this.predictionList[p]);
                                                    if (index > -1) {
                                                        p = p - 1
                                                        this.predictionList.splice(index, 1);
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                            else{
                                let index = this.predictionList.indexOf(this.predictionList[p]);
                                if (index > -1) {
                                    p = p - 1
                                    this.predictionList.splice(index, 1);
                                }
                            }
                        }
                        let checkSelect = 0;
                        for(let s = 0 ; s < this.predictionList.length ; s++){
                            if(this.predictionList[s].value == this.selectedValue){
                                checkSelect = 1
                            }
                        }
                        if(checkSelect == 0){
                            this.eventId = 0
                            this.marketId =
                                this.selectionId = 0
                            this.lay =
                                this.lay_matched = 0
                            this.back =
                                this.back_matched = 0
                            this.total_matched = 0
                            this.status =
                                this.scoreOne =
                                    this.scoreTwo =
                                        this.timeRecord =
                                            this.key1 = 0
                        }
                        this.eventLists = this.predictionList
                    }
                }
                console.log(this.eventLists);
            },
            odd_min(val){
                this.oddMin = val
                // if(this.predictionStatus == true){
                this.filter1(this.filterQuery)
                // }
            },
            odd_max(val){
                this.oddMax = val
                // if(this.predictionStatus == true){
                this.filter1(this.filterQuery)
                // }
            },
            matched_min(val){
                this.matchedMin = val
                // if(this.predictionStatus == true){
                this.filter1(this.filterQuery)
                // }
            },
            matched_max(val){
                this.matchedMin = val
                // if(this.predictionStatus == true){
                this.filter1(this.filterQuery)
                // }
            }
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
