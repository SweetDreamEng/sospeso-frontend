<template>
    <div class="live-stats-container">
        <CRow>
            <CCol lg="6" style="height: 180px; background: white; padding: 20px 30px;">
                <label style="color: red; font-weight: bold;">Date:</label>
                <div class="from_date" style="height: 40px; width: 100%;">
                    <div style="flex: 1; padding-top: 1px; padding-right: 10px;">From:</div>
                    <div style="flex: 4; padding-right: 35px;">
<!--                        <CInput type="text"  :value="this.from_date" @update:value="from_date_f" class="odd-filter-inputbox" placeholder="2000-01-01"></CInput>-->
                        <CSelect
                                class="fromdate"
                                :options="dateList1"
                                @update:value="from_date_f"
                        >
                        </CSelect>
                    </div>
                    <div style="flex: 1; padding-top: 1px; padding-right: 10px;">End:</div>
                    <div style="flex: 4; padding-right: 35px;">
<!--                        <CInput type="text"  :value="this.end_date" @update:value="end_date_f" class="odd-filter-inputbox" placeholder="2000-01-01"></CInput>-->
                        <CSelect
                                class="fromdate"
                                :options="dateList2"
                                @update:value="end_date_f"
                        >
                        </CSelect>
                    </div>
                    <div style="width: 40%; float: left;">
                        <CButton color="success" @click="getLiveData" class="G-L-button">
                            Get Data
                        </CButton>
                    </div>
                </div>

                <div class="from_date" style="padding-right: 35px;">
                    <label style="flex: 1; color: red; font-weight: bold;">League:</label>
                    <div style="flex: 4;">
                        <CSelect
                                class="league-list"
                                :options="leagues"
                                @update:value="set_league"
                        >
                        </CSelect>
                    </div>
                </div>

                 <div class="from_date" style="padding-right: 35px;">
                    <label style="flex: 2; color: red; font-weight: bold;">Minute:</label>
                    <div style="flex: 2; text-align: right; padding-top: 1px; padding-right: 10px;">From:</div>
                    <div style="flex: 3;">
                        <CInput type="text"  :value="this.min_minute" @update:value="min_minute_f" class="odd-filter-inputbox"></CInput>
                    </div>
                    <div style="flex: 2; text-align: right; padding-top: 1px; padding-right: 10px;">End:</div>
                    <div style="flex: 3;">
                        <CInput type="text"  :value="this.max_minute" @update:value="max_minute_f" class="odd-filter-inputbox"></CInput>
                    </div>
                </div>
            </CCol>
            <CCol lg="6" style="height: 180px; background: white; padding: 20px 30px;">
                <label style="color: red; font-weight: bold;">Events List</label>
                <CSelect
                        class="event-list"
                        :options="eventList"
                        @update:value="set_event"
                >
                </CSelect>
            </CCol>
            <CCol lg="6" class="stats-filter-content" style="height: 600px; background: white; padding: 20px 30px;">
                <div style="width: 50%; float: left; padding-right: 20px;">
                    <label style="color: red; font-weight: bold;">Home Team:</label>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Rank</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"  :value="homeTeam.rank.from" @update:value="h_rank_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.rank.to" @update:value="h_rank_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">On</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.on.from" @update:value="h_on_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.on.to" @update:value="h_on_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Off</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.off.from" @update:value="h_off_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.off.to" @update:value="h_off_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Blk</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.blk.from" @update:value="h_blk_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.blk.to" @update:value="h_blk_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">In</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.in.from" @update:value="h_in_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.in.to" @update:value="h_in_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Out</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.out.from" @update:value="h_out_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.out.to" @update:value="h_out_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Cnr</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.cnr.from" @update:value="h_cnr_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.cnr.to" @update:value="h_cnr_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">DA</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.da.from" @update:value="h_da_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.da.to" @update:value="h_da_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Pos</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="homeTeam.pos.from" @update:value="h_pos_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0" :value="homeTeam.pos.to" @update:value="h_pos_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Red</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0" :value="homeTeam.red.from" @update:value="h_red_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0" :value="homeTeam.red.to" @update:value="h_red_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Yel</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.yel.from" @update:value="h_yel_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.yel.to" @update:value="h_yel_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Goal</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.goal.from" @update:value="h_goal_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="homeTeam.goal.to" @update:value="h_goal_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                </div>
                <div style="width: 50%; float: left; padding-left: 20px;">
                    <label style="color: red; font-weight: bold;">Away Team:</label>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Rank</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.rank.from" @update:value="a_rank_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.rank.to" @update:value="a_rank_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">On</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.on.from" @update:value="a_on_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.on.to" @update:value="a_on_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Off</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.off.from" @update:value="a_off_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.off.to" @update:value="a_off_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Blk</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0"   :value="awayTeam.blk.from" @update:value="a_blk_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.blk.to" @update:value="a_blk_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">In</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.in.from" @update:value="a_in_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.in.to" @update:value="a_in_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Out</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.out.from" @update:value="a_out_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.out.to" @update:value="a_out_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Cnr</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.cnr.from" @update:value="a_cnr_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number" min="0" :value="awayTeam.cnr.to" @update:value="a_cnr_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">DA</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.da.from" @update:value="a_da_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0"  :value="awayTeam.da.to" @update:value="a_da_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style = "background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Pos</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style = "width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type = "number"  min="0" :value="awayTeam.pos.from" @update:value="a_pos_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style = "width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style = "width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.pos.to" @update:value="a_pos_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Red</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.red.from" @update:value="a_red_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.red.to" @update:value="a_red_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Yel</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.yel.from" @update:value="a_yel_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.yel.to" @update:value="a_yel_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Goal</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.goal.from" @update:value="a_goal_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  min="0" :value="awayTeam.goal.to" @update:value="a_goal_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                </div>
            </CCol>
            <CCol lg="6" class="stats-filter-content" style="height: 600px; background: white; padding: 20px 30px;">
                <label style="color: red; font-weight: bold;">Selected Event Stats:</label>
                <div class="stats-header">
                    <div style="flex: 2; border-right: 1px solid lightgray; color: black;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px;">
                            Italy Seria A
                        </div>
                        <div style="height: 20px; width: 100%; text-align: left; padding-left: 5px;">
                            Time
                        </div>
                    </div>
                    <div style="flex: 1; border-right: 1px solid lightgray;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px;">
                        </div>
                        <div style="height: 20px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black;">
                            Result
                        </div>
                    </div>
                    <div style="flex: 7;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px; color: black;">
                            Total Games
                        </div>
                        <div style="display: flex; height: 20px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                    </div>
                </div>
                <div class="stats-content">
                    <div style="flex: 2; border-right: 1px solid lightgray; color: black;">
                        <div style="width: 20%; float: left; text-align: center; padding-top: 20px;">FT</div>
                        <div style="width: 80%; float: left;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                Napoli (11)
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                Juventus (6)
                            </div>
                        </div>
                    </div>
                    <div style="flex: 1; border-right: 1px solid lightgray;">
                        <div style="height: 60px; width: 100%; text-align: center; padding-top: 20px;">
                            2 - 1
                        </div>
                    </div>
                    <div style="flex: 7;">
                        <div style="display: flex; height: 30px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black; padding-top: 3px;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                        <div style="display: flex; height: 30px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black; padding-top: 3px;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                    </div>
                </div>

                <div class="stats-header" style="background: #7c9fc7;">
                    <div style="flex: 2; border-right: 1px solid lightgray; color: black;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px;">
                            Italy Seria A
                        </div>
                        <div style="height: 20px; width: 100%; text-align: left; padding-left: 5px;">
                            H/A
                        </div>
                    </div>
                    <div style="flex: 1; border-right: 1px solid lightgray;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px;">
                        </div>
                        <div style="height: 20px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black;">
                            Result
                        </div>
                    </div>
                    <div style="flex: 7;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px; color: black;">
                            Avg Stats Per Game
                        </div>
                        <div style="display: flex; height: 20px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                    </div>
                </div>
                <div class="stats-content">
                    <div style="flex: 2; border-right: 1px solid lightgray; color: black;">
                        <div style="width: 20%; float: left; text-align: center;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                H
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                A
                            </div>
                        </div>
                        <div style="width: 80%; float: left;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                Napoli (11)
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                Juventus (6)
                            </div>
                        </div>
                    </div>
                    <div style="flex: 1; border-right: 1px solid lightgray;">
                        <div style="height: 60px; width: 100%; text-align: center;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                12
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                13
                            </div>
                        </div>
                    </div>
                    <div style="flex: 7;">
                        <div style="display: flex; height: 30px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black; padding-top: 3px;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                        <div style="display: flex; height: 30px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black; padding-top: 3px;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                    </div>
                </div>

                <div class="stats-header" style="background: #00ad4e;">
                    <div style="flex: 2; border-right: 1px solid lightgray; color: black;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px;">
                            Italy Seria A
                        </div>
                        <div style="height: 20px; width: 100%; text-align: left; padding-left: 5px;">
                            H/A
                        </div>
                    </div>
                    <div style="flex: 1; border-right: 1px solid lightgray;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px;">
                        </div>
                        <div style="height: 20px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black;">
                            Result
                        </div>
                    </div>
                    <div style="flex: 7;">
                        <div style="height: 20px; width: 100%; text-align: center; padding: 3px; color: black;">
                            Delta Indexes
                        </div>
                        <div style="display: flex; height: 20px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                    </div>
                </div>
                <div class="stats-content" style="border-bottom: 1px solid lightgrey;">
                    <div style="flex: 2; border-right: 1px solid lightgray; color: black;">
                        <div style="width: 20%; float: left; text-align: center;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                H
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                A
                            </div>
                        </div>
                        <div style="width: 80%; float: left;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                Napoli (11)
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                Juventus (6)
                            </div>
                        </div>
                    </div>
                    <div style="flex: 1; border-right: 1px solid lightgray;">
                        <div style="height: 60px; width: 100%; text-align: center;">
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                12
                            </div>
                            <div style="height: 30px; width: 100%; text-align: center; padding: 2px;">
                                13
                            </div>
                        </div>
                    </div>
                    <div style="flex: 7;">
                        <div style="display: flex; height: 30px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black; padding-top: 3px;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                        <div style="display: flex; height: 30px; width: 100%; text-align: left; padding-left: 5px; text-align: center; color: black; padding-top: 3px;">
                            <div style="flex: 1; text-align: center;">On</div>
                            <div style="flex: 1; text-align: center;">Off</div>
                            <div style="flex: 1; text-align: center;">Blk</div>
                            <div style="flex: 1; text-align: center;">In</div>
                            <div style="flex: 1; text-align: center;">Out</div>
                            <div style="flex: 1; text-align: center;">Cnr</div>
                            <div style="flex: 1; text-align: center;">DA</div>
                            <div style="flex: 1; text-align: center;">Pos</div>
                            <div style="flex: 1; text-align: center;">Red</div>
                            <div style="flex: 1; text-align: center;">Yel</div>
                        </div>
                    </div>
                </div>
            </CCol>
        </CRow>
    </div>
