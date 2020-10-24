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
                        <CInput type="text"  :value="this.min_minute" @update:value="min_minute_f" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
                            </div>
                        </div>
                        <div style="flex: 1; padding: 1px 5px;">
                            <label style="width: 30px; float: left; text-align: right; padding-right: 10px;">to</label>
                            <div style="width: calc(100% - 30px); float: left;">
                                <CInput type="text"  :value="this.from_date" @update:value="min_minute" class="odd-filter-inputbox"></CInput>
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
                eventList:[]
            }
        },
        methods: {
            getTable(val1, val2){
                window.axios.post(`${process.env.VUE_APP_URL}getlivestatsData`, [val1, val2]).then(({data})=> {
                    console.log('liveStatsData==>', data.data[0])
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
            set_event(){

            },
            getLiveData(){
                console.log('get live data parameters===>', this.from_date, this.end_date)
                this.getTable(this.from_date, this.end_date)
            }
        },
        created() {

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
