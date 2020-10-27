<template>
    <div class="live-stats-container">
        <CRow>
            <CCol lg="6" style="height: 180px; background: white; padding: 20px 30px;">
                <label style="color: red; font-weight: bold;">Date:</label>
                <div class="from_date" style="height: 40px; width: 100%;">
                    <div style="flex: 1; padding-top: 1px; padding-right: 10px;">From:</div>
                    <div style="flex: 4; padding-right: 35px;">
                        <CInput type="text"  :value="this.from_date" @update:value="from_date_f" class="odd-filter-inputbox" placeholder="2000-01-01"></CInput>
                    </div>
                    <div style="flex: 1; padding-top: 1px; padding-right: 10px;">End:</div>
                    <div style="flex: 4; padding-right: 35px;">
                        <CInput type="text"  :value="this.end_date" @update:value="end_date_f" class="odd-filter-inputbox" placeholder="2000-01-01"></CInput>
                    </div>
                    <div style="width: 40%; float: left;">
                        <CButton color="success" @click="getLiveData" class="G-L-button">
                            Get Data
                        </CButton>
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
            <CCol lg="6" style="height: 600px; background: white; padding: 20px 30px;">
                <div style="width: 50%; float: left; padding-right: 20px;">
                    <label style="color: red; font-weight: bold;">Home Team:</label>
                    <div style="display: flex;">
                        <div style="flex: 1; padding: 1px 5px;">
                            <div style="background: #b1a0c7; text-align: center; margin: auto; padding: 3px;">Rank</div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">from</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.rank.from" @update:value="h_rank_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.rank.to" @update:value="h_rank_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.on.from" @update:value="h_on_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.on.to" @update:value="h_on_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.off.from" @update:value="h_off_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.off.to" @update:value="h_off_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.blk.from" @update:value="h_blk_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.blk.to" @update:value="h_blk_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.in.from" @update:value="h_in_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.in.to" @update:value="h_in_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.out.from" @update:value="h_out_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.out.to" @update:value="h_out_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.cnr.from" @update:value="h_cnr_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.cnr.to" @update:value="h_cnr_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.da.from" @update:value="h_da_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.da.to" @update:value="h_da_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.pos.from" @update:value="h_pos_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.pos.to" @update:value="h_pos_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.red.from" @update:value="h_red_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.red.to" @update:value="h_red_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.yel.from" @update:value="h_yel_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.yel.to" @update:value="h_yel_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="homeTeam.goal.from" @update:value="h_goal_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="homeTeam.goal.to" @update:value="h_goal_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.rank.from" @update:value="a_rank_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.rank.to" @update:value="a_rank_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.on.from" @update:value="a_on_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.on.to" @update:value="a_on_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.off.from" @update:value="a_off_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.off.to" @update:value="a_off_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.blk.from" @update:value="a_blk_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.blk.to" @update:value="a_blk_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.in.from" @update:value="a_in_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.in.to" @update:value="a_in_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.out.from" @update:value="a_out_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.out.to" @update:value="a_out_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.cnr.from" @update:value="a_cnr_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.cnr.to" @update:value="a_cnr_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.da.from" @update:value="a_da_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.da.to" @update:value="a_da_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.pos.from" @update:value="a_pos_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.pos.to" @update:value="a_pos_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.red.from" @update:value="a_red_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.red.to" @update:value="a_red_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.yel.from" @update:value="a_yel_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.yel.to" @update:value="a_yel_to" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="number"  :value="awayTeam.goal.from" @update:value="a_goal_from" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="number"  :value="awayTeam.goal.to" @update:value="a_goal_to" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                    </div>
                </div>
            </CCol>
            <CCol lg="6" style="height: 600px; background: white; padding: 20px 30px;">
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
                            2 - 0
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
                        'to': 100
                    },
                    'on': {
                        'from': 0,
                        'to': 100
                    },
                    'off': {
                        'from': 0,
                        'to': 100
                    },
                    'blk': {
                        'from': 0,
                        'to': 100
                    },
                    'in': {
                        'from': 0,
                        'to': 100
                    },
                    'out': {
                        'from': 0,
                        'to': 100
                    },
                    'cnr': {
                        'from': 0,
                        'to': 100
                    },
                    'da': {
                        'from': 0,
                        'to': 100
                    },
                    'pos': {
                        'from': 0,
                        'to': 100
                    },
                    'red': {
                        'from': 0,
                        'to': 100
                    },
                    'yel': {
                        'from': 0,
                        'to': 100
                    },
                    'goal': {
                        'from': 0,
                        'to': 100
                    }
                },
                awayTeam:{
                    'rank': {
                        'from': 0,
                        'to': 100
                    },
                    'on': {
                        'from': 0,
                        'to': 100
                    },
                    'off': {
                        'from': 0,
                        'to': 100
                    },
                    'blk': {
                        'from': 0,
                        'to': 100
                    },
                    'in': {
                        'from': 0,
                        'to': 100
                    },
                    'out': {
                        'from': 0,
                        'to': 100
                    },
                    'cnr': {
                        'from': 0,
                        'to': 100
                    },
                    'da': {
                        'from': 0,
                        'to': 100
                    },
                    'pos': {
                        'from': 0,
                        'to': 100
                    },
                    'red': {
                        'from': 0,
                        'to': 100
                    },
                    'yel': {
                        'from': 0,
                        'to': 100
                    },
                    'goal': {
                        'from': 0,
                        'to': 100
                    }
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
                        if(events[i].time[0]){
                            let label = events[i].time[0].starting_at.date + ', ' + events[i].home_name + ' v ' + events[i].away_name
                            this.eventList.push({"label": label, "value": events[i]})
                        }
                    }
                })
            },
            from_date_f(val){
                console.log(val)
                this.from_date = val
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
            },
            get_search_events(){
                let events = this.eventList
                for(let i = 1 ; i < events.length ; i++){
                    let value = events[i].value
                    let stats = value.stats
                    let home_id = events[i].home_id
                    let away_id = events[i].away_id
                    if(value.away_rank && value.home_rank){
                        if(value.home_rank >= this.homeTeam.rank.from && value.home_rank <= this.homeTeam.rank.to && value.away_rank >= this.awayTeam.rank.from && value.away_rank <= this.awayTeam.rank.to){
                            if(stats[0]){

                            }
                        }
                    }
console.log('events===>', events[i].value)
                }
            },
            h_rank_from(val){
                this.homeTeam.rank.from = val
                this.get_search_events()
            },
            a_rank_from(val){
                this.awayTeam.rank.from = val
                this.get_search_events()
            },
            h_rank_to(val){
                this.homeTeam.rank.to = val
                this.get_search_events()
            },
            a_rank_to(val){
                this.awayTeam.rank.to = val
                this.get_search_events()
            },
            h_on_from(val){
                this.homeTeam.on.from = val
                this.get_search_events()
            },
            a_on_from(val){
                this.awayTeam.on.from = val
                this.get_search_events()
            },
            h_on_to(val){
                this.homeTeam.on.to = val
                this.get_search_events()
            },
            a_on_to(val){
                this.awayTeam.on.to = val
                this.get_search_events()
            },
            h_off_from(val){
                this.homeTeam.off.from = val
                this.get_search_events()
            },
            a_off_from(val){
                this.awayTeam.off.from = val
                this.get_search_events()
            },
            h_off_to(val){
                this.homeTeam.off.to = val
                this.get_search_events()
            },
            a_off_to(val){
                this.awayTeam.off.to = val
                this.get_search_events()
            },
            h_blk_from(val){
                this.homeTeam.blk.from = val
                this.get_search_events()
            },
            a_blk_from(val){
                this.awayTeam.blk.from = val
                this.get_search_events()
            },
            h_blk_to(val){
                this.homeTeam.blk.to = val
                this.get_search_events()
            },
            a_blk_to(val){
                this.awayTeam.blk.to = val
                this.get_search_events()
            },
            h_in_from(val){
                this.homeTeam.in.from = val
                this.get_search_events()
            },
            a_in_from(val){
                this.awayTeam.in.from = val
                this.get_search_events()
            },
            h_in_to(val){
                this.homeTeam.in.to = val
                this.get_search_events()
            },
            a_in_to(val){
                this.awayTeam.in.to = val
                this.get_search_events()
            },
            h_out_from(val){
                this.homeTeam.out.from = val
                this.get_search_events()
            },
            a_out_from(val){
                this.awayTeam.out.from = val
                this.get_search_events()
            },
            h_out_to(val){
                this.homeTeam.out.to = val
                this.get_search_events()
            },
            a_out_to(val){
                this.awayTeam.out.to = val
                this.get_search_events()
            },
            h_cnr_from(val){
                this.homeTeam.cnr.from = val
                this.get_search_events()
            },
            a_cnr_from(val){
                this.awayTeam.cnr.from = val
                this.get_search_events()
            },
            h_cnr_to(val){
                this.homeTeam.cnr.to = val
                this.get_search_events()
            },
            a_cnr_to(val){
                this.awayTeam.cnr.to = val
                this.get_search_events()
            },
            h_da_from(val){
                this.homeTeam.da.from = val
                this.get_search_events()
            },
            a_da_from(val){
                this.awayTeam.da.from = val
                this.get_search_events()
            },
            h_da_to(val){
                this.homeTeam.da.to = val
                this.get_search_events()
            },
            a_da_to(val){
                this.awayTeam.da.to = val
                this.get_search_events()
            },
            h_pos_from(val){
                this.homeTeam.pos.from = val
                this.get_search_events()
            },
            a_pos_from(val){
                this.awayTeam.pos.from = val
                this.get_search_events()
            },
            h_pos_to(val){
                this.homeTeam.pos.to = val
                this.get_search_events()
            },
            a_pos_to(val){
                this.awayTeam.pos.to = val
                this.get_search_events()
            },
            h_red_from(val){
                this.homeTeam.red.from = val
                this.get_search_events()
            },
            a_red_from(val){
                this.awayTeam.red.from = val
                this.get_search_events()
            },
            h_red_to(val){
                this.homeTeam.red.to = val
                this.get_search_events()
            },
            a_red_to(val){
                this.awayTeam.red.to = val
                this.get_search_events()
            },
            h_yel_from(val){
                this.homeTeam.yel.from = val
                this.get_search_events()
            },
            a_yel_from(val){
                this.awayTeam.yel.from = val
                this.get_search_events()
            },
            h_yel_to(val){
                this.homeTeam.yel.to = val
                this.get_search_events()
            },
            a_yel_to(val){
                this.awayTeam.yel.to = val
                this.get_search_events()
            },
            h_goal_from(val){
                this.homeTeam.goal.from = val
                this.get_search_events()
            },
            a_goal_from(val){
                this.awayTeam.goal.from = val
                this.get_search_events()
            },
            h_goal_to(val){
                this.homeTeam.goal.to = val
                this.get_search_events()
            },
            a_goal_to(val){
                this.awayTeam.goal.to = val
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
        },
        created() {
            this.getLeagueList()
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