</template>

<script>
    export default {
        name: 'LiveStatsAnalysis',
        components: {
        },
        data () {
            return {
                from_date: '',
                end_date: '',
                min_minute: 0,
                max_minute: 0,
                eventList:[{'label': 'select an event', 'value': null}],
                leagues: [{"league": '', 'value': 0, 'label': 'select league'}],
                selected_league: null,
                homeTeam:{
                    'rank': {
                        'from': 0,
                        'to': 1000
                    },
                    'on': {
                        'from': 0,
                        'to': 1000
                    },
                    'off': {
                        'from': 0,
                        'to': 1000
                    },
                    'blk': {
                        'from': 0,
                        'to': 1000
                    },
                    'in': {
                        'from': 0,
                        'to': 1000
                    },
                    'out': {
                        'from': 0,
                        'to': 1000
                    },
                    'cnr': {
                        'from': 0,
                        'to': 1000
                    },
                    'da': {
                        'from': 0,
                        'to': 1000
                    },
                    'pos': {
                        'from': 0,
                        'to': 1000
                    },
                    'red': {
                        'from': 0,
                        'to': 1000
                    },
                    'yel': {
                        'from': 0,
                        'to': 1000
                    },
                    'goal': {
                        'from': 0,
                        'to': 1000
                    }
                },
                awayTeam:{
                    'rank': {
                        'from': 0,
                        'to': 1000
                    },
                    'on': {
                        'from': 0,
                        'to': 1000
                    },
                    'off': {
                        'from': 0,
                        'to': 1000
                    },
                    'blk': {
                        'from': 0,
                        'to': 1000
                    },
                    'in': {
                        'from': 0,
                        'to': 1000
                    },
                    'out': {
                        'from': 0,
                        'to': 1000
                    },
                    'cnr': {
                        'from': 0,
                        'to': 1000
                    },
                    'da': {
                        'from': 0,
                        'to': 1000
                    },
                    'pos': {
                        'from': 0,
                        'to': 1000
                    },
                    'red': {
                        'from': 0,
                        'to': 1000
                    },
                    'yel': {
                        'from': 0,
                        'to': 1000
                    },
                    'goal': {
                        'from': 0,
                        'to': 1000
                    }
                },
                origin_events: [],
                total_home_stats:{
                    'competition': '',
                    'name': '',
                    'score': '',
                    'time': '',
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                },
                total_away_stats:{
                    'name': '',
                    'score': '',
                    'time': '',
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                },
                dateList1: [],
                dateList2:[],
                avg_home_stats:{
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                },
                avg_away_stats:{
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                },
            }
        },
        methods: {
            getTable(val1, val2, val3){
                window.axios.post(`${process.env.VUE_APP_URL}getlivestatsData`, [val1, val2, val3]).then(({data})=> {
                    console.log('liveStatsData==>', data.data[0])
                    let events = data.data[0]
                    this.eventList = [{'label': 'select an event', 'value': null}]
                    for(let i = 0 ; i < events.length ; i++){
                        console.log(events[i])
                        if(events[i].time[0]){
                            let date_str = events[i].time[0].starting_at.date_time.split(" ")[0] + ', '+ events[i].time[0].starting_at.date_time.split(" ")[1]
                            let label = date_str + ' >> ' + events[i].home_name + ' v ' + events[i].away_name
                            this.eventList.push({"label": label, "value": events[i]})
                        }
                    }
                    this.origin_events = this.eventList
                    console.log('eventListResult===>', this.eventList)
                })
            },
            from_date_f(val){
                console.log(val)
                this.from_date = val
                this.end_date = val
                let new_dateList = []
                for(let i = 0 ; i < this.dateList1.length ; i++){
                    if(this.dateList1[i].value >= this.from_date){
                        new_dateList.push(this.dateList1[i])
                    }
                }
                this.dateList2 = new_dateList
            },
            end_date_f(val){
                console.log(val)
                this.end_date = val
            },
            min_minute_f(){

            },
            max_minute_f(){

            },
            set_event(val){
                console.log('selected event value log', val)
                this.total_home_stats = {
                    'competition': '',
                    'name': '',
                    'score': '',
                    'time': '',
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                }
                this.total_away_stats = {
                    'name': '',
                    'score': '',
                    'time': '',
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                }
                let home_id = val.home_id
                let away_id = val.away_id
                let home_name = val.home_name
                let away_name = val.away_name
                let home_rank = val.home_rank
                let away_rank = val.away_rank

                this.total_home_stats.name = home_name + ' (' + home_rank + ') '
                this.total_away_stats.name = away_name + ' (' + away_rank + ') '
                this.total_home_stats.time = 'FT'
                let statsLength = val.stats.length
                let cStats = val.stats[statsLength - 1]
                let cScore = val.scores[statsLength - 1]
                let cSeasonStats = val.season_stats
                this.total_home_stats.score = cScore.localteam_score
                this.total_away_stats.score = cScore.visitorteam_score
                if(val.competitions.length > 0){
                    this.total_home_stats.competition = val.competitions[0].name
                }

                this.avg_home_stats = {
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                }
                this.avg_away_stats = {
                    'on': '-',
                    'off': '-',
                    'blk': '-',
                    'in': '-',
                    'out': '-',
                    'cnr': '-',
                    'da': '-',
                    'pos': '-',
                    'red': '-',
                    'yel': '-'
                }
                if(cSeasonStats.length > 0){
                    for(let i = 0; i < cSeasonStats.length ; i++){
                        if(cSeasonStats[i].stats){
                            if(cSeasonStats[i].stats.length > 0){

                            }
                        }
                    }
                }

            },
            get_search_events(){
                let events = this.origin_events
                let event_list = [{'label': 'select an event', 'value': null}]
                for(let i = 1 ; i < events.length ; i++){
                    let value = events[i].value
                    let stats = value.stats
                    let home_id = value.home_id
                    let away_id = value.away_id
                    if(value.away_rank && value.home_rank){
                        // console.log('rank checking', this.homeTeam.rank.from, this.homeTeam.rank.to, this.awayTeam.rank.from, this.awayTeam.rank.to)
                        // console.log('rank checking', value.home_rank, value.away_rank)
                        if(value.home_rank >= this.homeTeam.rank.from && value.home_rank <= this.homeTeam.rank.to && value.away_rank >= this.awayTeam.rank.from && value.away_rank <= this.awayTeam.rank.to){
                            let stats_length = stats.length

                            if(stats_length > 0){
                                // console.log('rank checking', value.home_rank, value.away_rank)
                                let statsData = stats[stats_length - 1]
                                // console.log('statsData=>', statsData)
                                let home_stats_data = {
                                    'on': 0,
                                    'off': 0,
                                    'blk': 0,
                                    'in': 0,
                                    'out': 0,
                                    'cnr': 0,
                                    'da': 0,
                                    'pos': 0,
                                    'red': 0,
                                    'yel': 0,
                                    'goal': 0
                                }
                                let away_stats_data = {
                                    'on': 0,
                                    'off': 0,
                                    'blk': 0,
                                    'in': 0,
                                    'out': 0,
                                    'cnr': 0,
                                    'da': 0,
                                    'pos': 0,
                                    'red': 0,
                                    'yel': 0,
                                    'goal': 0
                                }
                                if(statsData[0].team_id == home_id){
                                    if(statsData[0].shots){
                                        home_stats_data.on = statsData[0].shots.ongoal
                                        away_stats_data.on = statsData[1].shots.ongoal
                                        home_stats_data.off = statsData[0].shots.offgoal
                                        away_stats_data.off = statsData[1].shots.offgoal
                                        home_stats_data.blk = statsData[0].shots.blocked
                                        away_stats_data.blk = statsData[1].shots.blocked
                                        home_stats_data.in = statsData[0].shots.insidebox
                                        away_stats_data.in = statsData[1].shots.insidebox
                                        home_stats_data.out = statsData[0].shots.outsidebox
                                        away_stats_data.out = statsData[1].shots.outsidebox
                                    }
                                    if(statsData[0].corners){
                                        home_stats_data.cnr = statsData[0].corners
                                        away_stats_data.cnr = statsData[1].corners
                                    }
                                    if(statsData[0].attacks){
                                        home_stats_data.cnr = statsData[0].attacks.dangerous_attacks
                                        away_stats_data.cnr = statsData[1].attacks.dangerous_attacks
                                    }
                                    if(statsData[0].possessiontime){
                                        home_stats_data.pos = statsData[0].possessiontime
                                        away_stats_data.pos = statsData[1].possessiontime
                                    }
                                    if(statsData[0].redcards){
                                        home_stats_data.red = statsData[0].redcards
                                        away_stats_data.red = statsData[1].redcards
                                    }
                                    if(statsData[0].yellowcards){
                                        home_stats_data.yel = statsData[0].yellowcards
                                        away_stats_data.yel = statsData[1].yellowcards
                                    }
                                    if(statsData[0].goals){
                                        home_stats_data.goal = statsData[0].goals
                                        away_stats_data.goal = statsData[1].goals
                                    }
                                }
                                else if(statsData[1].team_id == home_id){
                                    if(statsData[0].shots){
                                        home_stats_data.on = statsData[1].shots.ongoal
                                        away_stats_data.on = statsData[0].shots.ongoal
                                        home_stats_data.off = statsData[1].shots.offgoal
                                        away_stats_data.off = statsData[0].shots.offgoal
                                        home_stats_data.blk = statsData[1].shots.blocked
                                        away_stats_data.blk = statsData[0].shots.blocked
                                        home_stats_data.in = statsData[1].shots.insidebox
                                        away_stats_data.in = statsData[0].shots.insidebox
                                        home_stats_data.out = statsData[1].shots.outsidebox
                                        away_stats_data.out = statsData[0].shots.outsidebox
                                    }
                                    if(statsData[0].corners){
                                        home_stats_data.cnr = statsData[1].corners
                                        away_stats_data.cnr = statsData[0].corners
                                    }
                                    if(statsData[0].attacks){
                                        home_stats_data.cnr = statsData[1].attacks.dangerous_attacks
                                        away_stats_data.cnr = statsData[0].attacks.dangerous_attacks
                                    }
                                    if(statsData[0].possessiontime){
                                        home_stats_data.pos = statsData[1].possessiontime
                                        away_stats_data.pos = statsData[0].possessiontime
                                    }
                                    if(statsData[0].redcards){
                                        home_stats_data.red = statsData[1].redcards
                                        away_stats_data.red = statsData[0].redcards
                                    }
                                    if(statsData[0].yellowcards){
                                        home_stats_data.yel = statsData[1].yellowcards
                                        away_stats_data.yel = statsData[0].yellowcards
                                    }
                                    if(statsData[0].goals){
                                        home_stats_data.goal = statsData[1].goals
                                        away_stats_data.goal = statsData[0].goals
                                    }
                                }
                                // console.log('on checking=>', home_stats_data.on, away_stats_data.on, statsData[0].team_id, home_id)
                                if(home_stats_data.on >= this.homeTeam.on.from && home_stats_data.on <= this.homeTeam.on.to && away_stats_data.on >= this.awayTeam.on.from && away_stats_data.on <= this.awayTeam.on.to){
// console.log('+++++++++++++++++++++++on - checking', this.homeTeam.on.from, this.homeTeam.on.to, this.awayTeam.on.from, this.awayTeam.on.to)
                                    if(home_stats_data.off >= this.homeTeam.off.from && home_stats_data.off <= this.homeTeam.off.to && away_stats_data.off >= this.awayTeam.off.from && away_stats_data.off <= this.awayTeam.off.to){
                                        if(home_stats_data.blk >= this.homeTeam.blk.from && home_stats_data.blk <= this.homeTeam.blk.to && away_stats_data.blk >= this.awayTeam.blk.from && away_stats_data.blk <= this.awayTeam.blk.to){
                                            if(home_stats_data.in >= this.homeTeam.in.from && home_stats_data.in <= this.homeTeam.in.to && away_stats_data.in >= this.awayTeam.in.from && away_stats_data.in <= this.awayTeam.in.to){
                                                if(home_stats_data.out >= this.homeTeam.out.from && home_stats_data.out <= this.homeTeam.out.to && away_stats_data.out >= this.awayTeam.out.from && away_stats_data.out <= this.awayTeam.out.to){
                                                    if(home_stats_data.cnr >= this.homeTeam.cnr.from && home_stats_data.cnr <= this.homeTeam.cnr.to && away_stats_data.cnr >= this.awayTeam.cnr.from && away_stats_data.cnr <= this.awayTeam.cnr.to){
                                                        if(home_stats_data.da >= this.homeTeam.da.from && home_stats_data.da <= this.homeTeam.da.to && away_stats_data.da >= this.awayTeam.da.from && away_stats_data.da <= this.awayTeam.da.to){
                                                            if(home_stats_data.pos >= this.homeTeam.pos.from && home_stats_data.pos <= this.homeTeam.pos.to && away_stats_data.pos >= this.awayTeam.pos.from && away_stats_data.pos <= this.awayTeam.pos.to){
                                                                if(home_stats_data.red >= this.homeTeam.red.from && home_stats_data.red <= this.homeTeam.red.to && away_stats_data.red >= this.awayTeam.red.from && away_stats_data.red <= this.awayTeam.red.to){
                                                                    if(home_stats_data.yel >= this.homeTeam.yel.from && home_stats_data.yel <= this.homeTeam.yel.to && away_stats_data.yel >= this.awayTeam.yel.from && away_stats_data.yel <= this.awayTeam.yel.to){
                                                                        if(home_stats_data.goal >= this.homeTeam.goal.from && home_stats_data.goal <= this.homeTeam.goal.to && away_stats_data.goal >= this.awayTeam.goal.from && away_stats_data.goal <= this.awayTeam.goal.to){
                                                                            event_list.push({"label": events[i].label, "value": events[i].value})
                                                                        }
                                                                    }
                                                                }
                                                            }
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
                this.eventList = event_list
            },
            h_rank_from(val){
                this.homeTeam.rank.from = parseInt(val)
                console.log('homeTeam From====>', val)
                this.get_search_events()
            },
            a_rank_from(val){
                this.awayTeam.rank.from = parseInt(val)
                this.get_search_events()
            },
            h_rank_to(val){
                this.homeTeam.rank.to = parseInt(val)
                this.get_search_events()
            },
            a_rank_to(val){
                this.awayTeam.rank.to = parseInt(val)
                this.get_search_events()
            },
            h_on_from(val){
                this.homeTeam.on.from = parseInt(val)
                console.log('homeTeam From====>', val)
                this.get_search_events()
            },
            a_on_from(val){
                this.awayTeam.on.from = parseInt(val)
                this.get_search_events()
            },
            h_on_to(val){
                this.homeTeam.on.to = parseInt(val)
                this.get_search_events()
            },
            a_on_to(val){
                this.awayTeam.on.to = parseInt(val)
                this.get_search_events()
            },
            h_off_from(val){
                this.homeTeam.off.from = parseInt(val)
                this.get_search_events()
            },
            a_off_from(val){
                this.awayTeam.off.from = parseInt(val)
                this.get_search_events()
            },
            h_off_to(val){
                this.homeTeam.off.to = parseInt(val)
                this.get_search_events()
            },
            a_off_to(val){
                this.awayTeam.off.to = parseInt(val)
                this.get_search_events()
            },
            h_blk_from(val){
                this.homeTeam.blk.from = parseInt(val)
                this.get_search_events()
            },
            a_blk_from(val){
                this.awayTeam.blk.from = parseInt(val)
                this.get_search_events()
            },
            h_blk_to(val){
                this.homeTeam.blk.to = parseInt(val)
                this.get_search_events()
            },
            a_blk_to(val){
                this.awayTeam.blk.to = parseInt(val)
                this.get_search_events()
            },
            h_in_from(val){
                this.homeTeam.in.from = parseInt(val)
                this.get_search_events()
            },
            a_in_from(val){
                this.awayTeam.in.from = parseInt(val)
                this.get_search_events()
            },
            h_in_to(val){
                this.homeTeam.in.to = parseInt(val)
                this.get_search_events()
            },
            a_in_to(val){
                this.awayTeam.in.to = parseInt(val)
                this.get_search_events()
            },
            h_out_from(val){
                this.homeTeam.out.from = parseInt(val)
                this.get_search_events()
            },
            a_out_from(val){
                this.awayTeam.out.from = parseInt(val)
                this.get_search_events()
            },
            h_out_to(val){
                this.homeTeam.out.to = parseInt(val)
                this.get_search_events()
            },
            a_out_to(val){
                this.awayTeam.out.to = parseInt(val)
                this.get_search_events()
            },
            h_cnr_from(val){
                this.homeTeam.cnr.from = parseInt(val)
                this.get_search_events()
            },
            a_cnr_from(val){
                this.awayTeam.cnr.from = parseInt(val)
                this.get_search_events()
            },
            h_cnr_to(val){
                this.homeTeam.cnr.to = parseInt(val)
                this.get_search_events()
            },
            a_cnr_to(val){
                this.awayTeam.cnr.to = parseInt(val)
                this.get_search_events()
            },
            h_da_from(val){
                this.homeTeam.da.from = parseInt(val)
                this.get_search_events()
            },
            a_da_from(val){
                this.awayTeam.da.from = parseInt(val)
                this.get_search_events()
            },
            h_da_to(val){
                this.homeTeam.da.to = parseInt(val)
                this.get_search_events()
            },
            a_da_to(val){
                this.awayTeam.da.to = parseInt(val)
                this.get_search_events()
            },
            h_pos_from(val){
                this.homeTeam.pos.from = parseInt(val)
                this.get_search_events()
            },
            a_pos_from(val){
                this.awayTeam.pos.from = parseInt(val)
                this.get_search_events()
            },
            h_pos_to(val){
                this.homeTeam.pos.to = parseInt(val)
                this.get_search_events()
            },
            a_pos_to(val){
                this.awayTeam.pos.to = parseInt(val)
                this.get_search_events()
            },
            h_red_from(val){
                this.homeTeam.red.from = parseInt(val)
                this.get_search_events()
            },
            a_red_from(val){
                this.awayTeam.red.from = parseInt(val)
                this.get_search_events()
            },
            h_red_to(val){
                this.homeTeam.red.to = parseInt(val)
                this.get_search_events()
            },
            a_red_to(val){
                this.awayTeam.red.to = parseInt(val)
                this.get_search_events()
            },
            h_yel_from(val){
                this.homeTeam.yel.from = parseInt(val)
                this.get_search_events()
            },
            a_yel_from(val){
                this.awayTeam.yel.from = parseInt(val)
                this.get_search_events()
            },
            h_yel_to(val){
                this.homeTeam.yel.to = parseInt(val)
                this.get_search_events()
            },
            a_yel_to(val){
                this.awayTeam.yel.to = parseInt(val)
                this.get_search_events()
            },
            h_goal_from(val){
                this.homeTeam.goal.from = parseInt(val)
                this.get_search_events()
            },
            a_goal_from(val){
                this.awayTeam.goal.from = parseInt(val)
                this.get_search_events()
            },
            h_goal_to(val){
                this.homeTeam.goal.to = parseInt(val)
                this.get_search_events()
            },
            a_goal_to(val){
                this.awayTeam.goal.to = parseInt(val)
                this.get_search_events()
            },
            getLiveData(){
                console.log('get live data parameters===>', this.from_date, this.end_date)
                if(this.selected_league){
                    this.getTable(this.from_date, this.end_date, this.selected_league)
                }
                else{
                    return
                }
            },
            getLeagueList(){
                window.axios.post(`${process.env.VUE_APP_URL}getleaguelist`).then(({data})=> {
                    console.log('liveStatsData==>', data.data[0])
                    let datalist = data.data[0]
                    let self = this
                    for(let i = 0 ; i < datalist.length ; i++){
                        self.leagues.push({'league': datalist[i].name, 'value': datalist[i].eventId, 'label': datalist[i].name})
                    }
                    this.sortJSON(self.leagues,'league', '123');
                    console.log(this.leagues)
                })
            },
            set_league(val){
                console.log('value===>', val)
                this.selected_league = val
            },
            sortJSON(data, key){
                return data.sort(function(a, b) {
                    var x = a[key]; var y = b[key];
                    return ((x < y) ? -1 : ((x > y) ? 1 : 0));
                });
            },
            getDateList(){
                this.dateList1 = []
                this.dateList2 = []
                for(let i = 0; i < 118 ; i++){
                    let start_date = new Date();
                    let next_date = start_date.setDate(start_date.getDate() - (118 - i));
                    next_date = new Date(next_date).toISOString()
                    next_date = next_date.substring(0,10)
                    this.dateList1.push({'label': next_date, 'value': next_date})
                }
                this.dateList2 = this.dateList1
                console.log('datelistcheck===>', this.dateList1, this.dateList2)
            }
        },
        created() {
            this.getLeagueList()
            this.getDateList()
        },
        mounted() {

        },
        beforeDestroy() {

        }
    }
</script>
<style>
    .live-stats-container{
        min-width: 1200px;
    }
    .live-stats-container input{
        border-radius: 0;
        height: 25px;
    }
    .live-stats-container .stats-filter-content input{
        padding-left: 5px;
        padding-right: 0px;
    }
    .from_date{
        display: flex;
        width: 60%;
    }
    .live-stats-container .event-list{
        width: 60%;
        background: none;
        padding: 0;
    }
    .live-stats-container .league-list{
        width: 100%;
        background: none;
        padding: 0;
    }
    .live-stats-container .stats-header{
        height: 40px;
        width: 100%;
        border: none;
        background: #b1a0c7;
        display: flex;
    }
    .live-stats-container .stats-content{
        height: 60px;
        width: 100%;
        border: none;
        background: none;
        display: flex;
        border-right: 1px solid lightgrey;
        border-left: 1px solid lightgrey;
    }
</style>
