<template>
    <div class="live-stats-container" style="min-width: 1240px;">
        <CCard body-wrapper>
            <CTabs variant="tabs" :active-tab="1">
                <CTab :title="'Scheduled Games('+scheduleLength+')'">
                    <div v-for="item in scheduleArray" :key="item.league">
                        <div v-if="item.events.length > 0" class="schedule-header" style="height: 30px; background: #d6d8d9; font-weight: 700; font-size: 15px; padding: 3px 10px;">
                            {{item.league}}
                        </div>
                        <div v-for="item1 in item.events" :key="item1._id" class="event-content" style="height: 35px; font-size: 16px;">
                            <div style="background: white">
                                <div style="width: 5%; float: left;">
                                    {{item1.time.starting_at.time}}
                                </div>
                                <div style="width: 20%; float: left; text-align: right; padding-right: 2%;">
                                    {{item1.localTeamName}}
                                </div>
                                <div style="width: 20%; float: left; text-align: left; padding-left: 5%;">
                                    {{item1.visitorTeamName}}
                                </div>
                            </div>
                        </div>
                    </div>
                </CTab>
                <CTab :title="'LIVE Games('+liveNumbers+')'">
                    <div v-for="item in eventArray" :key="item.league" style="margin-top: -3px;">
                        <div v-if="item.events.length > 0 && item.league"  class="header" style="width: 100%; height: 50px;">
                            <div class="header-content" style="width: 16%; height: 50px; float: left; text-align: left;">
                                {{item.league}}
                            </div>
                            <div class="header-content" style="width: 5%; min-width: 30px; height: 50px; float: left; border-left: 1px solid whitesmoke; padding-top: 23px">
                                Result
                            </div>
                            <div class="header-content detail_total" style="width: 25%; height: 50px; float: left; border-left: 1px solid whitesmoke">
                                Total Game
                                <div style="width: 100%">
                                    <div class="detail">
                                        On
                                    </div>
                                    <div class="detail">
                                        Off
                                    </div>
                                    <div class="detail">
                                        Blk
                                    </div>
                                    <div class="detail">
                                        In
                                    </div>
                                    <div class="detail">
                                        Out
                                    </div>
                                    <div class="detail">
                                        Cnr
                                    </div>
                                    <div class="detail">
                                        DA
                                    </div>
                                    <div class="detail">
                                        Poss
                                    </div>
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Pas-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Acc-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Atk-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Ofs-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Sav-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Sbst-->
                                    <!--                                        </div>-->
                                    <div class="detail">
                                        Red
                                    </div>
                                    <div class="detail" style="width: 4%;">
                                        Rtg
                                    </div>
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Fou-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail" style="min-width: 30px;">-->
                                    <!--                                            G_att-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Safe-->
                                    <!--                                        </div>-->
                                </div>
                            </div>
                            <div class="header-content detail_total" style="width: 26%; height: 50px; float: left; border-left: 1px solid whitesmoke">
                                Last 10 minutes
                                <div style="width: 100%">
                                    <div class="detail">
                                        On
                                    </div>
                                    <div class="detail">
                                        Off
                                    </div>
                                    <div class="detail">
                                        Blk
                                    </div>
                                    <div class="detail">
                                        In
                                    </div>
                                    <div class="detail">
                                        Out
                                    </div>
                                    <div class="detail">
                                        Cnr
                                    </div>
                                    <div class="detail">
                                        DA
                                    </div>
                                    <div class="detail" style="min-width: 32px;">
                                        Poss
                                    </div>
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Pas-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Acc-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Atk-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Ofs-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Sav-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Sbst-->
                                    <!--                                        </div>-->
                                    <div class="detail" style="min-width: 30px;">
                                        Goals
                                    </div>
                                    <div class="detail" style="width: 4%;">
                                        Rtg
                                    </div>
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Fou-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail" style="min-width: 30px;">-->
                                    <!--                                            G_att-->
                                    <!--                                        </div>-->
                                    <!--                                        <div class="detail">-->
                                    <!--                                            Safe-->
                                    <!--                                        </div>-->
                                </div>
                            </div>
                            <div class="header-content" style="width: 10%; height: 50px; float: left; border-left: 1px solid whitesmoke">
                                Alert
                            </div>
                            <div class="header-content" style="width: 18%; height: 50px; float: left; border-left: 1px solid whitesmoke">
                                Chart
                            </div>
                        </div>
                        <div v-for="(item1, index) in item.events" :key="item1.away_id" class="content" style="width: 100%; height: 62px; font-weight: 600">
                            <!--  home team data part Total -->
                            <div style="width: 16%; height: 30px; float: left; position: relative; top: 0px;">
                                <div class="time_manner" style="width: 60px; float: left;position: relative; top:  23px; left: 15px; font-size: 17px; font-weight: normal">{{item1.home.time}}'</div>
                                <div v-if="item1.home.flash == 1" class="goal_manner" style="width: calc(100% - 65px); float: left;">{{item1.main_data.home_name}} ({{item1.main_data.home_rank}})</div>
                                <div v-else style="width: calc(100% - 65px); float: left;">{{item1.main_data.home_name}} ({{item1.main_data.home_rank}})</div>
                            </div>
                            <div
                                    @click="SetCollapse1(item1.index0)"
                                    duration="100"
                                    style="height: 0px; position: relative; top: 17px; left: -18px;"
                            >
                                <img v-if="isPlus(item1.index0)" src="/img/ico-plus.png" width="13px;" style="width: 16px; cursor: pointer;"/>
                                <img v-if="isMinus(item1.index0)" src="/img/ico-minus.png" width="13px;" style="width: 16px; cursor: pointer;"/>
                            </div>
                            <div style="width: 5%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">
                                    <transition name="slide-fade" mode="out-in" class="livenow">
                                        <div :key="item1.home.score" class="detail" style="color: red; position: relative; top: 22px; left: 7px; font-size: 18px;">
                                            {{item1.home.score}} - {{item1.away.score}}
                                        </div>
                                    </transition>
                                </div>
                            </div>
                            <div class="detail_total" style="width: 25%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">
                                    <transition name="slide-fade" mode="out-in" class="livenow">
                                        <div :key="item1.homeT.on" v-if="item1.homeT.on == 0" class="detail" style="color: red;">
                                            {{item1.homeT.on}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.on" v-if="item1.homeT.on > 0" class="detail" style="color: green;">
                                            {{item1.homeT.on}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.off" v-if="item1.homeT.off == 0" class="detail" style="color: red">
                                            {{item1.homeT.off}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.off" v-if="item1.homeT.off > 0" class="detail" style="color: green">
                                            {{item1.homeT.off}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.blk" v-if="item1.homeT.blk > 0" class="detail" style="color: green">
                                            {{item1.homeT.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div v-if="item1.homeT.blk == 0" class="detail" style="color: red">
                                            {{item1.homeT.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.blk" v-if="item1.homeT.blk == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.in" v-if="item1.homeT.in == 0" class="detail" style="color: red">
                                            {{item1.homeT.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.in" v-if="item1.homeT.in > 0" class="detail" style="color: green;">
                                            {{item1.homeT.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.in" v-if="item1.homeT.in == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.out" v-if="item1.homeT.out == 0" class="detail" style="color: red">
                                            {{item1.homeT.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.out" v-if="item1.homeT.out > 0" class="detail" style="color: green">
                                            {{item1.homeT.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.out" v-if="item1.homeT.out == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.cnr" v-if="item1.homeT.cnr == 0" class="detail" style="color: red">
                                            {{item1.homeT.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.cnr" v-if="item1.homeT.cnr > 0" class="detail" style="color: green">
                                            {{item1.homeT.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.cnr" v-if="item1.homeT.cnr == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.da" v-if="item1.homeT.da == 0" class="detail" style="color: red">
                                            {{item1.homeT.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.da" v-if="item1.homeT.da > 0" class="detail" style="color: green">
                                            {{item1.homeT.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.poss" v-if="item1.homeT.poss == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.poss" v-if="item1.homeT.poss == 0" class="detail" style="color: green">
                                            {{item1.homeT.poss}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.poss" v-if="item1.homeT.poss != 0 && item1.homeT.poss != null" class="detail" style="color: green">
                                            {{item1.homeT.poss}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.red" v-if="item1.homeT.red == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.red" v-if="item1.homeT.red == 0" class="detail" style="color: red">
                                            0
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.homeT.red" v-if="item1.homeT.red != 0 && item1.homeT.red != null" class="detail" style="color: green">
                                            {{item1.homeT.red}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div class="detail" style="color: green">
                                            -
                                        </div>
                                    </transition>
                                </div>
                            </div>
                            <div class="detail_total" style="width: 26%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.on" v-if="item1.home.on >= 0" class="detail" style="color: green;">
                                            {{item1.home.on}}
                                        </div>
                                    </transition>

                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.off" v-if="item1.home.off >= 0" class="detail" style="color: green">
                                            {{item1.home.off}}
                                        </div>
                                    </transition>

                                    <transition name="slide-fade" mode="out-in">
                                        <div v-if="item1.home.blk >= 0" class="detail" style="color: red">
                                            {{item1.home.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.blk" v-if="item1.home.blk == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>

                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.in" v-if="item1.home.in >= 0" class="detail" style="color: green;">
                                            {{item1.home.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.in" v-if="item1.home.in == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>

                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.out" v-if="item1.home.out >= 0" class="detail" style="color: green">
                                            {{item1.home.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.out" v-if="item1.home.out == null" class="detail">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.cnr" v-if="item1.home.cnr == 0" class="detail" style="color: red">
                                            {{item1.home.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.cnr" v-if="item1.home.cnr > 0" class="detail" style="color: green">
                                            {{item1.home.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.cnr" v-if="item1.home.cnr == null" class="detail">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.da" v-if="item1.home.da == 0" class="detail" style="color: red">
                                            {{item1.home.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.da" v-if="item1.home.da > 0" class="detail" style="color: green">
                                            {{item1.home.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.poss" v-if="item1.home.poss == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.poss" v-if="item1.home.poss == 0" class="detail" style="color: red">
                                            0
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.poss" v-if="item1.home.poss != null && item1.home.poss != 0" class="detail" style="color: green">
                                            {{item1.home.poss}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.goal" v-if="item1.home.goal == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.home.goal" v-if="item1.home.goal != null" class="detail" style="color: green">
                                            {{item1.home.goal}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div class="detail" style="color: green">
                                            -
                                        </div>
                                    </transition>
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.pas" v-if="item1.home.pas == null" class="detail">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.pas" v-if="item1.home.pas >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.pas}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.acc" v-if="item1.home.acc == null" class="detail" >-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.acc" v-if="item1.home.acc >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.acc}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.atk" v-if="item1.home.atk == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.atk" v-if="item1.home.atk >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.atk}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.ofs" v-if="item1.home.ofs == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.ofs" v-if="item1.home.ofs >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.ofs}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.sav" v-if="item1.home.sav == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.sav" v-if="item1.home.sav >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.sav}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.sbst" v-if="item1.home.sbst == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.sbst" v-if="item1.home.sbst >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.sbst}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.red" v-if="item1.home.red == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.red" v-if="item1.home.red >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.red}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.fou" v-if="item1.home.fou == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.fou" v-if="item1.home.fou >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.fou}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.g_att" v-if="item1.home.g_att == null" class="detail" style="color: red; min-width: 30px;">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.g_att" v-if="item1.home.g_att >= 0" class="detail" style="color: green; min-width: 30px;">-->
                                    <!--                                                {{item1.home.g_att}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->

                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.safe" v-if="item1.home.safe == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.home.safe" v-if="item1.home.safe >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.home.safe}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                </div>
                            </div>
                            <div style="width: 10%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                <div style="width: 100%; padding: 3px 7px; color: white;">
                                    ...
                                </div>
                            </div>
                            <div style="width: 18%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                <div style="width: 100%; padding: 3px 7px; color: white;">
                                    ...
                                </div>
                            </div>
                            <!--  away team data part  Total-->
                            <div style="width: 16%; height: 30px; float: left; position: relative; top: 0px; border-bottom: 1px solid lightgray;">
                                <div style="width: 60px; float: left; color: white;">.</div>
                                <div v-if="item1.away.flash == 1" class="goal_manner" style="width: calc(100% - 65px); float: left;">{{item1.main_data.away_name}} ({{item1.main_data.away_rank}})</div>
                                <div v-else style="width: calc(100% - 65px); float: left;">{{item1.main_data.away_name}} ({{item1.main_data.away_rank}})</div>
                            </div>
                            <div style="width: 5%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">
                                    <transition name="slide-fade" mode="out-in" class="livenow">
                                    </transition>
                                </div>
                            </div>
                            <div class="detail_total" style="width: 25%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.on" v-if="item1.awayT.on == 0" class="detail" style="color: red;">
                                            {{item1.awayT.on}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.on" v-if="item1.awayT.on > 0" class="detail" style="color: green;">
                                            {{item1.awayT.on}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.off" v-if="item1.awayT.off == 0" class="detail" style="color: red">
                                            {{item1.awayT.off}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.off" v-if="item1.awayT.off > 0" class="detail" style="color: green">
                                            {{item1.awayT.off}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.blk" v-if="item1.awayT.blk > 0" class="detail" style="color: green">
                                            {{item1.awayT.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.blk" v-if="item1.awayT.blk == 0" class="detail" style="color: red">
                                            {{item1.awayT.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.blk" v-if="item1.awayT.blk == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.in" v-if="item1.awayT.in == 0" class="detail" style="color: red">
                                            {{item1.awayT.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.in" v-if="item1.awayT.in > 0" class="detail" style="color: green;">
                                            {{item1.awayT.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.in" v-if="item1.awayT.in == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.out" v-if="item1.awayT.out == 0" class="detail" style="color: red">
                                            {{item1.awayT.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.out" v-if="item1.awayT.out > 0" class="detail" style="color: green">
                                            {{item1.awayT.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.out" v-if="item1.awayT.out == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.cnr" v-if="item1.awayT.cnr == 0" class="detail" style="color: red">
                                            {{item1.awayT.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.cnr" v-if="item1.awayT.cnr > 0" class="detail" style="color: green">
                                            {{item1.awayT.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.cnr" v-if="item1.awayT.cnr == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div v-if="item1.awayT.da == 0" class="detail" style="color: red">
                                            {{item1.awayT.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.da" v-if="item1.awayT.da > 0" class="detail" style="color: green">
                                            {{item1.awayT.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.poss" v-if="item1.awayT.poss == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.poss" v-if="item1.awayT.poss == 0" class="detail" style="color: red">
                                            0
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.poss" v-if="item1.awayT.poss != 0 && item1.awayT.poss != null" class="detail" style="color: green">
                                            {{item1.awayT.poss}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.red" v-if="item1.awayT.red == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.red" v-if="item1.awayT.red == 0" class="detail" style="color: red">
                                            0
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.awayT.red" v-if="item1.awayT.red > 0" class="detail" style="color: green">
                                            {{item1.awayT.red}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div class="detail" style="color: green">
                                            -
                                        </div>
                                    </transition>
                                </div>
                            </div>
                            <div class="detail_total" style="width: 26%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.on" v-if="item1.away.on == null" class="detail" style="color: red;">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.on" v-if="item1.away.on != null" class="detail" style="color: green;">
                                            {{item1.away.on}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.off" v-if="item1.away.off == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.off" v-if="item1.away.off != null" class="detail" style="color: green">
                                            {{item1.away.off}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.blk" v-if="item1.away.blk > 0" class="detail" style="color: green">
                                            {{item1.away.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.blk" v-if="item1.away.blk == 0" class="detail" style="color: red">
                                            {{item1.away.blk}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.blk" v-if="item1.away.blk == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.in" v-if="item1.away.in == 0" class="detail" style="color: red">
                                            {{item1.away.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.in" v-if="item1.away.in > 0" class="detail" style="color: green;">
                                            {{item1.away.in}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.in" v-if="item1.away.in == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.out" v-if="item1.away.out == 0" class="detail" style="color: red">
                                            {{item1.away.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.out" v-if="item1.away.out > 0" class="detail" style="color: green">
                                            {{item1.away.out}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.out" v-if="item1.away.out == null" class="detail">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.cnr" v-if="item1.away.cnr == 0" class="detail" style="color: red">
                                            {{item1.away.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.cnr" v-if="item1.away.cnr > 0" class="detail" style="color: green">
                                            {{item1.away.cnr}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.cnr" v-if="item1.away.cnr == null" class="detail">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div v-if="item1.away.da == 0" class="detail" style="color: red">
                                            {{item1.away.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.da" v-if="item1.away.da > 0" class="detail" style="color: green">
                                            {{item1.away.da}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.poss" v-if="item1.away.poss == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.poss" v-if="item1.away.poss == 0" class="detail" style="color: red">
                                            0
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.poss" v-if="item1.away.poss != null && item1.away.poss != 0" class="detail" style="color: green">
                                            {{item1.away.poss}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.goal" v-if="item1.away.goal == null" class="detail" style="color: red">
                                            -
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div :key="item1.away.poss" v-if="item1.away.goal != null" class="detail" style="color: green">
                                            {{item1.away.goal}}
                                        </div>
                                    </transition>
                                    <transition name="slide-fade" mode="out-in">
                                        <div class="detail" style="color: green">
                                            -
                                        </div>
                                    </transition>
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.pas" v-if="item1.away.pas == null" class="detail">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.pas" v-if="item1.away.pas == 0" class="detail">-->
                                    <!--                                                0-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.pas" v-if="item1.away.pas > 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.pas}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.acc" v-if="item1.away.acc == null" class="detail">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.acc" v-if="item1.away.acc == 0" class="detail">-->
                                    <!--                                                0-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.acc" v-if="item1.away.acc > 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.acc}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.atk" v-if="item1.away.atk == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.atk" v-if="item1.away.atk == 0" class="detail" style="color: red">-->
                                    <!--                                                {{item1.away.atk}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.atk" v-if="item1.away.atk > 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.atk}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.ofs" v-if="item1.away.ofs == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.ofs" v-if="item1.away.ofs == 0" class="detail" style="color: red">-->
                                    <!--                                                0-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.ofs" v-if="item1.away.ofs > 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.ofs}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.sav" v-if="item1.away.sav == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.sav" v-if="item1.away.sav == 0" class="detail" style="color: red">-->
                                    <!--                                                0-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.sav" v-if="item1.away.sav > 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.sav}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.sbst" v-if="item1.away.sbst == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.sbst" v-if="item1.away.sbst >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.sbst}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.red" v-if="item1.away.red == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.red" v-if="item1.away.red >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.red}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.fou" v-if="item1.away.fou == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.fou" v-if="item1.away.fou >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.fou}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.g_att" v-if="item1.away.g_att == null" class="detail" style="color: red; min-width: 30px;">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.g_att" v-if="item1.away.g_att >= 0" class="detail" style="color: green; min-width: 30px;">-->
                                    <!--                                                {{item1.away.g_att}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.safe" v-if="item1.away.safe == null" class="detail" style="color: red">-->
                                    <!--                                                - -->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                    <!--                                        <transition name="slide-fade" mode="out-in">-->
                                    <!--                                            <div :key="item1.away.safe" v-if="item1.away.safe >= 0" class="detail" style="color: green">-->
                                    <!--                                                {{item1.away.safe}}-->
                                    <!--                                            </div>-->
                                    <!--                                        </transition>-->
                                </div>
                            </div>
                            <div style="width: 10%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                <div style="width: 100%; padding: 3px 7px; color: white;">
                                    ...
                                </div>
                            </div>
                            <div style="width: 18%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                <div style="width: 100%; padding: 3px 7px; color: white;">
                                    ...
                                </div>
                            </div>
                            <!--  home team data part  last 10 minutes-->
                            <CCollapse
                                    :show="isCollapsed1(item1.index0)" class="mt-0"
                            >
<<<<<<< HEAD
                                <div class = "bottom-part bottom-part1">
                                    <div class="header" style="width: 100%; height: 50px;">
                                        <div class="header-content detail_total" style="width: 25.5%; height: 50px; float: left; border-left: 1px solid whitesmoke">
=======
                                <div class = "bottom-part">
                                    <div class="header" style="width: 100%; height: 50px;">
                                        <div class="header-content" style="width: 15%; height: 50px; float: left; text-align: left; color: #ffffff; background: #ffffff;">
                                            .
                                        </div>
                                        <div class="header-content detail_total" style="width: 22.5%; height: 50px; float: left; border-left: 1px solid whitesmoke">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                            More info Total
                                            <div style="width: 100%">
                                                <div class="detail">
                                                    Pas
                                                </div>
                                                <div class="detail">
                                                    Acc
                                                </div>
                                                <div class="detail">
                                                    Atk
                                                </div>
                                                <div class="detail">
                                                    Ofs
                                                </div>
                                                <div class="detail">
                                                    Sav
                                                </div>
                                                <div class="detail">
                                                    Sbst
                                                </div>
                                                <div class="detail">
                                                    Fou
                                                </div>
                                                <div class="detail" style="min-width: 30px;">
                                                    G_att
                                                </div>
                                                <div class="detail">
                                                    Safe
                                                </div>
                                            </div>
                                        </div>
<<<<<<< HEAD
                                        <div class="header-content detail_total" style="width: 24%; height: 50px; float: left; border-left: 1px solid whitesmoke">
=======
                                        <div class="header-content detail_total" style="width: 20%; height: 50px; float: left; border-left: 1px solid whitesmoke">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                            Total Indexes
                                            <div style="width: 100%">
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    TSM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    STPM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    BS
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    C
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px; min-width: 32px;">
                                                    DAPM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    SA
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    PA
                                                </div>
                                            </div>
                                        </div>
<<<<<<< HEAD
                                        <div class="header-content detail_total" style="width: 26.5%; height: 50px; float: left; border-left: 1px solid whitesmoke">
=======
                                        <div class="header-content detail_total" style="width: 22.5%; height: 50px; float: left; border-left: 1px solid whitesmoke">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                            More info last 10 minutes
                                            <div style="width: 100%">
                                                <div class="detail">
                                                    Pas
                                                </div>
                                                <div class="detail">
                                                    Acc
                                                </div>
                                                <div class="detail">
                                                    Atk
                                                </div>
                                                <div class="detail">
                                                    Ofs
                                                </div>
                                                <div class="detail">
                                                    Sav
                                                </div>
                                                <div class="detail">
                                                    Sbst
                                                </div>
                                                <div class="detail">
                                                    Fou
                                                </div>
                                                <div class="detail" style="min-width: 30px;">
                                                    G_att
                                                </div>
                                                <div class="detail">
                                                    Safe
                                                </div>
                                            </div>
                                        </div>
<<<<<<< HEAD
                                        <div class="header-content" style="width: 24%; height: 50px; float: left; border-left: 1px solid whitesmoke">
=======
                                        <div class="header-content" style="width: 20%; height: 50px; float: left; border-left: 1px solid whitesmoke">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                            Last 10 minutes Indexes
                                            <div style="width: 100%">
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    TSM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    STPM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    BS
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    C
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px; min-width: 32px;">
                                                    DAPM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    SA
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    PA
                                                </div>
                                            </div>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 25.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
=======
                                    <div style="width: 15%; height: 30px; float: left;">
                                        <div class="time_manner" style="width: 60px; float: left;position: relative; top:  23px; left: 15px; font-size: 17px; font-weight: normal"></div>
                                    </div>
                                    <div class="detail_total" style="width: 22.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.pas" v-if="item1.homeT.pas == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.pas" v-if="item1.homeT.pas == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.pas" v-if="item1.homeT.pas != null && item1.homeT.pas != 0" class="detail" style="color: green">
                                                    {{item1.homeT.pas}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.acc" v-if="item1.homeT.acc == 0" class="detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.acc" v-if="item1.homeT.acc == null" class="detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.acc" v-if="item1.homeT.acc != 0 && item1.homeT.acc != null" class="detail" style="color: green">
                                                    {{item1.homeT.acc}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.atk" v-if="item1.homeT.atk == 0" class="detail" style="color: red">
                                                    {{item1.homeT.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.atk" v-if="item1.homeT.atk == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.atk" v-if="item1.homeT.atk != 0 && item1.homeT.atk != null" class="detail" style="color: green">
                                                    {{item1.homeT.atk}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.ofs" v-if="item1.homeT.ofs == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.ofs" v-if="item1.homeT.ofs == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.ofs" v-if="item1.homeT.ofs != 0 && item1.homeT.ofs != null" class="detail" style="color: green">
                                                    {{item1.homeT.ofs}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.sav" v-if="item1.homeT.sav == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.sav" v-if="item1.homeT.sav == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.sav" v-if="item1.homeT.sav != 0 && item1.homeT.sav != null" class="detail" style="color: green">
                                                    {{item1.homeT.sav}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.sbst" v-if="item1.homeT.sbst == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.sbst" v-if="item1.homeT.sbst == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.sbst" v-if="item1.homeT.sbst != 0 && item1.homeT.sbst != null" class="detail" style="color: green">
                                                    {{item1.homeT.sbst}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.fou" v-if="item1.homeT.fou == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.fou" v-if="item1.homeT.fou == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.fou" v-if="item1.homeT.fou != 0 && item1.homeT.fou != null" class="detail" style="color: green">
                                                    {{item1.homeT.fou}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.g_att" v-if="item1.homeT.g_att == null" class="detail" style="color: red; min-width: 30px;">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.g_att" v-if="item1.homeT.g_att == 0" class="detail" style="color: red; min-width: 30px;">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.g_att" v-if="item1.homeT.g_att != 0 && item1.homeT.g_att != null" class="detail" style="color: green; min-width: 30px;">
                                                    {{item1.homeT.g_att}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.safe" v-if="item1.homeT.safe == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.safe" v-if="item1.homeT.safe == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.homeT.safe" v-if="item1.homeT.safe != 0 && item1.homeT.safe != null" class="detail" style="color: green">
                                                    {{item1.homeT.safe}}
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 24%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
=======
                                    <div class="detail_total" style="width: 20%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time != 'HT'" :key="(item1.homeT.on + item1.homeT.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.homeT.on) + parseInt(item1.homeT.off))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time == 'HT'" :key="(item1.homeT.on + item1.homeT.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.homeT.on) + parseInt(item1.homeT.off))/45).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time == 'HT'" :key="item1.homeT.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.homeT.on))/45).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time != 'HT'" :key="item1.homeT.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.homeT.on))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.blk != null && parseInt(item1.awayT.on) + parseInt(item1.awayT.off) != 0" :key="((parseInt(item1.homeT.blk))/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.homeT.blk))/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.blk != null && parseInt(item1.awayT.on) + parseInt(item1.awayT.off) == 0" :key="((parseInt(item1.homeT.blk))/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.blk == null" :key="item1.homeT.blk" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.on != 0" :key="(parseInt(item1.home.score))/parseInt(item1.homeT.on)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.score))/parseInt(item1.homeT.on)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.on == 0" :key="(parseInt(item1.home.score))/parseInt(item1.homeT.on)" class="detail index_detail" style="color: green;">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time != 'HT'" :key="item1.home.cnr" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.homeT.da))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time == 'HT'" :key="item1.home.cnr" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.homeT.da))/45).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)) != 0" :key="(parseInt(item1.homeT.on)/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.homeT.on)/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)) == 0" :key="(parseInt(item1.homeT.on)/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.pas != 0 && item1.homeT.pas != null" :key="(parseInt(item1.homeT.on)/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.homeT.acc)/parseInt(item1.homeT.pas)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.pas === 0 && item1.homeT.pas != null" :key="(parseInt(item1.homeT.on)/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.homeT.pas == null" :key="(parseInt(item1.homeT.on)/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off)))" class="detail index_detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 26.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
=======
                                    <div class="detail_total" style="width: 22.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.pas" v-if="item1.home.pas == null" class="detail">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.pas" v-if="item1.home.pas == 0" class="detail">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.pas" v-if="item1.home.pas > 0" class="detail" style="color: green">
                                                    {{item1.home.pas}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.acc" v-if="item1.home.acc == null" class="detail">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.acc" v-if="item1.home.acc == 0" class="detail">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.acc" v-if="item1.home.acc > 0" class="detail" style="color: green">
                                                    {{item1.home.acc}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.atk" v-if="item1.home.atk == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.atk" v-if="item1.home.atk == 0" class="detail" style="color: red">
                                                    {{item1.home.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.atk" v-if="item1.home.atk > 0" class="detail" style="color: green">
                                                    {{item1.home.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.ofs" v-if="item1.home.ofs == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.ofs" v-if="item1.home.ofs == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.ofs" v-if="item1.home.ofs > 0" class="detail" style="color: green">
                                                    {{item1.home.ofs}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.sav" v-if="item1.home.sav == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.sav" v-if="item1.home.sav == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.sav" v-if="item1.home.sav > 0" class="detail" style="color: green">
                                                    {{item1.home.sav}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.sbst" v-if="item1.home.sbst == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.sbst" v-if="item1.home.sbst >= 0" class="detail" style="color: green">
                                                    {{item1.home.sbst}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.fou" v-if="item1.home.fou == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.fou" v-if="item1.home.fou >= 0" class="detail" style="color: green">
                                                    {{item1.home.fou}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.g_att" v-if="item1.home.g_att == null" class="detail" style="color: red; min-width: 30px;">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.g_att" v-if="item1.home.g_att >= 0" class="detail" style="color: green; min-width: 30px;">
                                                    {{item1.home.g_att}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.safe" v-if="item1.home.safe == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home.safe" v-if="item1.home.safe >= 0" class="detail" style="color: green">
                                                    {{item1.home.safe}}
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 24%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
=======
                                    <div class="detail_total" style="width: 20%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="(item1.home.on + item1.home.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.on) + parseInt(item1.home.off))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="(item1.home.on + item1.home.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.on) + parseInt(item1.home.off))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(item1.home.on + item1.home.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.on) + parseInt(item1.home.off))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="item1.home.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.on))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="item1.home.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.on))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="item1.home.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.on))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.away.on) + parseInt(item1.away.off) != 0 && item1.home.blk != null" :key="((parseInt(item1.home.blk))/(parseInt(item1.away.on)+ parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.blk))/(parseInt(item1.away.on) + parseInt(item1.away.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.away.on) + parseInt(item1.away.off) == 0 && item1.home.blk != null" :key="((parseInt(item1.home.blk))/(parseInt(item1.away.on)+ parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.blk == null" :key="item1.home.blk" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.on != 0" :key="(parseInt(item1.home.score))/parseInt(item1.home.on)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.goal))/parseInt(item1.home.on)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.on == 0" :key="(parseInt(item1.home.score))/parseInt(item1.home.on)" class="detail index_detail" style="color: green;">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="((parseInt(item1.home.da))/parseInt(item1.home.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.da))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="((parseInt(item1.home.da))/parseInt(item1.home.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(parseInt(item1.home.da))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.home.on) + parseInt(item1.home.off)) != 0" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.home.on) + parseInt(item1.home.off)) == 0" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.pas != 0 && item1.home.pas != null" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.home.acc)/parseInt(item1.home.pas)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.pas == 0 && item1.home.pas != null" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.pas == null" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
                                    <!--  away team data part  last 10 minutes-->
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 25.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
=======
                                    <div style="width: 15%; height: 30px; float: left; border-bottom: 1px solid lightgray;">
                                        <div style="width: 60px; float: left; color: white;">.</div>
                                    </div>
                                    <div class="detail_total" style="width: 22.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.pas" v-if="item1.awayT.pas == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.pas" v-if="item1.awayT.pas == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.pas" v-if="item1.awayT.pas > 0" class="detail" style="color: green">
                                                    {{item1.awayT.pas}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.acc" v-if="item1.awayT.acc == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.acc" v-if="item1.awayT.acc == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.acc" v-if="item1.awayT.acc > 0" class="detail" style="color: green">
                                                    {{item1.awayT.acc}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.atk" v-if="item1.awayT.atk == 0" class="detail" style="color: red">
                                                    {{item1.awayT.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.atk" v-if="item1.awayT.atk > 0" class="detail" style="color: green">
                                                    {{item1.awayT.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.ofs" v-if="item1.awayT.ofs == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.ofs" v-if="item1.awayT.ofs == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.ofs" v-if="item1.awayT.ofs > 0" class="detail" style="color: green">
                                                    {{item1.awayT.ofs}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.sav" v-if="item1.awayT.sav == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.sav" v-if="item1.awayT.sav == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.sav" v-if="item1.awayT.sav > 0" class="detail" style="color: green">
                                                    {{item1.awayT.sav}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.sbst" v-if="item1.awayT.sbst == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.sbst" v-if="item1.awayT.sbst == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.sbst" v-if="item1.awayT.sbst > 0" class="detail" style="color: green">
                                                    {{item1.awayT.sbst}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.fou" v-if="item1.awayT.fou == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.fou" v-if="item1.awayT.fou == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.fou" v-if="item1.awayT.fou > 0" class="detail" style="color: green">
                                                    {{item1.awayT.fou}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.g_att" v-if="item1.awayT.g_att == null" class="detail" style="color: red; min-width: 30px;">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.g_att" v-if="item1.awayT.g_att == 0" class="detail" style="color: red; min-width: 30px;">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.g_att" v-if="item1.awayT.g_att > 0" class="detail" style="color: green; min-width: 30px;">
                                                    {{item1.awayT.g_att}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.safe" v-if="item1.awayT.safe == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.safe" v-if="item1.awayT.safe == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.awayT.safe" v-if="item1.awayT.safe > 0" class="detail" style="color: green">
                                                    {{item1.awayT.safe}}
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 24%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
=======
                                    <div class="detail_total" style="width: 20%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time != 'HT'" :key="((parseInt(item1.awayT.on) + parseInt(item1.awayT.off))/parseInt(item1.home.time))" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.awayT.on) + parseInt(item1.awayT.off))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time == 'HT'" :key="(item1.awayT.on + item1.awayT.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.awayT.on) + parseInt(item1.awayT.off))/45).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time == 'HT'" :key="item1.homeT.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.awayT.on))/45).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time != 'HT'" :key="item1.awayT.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.awayT.on))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.blk != null && parseInt(item1.homeT.on) + parseInt(item1.homeT.off) != 0" :key="((parseInt(item1.homeT.blk))/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.awayT.blk))/(parseInt(item1.homeT.on) + parseInt(item1.homeT.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.blk != null && parseInt(item1.homeT.on) + parseInt(item1.homeT.off) == 0" :key="((parseInt(item1.homeT.blk))/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.blk == null" :key="((parseInt(item1.homeT.blk))/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.on != 0" :key="(parseInt(item1.away.score))/parseInt(item1.awayT.on)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.score))/parseInt(item1.awayT.on)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.on == 0" :key="(parseInt(item1.home.score))/parseInt(item1.awayT.on)" class="detail index_detail" style="color: green;">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time != 'HT'" :key="((parseInt(item1.awayT.da))/parseInt(item1.home.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.awayT.da))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time == 'HT'" :key="((parseInt(item1.awayT.da))/45)" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.awayT.da))/45).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)) != 0" :key="(parseInt(item1.awayT.on)/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.awayT.on)/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)) == 0" :key="(parseInt(item1.awayT.on)/(parseInt(item1.awayT.on) + parseInt(item1.awayT.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.pas != 0 && item1.awayT.pas != null" :key="(parseInt(item1.awayT.acc)/parseInt(item1.awayT.pas))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.awayT.acc)/parseInt(item1.awayT.pas)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.pas === 0 && item1.awayT.pas != null" :key="(parseInt(item1.awayT.acc)/parseInt(item1.awayT.pas))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.awayT.pas == null" :key="(parseInt(item1.awayT.acc)/parseInt(item1.awayT.pas))" class="detail index_detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 26.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
=======
                                    <div class="detail_total" style="width: 22.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.pas" v-if="item1.away.pas == null" class="detail">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.pas" v-if="item1.away.pas == 0" class="detail">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.pas" v-if="item1.away.pas > 0" class="detail" style="color: green">
                                                    {{item1.away.pas}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.acc" v-if="item1.away.acc == null" class="detail">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.acc" v-if="item1.away.acc == 0" class="detail">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.acc" v-if="item1.away.acc > 0" class="detail" style="color: green">
                                                    {{item1.away.acc}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.atk" v-if="item1.away.atk == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.atk" v-if="item1.away.atk == 0" class="detail" style="color: red">
                                                    {{item1.away.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.atk" v-if="item1.away.atk > 0" class="detail" style="color: green">
                                                    {{item1.away.atk}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.ofs" v-if="item1.away.ofs == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.ofs" v-if="item1.away.ofs == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.ofs" v-if="item1.away.ofs > 0" class="detail" style="color: green">
                                                    {{item1.away.ofs}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.sav" v-if="item1.away.sav == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.sav" v-if="item1.away.sav == 0" class="detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.sav" v-if="item1.away.sav > 0" class="detail" style="color: green">
                                                    {{item1.away.sav}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.sbst" v-if="item1.away.sbst == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.sbst" v-if="item1.away.sbst >= 0" class="detail" style="color: green">
                                                    {{item1.away.sbst}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.fou" v-if="item1.away.fou == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.fou" v-if="item1.away.fou >= 0" class="detail" style="color: green">
                                                    {{item1.away.fou}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.g_att" v-if="item1.away.g_att == null" class="detail" style="color: red; min-width: 30px;">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.g_att" v-if="item1.away.g_att >= 0" class="detail" style="color: green; min-width: 30px;">
                                                    {{item1.away.g_att}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.safe" v-if="item1.away.safe == null" class="detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away.safe" v-if="item1.away.safe >= 0" class="detail" style="color: green">
                                                    {{item1.away.safe}}
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total" style="width: 24%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
=======
                                    <div class="detail_total" style="width: 20%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="(item1.away.on + item1.away.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.on) + parseInt(item1.away.off))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="(item1.away.on + item1.away.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.on) + parseInt(item1.away.off))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(item1.away.on + item1.away.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.on) + parseInt(item1.away.off))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="item1.away.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.on))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="item1.away.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.on))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="item1.away.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.on))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.on) + parseInt(item1.home.off) != 0 && item1.away.blk != null" :key="item1.away.blk" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.blk))/(parseInt(item1.home.on) + parseInt(item1.home.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.on) + parseInt(item1.home.off) == 0 && item1.away.blk != null" :key="item1.away.blk" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.blk == null" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.on != 0" :key="(parseInt(item1.away.score))/parseInt(item1.away.on)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.goal))/parseInt(item1.away.on)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.on == 0" :key="(parseInt(item1.away.score))/parseInt(item1.away.on)" class="detail index_detail" style="color: green;">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="((parseInt(item1.away.da))/parseInt(item1.away.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.da))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="((parseInt(item1.away.da))/parseInt(item1.away.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(parseInt(item1.away.da))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.away.on) + parseInt(item1.away.off)) != 0" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.away.on) + parseInt(item1.away.off)) == 0" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.pas != 0 && item1.away.pas != null" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.away.acc)/parseInt(item1.away.pas)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.pas == 0 && item1.away.pas != null" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.pas == null" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
                                </div>
                                <div class = "bottom-part">
                                    <div class="header" style="width: 100%; height: 50px;">
<<<<<<< HEAD
                                        <div class="header-content" style="text-align: center; padding-top: 20px; width: 2.5%; height: 50px; float: left; background: #8db4e2; border-left: 1px solid #ffffff;">
                                            P
                                        </div>
                                        <div class="header-content detail_total" style="width: 42%; height: 50px; float: left; border-left: 1px solid #ffffff; background: #8db4e2">
                                            Avg Stats Per Game
                                            <div class="season-part" style="width: 100%">
                                                <div class="detail season-detail" style="min-width: 30px!important; width: 6.5%!important">
                                                    Goals
                                                </div>
                                                <div class="detail season-detail" style="min-width: 20px!important; width: 4.5%!important">
                                                    On
                                                </div>
                                                <div class="detail season-detail" style="min-width: 20px!important;">
                                                    Off
                                                </div>
                                                <div class="detail season-detail">
                                                    Blk
                                                </div>
                                                <div class="detail season-detail" style="min-width: 20px!important; width: 4.5%!important">
                                                    In
                                                </div>
                                                <div class="detail season-detail">
                                                    Out
                                                </div>
                                                <div class="detail season-detail">
                                                    Cnr
                                                </div>
                                                <div class="detail season-detail">
                                                    DA
                                                </div>
                                                <div class="detail season-detail" style="min-width: 30px;">
                                                    Pos
                                                </div>
                                                <div class="detail season-detail">
                                                    Pas
                                                </div>
                                                <div class="detail season-detail">
                                                    Acc
                                                </div>
                                                <div class="detail season-detail">
                                                    Atk
                                                </div>
                                                <div class="detail season-detail">
                                                    Ofs
                                                </div>
                                                <div class="detail season-detail">
                                                    Sav
                                                </div>
                                                <div class="detail season-detail">
                                                    Sbst
                                                </div>
                                                <div class="detail season-detail">
                                                    Fou
                                                </div>
                                                <div class="detail season-detail" style="min-width: 30px!important; width: 6.5%!important">
                                                    G_att
                                                </div>
                                                <div class="detail season-detail">
                                                    Safe
                                                </div>
                                            </div>
                                        </div>
                                        <div class="header-content detail_total" style="width: 37.5%; height: 50px; float: left; border-left: 1px solid #ffffff; background: #8db4e2">
                                            Total Avg Stats
                                            <div class="season-part" style="width: 100%">
                                                <div class="detail season-detail" style="min-width: 30px!important; width: 6.5%!important">
                                                    Goals
                                                </div>
                                                <div class="detail season-detail" style="min-width: 20px!important; width: 4.5%!important">
                                                    On
                                                </div>
                                                <div class="detail season-detail" style="min-width: 20px!important;">
=======
                                        <div class="header-content" style="width: 15%; height: 50px; float: left; text-align: left; background: #8db4e2; padding-top: 20px;">
                                            H/A
                                        </div>
                                        <div class="header-content" style="text-align: center; padding-top: 20px; width: 5%; height: 50px; float: left; background: #8db4e2; border-left: 1px solid #ffffff;">
                                            P
                                        </div>
                                        <div class="header-content detail_total" style="width: 60%; height: 50px; float: left; border-left: 1px solid #ffffff; background: #8db4e2">
                                            Avg Stats Per Game
                                            <div class="season-part" style="width: 100%">
                                                <div class="detail season-detail">
                                                    On
                                                </div>
                                                <div class="detail season-detail">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    Off
                                                </div>
                                                <div class="detail season-detail">
                                                    Blk
                                                </div>
<<<<<<< HEAD
                                                <div class="detail season-detail" style="min-width: 20px!important; width: 4.5%!important">
=======
                                                <div class="detail season-detail">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    In
                                                </div>
                                                <div class="detail season-detail">
                                                    Out
                                                </div>
                                                <div class="detail season-detail">
                                                    Cnr
                                                </div>
                                                <div class="detail season-detail">
                                                    DA
                                                </div>
<<<<<<< HEAD
                                                <div class="detail season-detail" style="min-width: 30px;">
=======
                                                <div class="detail" season-detail style="min-width: 30px;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    Pos
                                                </div>
                                                <div class="detail season-detail">
                                                    Pas
<<<<<<< HEAD

=======
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                                <div class="detail season-detail">
                                                    Acc
                                                </div>
                                                <div class="detail season-detail">
                                                    Atk
                                                </div>
                                                <div class="detail season-detail">
                                                    Ofs
                                                </div>
                                                <div class="detail season-detail">
                                                    Sav
                                                </div>
                                                <div class="detail season-detail">
                                                    Sbst
                                                </div>
                                                <div class="detail season-detail">
                                                    Fou
                                                </div>
<<<<<<< HEAD
                                                <div class="detail season-detail" style="min-width: 30px!important; width: 6.5%!important">
=======
                                                <div class="detail season-detail" style="min-width: 30px;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    G_att
                                                </div>
                                                <div class="detail season-detail">
                                                    Safe
                                                </div>
                                            </div>
                                        </div>
<<<<<<< HEAD
                                        <div class="header-content" style="width: 18%; height: 50px; float: left; border-left: 1px solid #ffffff; background: #8db4e2">
=======
                                        <div class="header-content" style="width: 20%; height: 50px; float: left; border-left: 1px solid #ffffff; background: #8db4e2">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                            Indexes
                                            <div style="width: 100%">
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    TSM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    STPM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    BS
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    C
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px; min-width: 32px;">
                                                    DAPM
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    SA
                                                </div>
                                                <div class="detail index_detail" style="font-size: 11px!important; padding-top: 2px;">
                                                    PA
                                                </div>
                                            </div>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div style="width: 2.5%; height: 30px; float: left; border-left: 1px solid lightgray;">
                                        <div style="text-align: center;">{{item1.home_p}}</div>
                                    </div>
                                    <div class="detail_total season-stats-part" style="width: 42%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.goals" v-if="item1.home_season.goals == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.goals" v-if="item1.home_season.goals == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.goals" v-if="item1.home_season.goals != 0 && item1.home_season.goals != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.goals/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
=======
                                    <div style="width: 15%; height: 30px; float: left;">
                                        <div class="time_manner" style="width: 60px; float: left;position: relative; top:  23px; left: 15px; font-size: 17px; font-weight: normal"></div>
                                    </div>
                                    <div style="width: 5%; height: 30px; float: left; border-left: 1px solid lightgray;">
                                        <div style="text-align: center;">{{item1.home_p}}</div>
                                    </div>
                                    <div class="detail_total" style="width: 60%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                <div :key="item1.home_season.on" v-if="item1.home_season.on == 0" class="detail season-detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.on" v-if="item1.home_season.on == null" class="detail season-detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.on" v-if="item1.home_season.on != null && item1.home_season.on != 0" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.on/item1.home_p).toFixed(1)}}
=======
                                                    {{item1.home_season.on}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.off" v-if="item1.home_season.off == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.off" v-if="item1.home_season.off == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.off" v-if="item1.home_season.off != 0 && item1.home_season.off != null" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.off/item1.home_p).toFixed(1)}}
=======
                                                    {{item1.home_season.off}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.blk" v-if="item1.home_season.blk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.blk" v-if="item1.home_season.blk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.blk" v-if="item1.home_season.blk != 0 && item1.home_season.blk != null" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.blk/item1.home_p).toFixed(1)}}
=======
                                                    {{item1.home_season.blk}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.in" v-if="item1.home_season.in == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.in" v-if="item1.home_season.in == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.in" v-if="item1.home_season.in != 0 && item1.home_season.in != null" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.in/item1.home_p).toFixed(1)}}
=======
                                                    {{item1.home_season.in}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.out" v-if="item1.home_season.out == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.out" v-if="item1.home_season.out == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.out" v-if="item1.home_season.out != 0 && item1.home_season.out != null" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.out/item1.home_p).toFixed(1)}}
=======
                                                    {{item1.home_season.out}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.cnr" v-if="item1.home_season.cnr == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.cnr" v-if="item1.home_season.cnr == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.cnr" v-if="item1.home_season.cnr != 0 && item1.home_season.cnr != null" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.cnr/item1.home_p).toFixed(1)}}
=======
                                                    {{item1.home_season.cnr}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.da" v-if="item1.home_season.da == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.da" v-if="item1.home_season.da == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.da" v-if="item1.home_season.da != 0 && item1.home_season.da != null" class="detail season-detail" style="color: green">
<<<<<<< HEAD
                                                    {{(item1.home_season.da/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pos" v-if="item1.home_season.pos == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pos" v-if="item1.home_season.pos == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pos" v-if="item1.home_season.pos != 0 && item1.home_season.pos != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.pos/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas != 0 && item1.home_season.pas != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.pas/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc != 0 && item1.home_season.acc != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.acc/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk != 0 && item1.home_season.atk != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.atk/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs != 0 && item1.home_season.ofs != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.ofs/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.sav/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.sbst/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.fou/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att != 0 && item1.home_season.g_att != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.g_att/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe != 0 && item1.home_season.safe != null" class="detail season-detail" style="color: green">
                                                    {{(item1.home_season.safe/item1.home_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                         </div>
                                    </div>
                                    <div class="detail_total season-stats-part" style="width: 37.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.goals" v-if="item1.home_season.goals == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.goals" v-if="item1.home_season.goals == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.goals" v-if="item1.home_season.goals != 0 && item1.home_season.goals != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.goals}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.on" v-if="item1.home_season.on == 0" class="detail season-detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.on" v-if="item1.home_season.on == null" class="detail season-detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.on" v-if="item1.home_season.on != null && item1.home_season.on != 0" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.on}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.off" v-if="item1.home_season.off == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.off" v-if="item1.home_season.off == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.off" v-if="item1.home_season.off != 0 && item1.home_season.off != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.off}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.blk" v-if="item1.home_season.blk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.blk" v-if="item1.home_season.blk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.blk" v-if="item1.home_season.blk != 0 && item1.home_season.blk != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.blk}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.in" v-if="item1.home_season.in == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.in" v-if="item1.home_season.in == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.in" v-if="item1.home_season.in != 0 && item1.home_season.in != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.in}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.out" v-if="item1.home_season.out == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.out" v-if="item1.home_season.out == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.out" v-if="item1.home_season.out != 0 && item1.home_season.out != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.out}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.cnr" v-if="item1.home_season.cnr == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.cnr" v-if="item1.home_season.cnr == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.cnr" v-if="item1.home_season.cnr != 0 && item1.home_season.cnr != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.cnr}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.da" v-if="item1.home_season.da == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.da" v-if="item1.home_season.da == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.da" v-if="item1.home_season.da != 0 && item1.home_season.da != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.da}}
=======
                                                    {{item1.home_season.da}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pos" v-if="item1.home_season.pos == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pos" v-if="item1.home_season.pos == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pos" v-if="item1.home_season.pos != 0 && item1.home_season.pos != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.pos}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas != 0 && item1.home_season.pas != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.pas}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc != 0 && item1.home_season.acc != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.acc}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk != 0 && item1.home_season.atk != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.atk}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs != 0 && item1.home_season.ofs != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.ofs}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.sav}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.sbst}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.fou}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att != 0 && item1.home_season.g_att != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.g_att}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe != 0 && item1.home_season.safe != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.safe}}
                                                </div>
                                            </transition>

                                        </div>
                                    </div>
                                    <div class="detail_total season-stats-part" style="width: 18%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.on + item1.home_season.off)/90/item1.home_p).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.on)/90/item1.home_p).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home_season.blk" class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.blk)/item1.home_p).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="!item1.home_season.blk" class="detail index_detail" style="color: green;">
                                                    -
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.goals)/(item1.home_season.on)).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.da)/90/item1.home_p).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.on)/(item1.home_season.on + item1.home_season.off)).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.home_season.acc)/(item1.home_season.pas)).toFixed(2)}}
                                                </div>
                                            </transition>

                                        </div>
                                    </div>
                                    <!--  away team data part  last 10 minutes-->
                                    <div style="width: 2.5%; height: 30px; float: left; border-bottom: 1px solid lightgray; border-left: 1px solid lightgray;">
                                        <div style="text-align: center;">{{item1.away_p}}</div>
                                    </div>
                                    <div class="detail_total season-stats-part" style="width: 42%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.goals" v-if="item1.away_season.goals == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.goals" v-if="item1.away_season.goals == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.goals" v-if="item1.away_season.goals != 0 && item1.home_season.goals != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.goals/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.on" v-if="item1.away_season.on == 0" class="detail season-detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.on" v-if="item1.away_season.on == null" class="detail season-detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.on" v-if="item1.away_season.on != null && item1.home_season.on != 0" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.on/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.off" v-if="item1.away_season.off == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.off" v-if="item1.away_season.off == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.off" v-if="item1.away_season.off != 0 && item1.away_season.off != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.off/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.blk" v-if="item1.away_season.blk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.blk" v-if="item1.away_season.blk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.blk" v-if="item1.away_season.blk != 0 && item1.home_season.blk != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.blk/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.in" v-if="item1.away_season.in == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.in" v-if="item1.away_season.in == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.in" v-if="item1.away_season.in != 0 && item1.away_season.in != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.in/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.pas" v-if="item1.home_season.pas != 0 && item1.home_season.pas != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.pas}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.out" v-if="item1.away_season.out == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.out" v-if="item1.away_season.out == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.out" v-if="item1.away_season.out != 0 && item1.away_season.out != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.out/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.acc" v-if="item1.home_season.acc != 0 && item1.home_season.acc != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.acc}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.cnr" v-if="item1.away_season.cnr == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.cnr" v-if="item1.away_season.cnr == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.cnr" v-if="item1.away_season.cnr != 0 && item1.away_season.cnr != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.cnr/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.atk" v-if="item1.home_season.atk != 0 && item1.home_season.atk != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.atk}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.da" v-if="item1.away_season.da == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.da" v-if="item1.away_season.da == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.da" v-if="item1.away_season.da != 0 && item1.away_season.da != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.da/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.ofs" v-if="item1.home_season.ofs != 0 && item1.home_season.ofs != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.ofs}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.pos" v-if="item1.away_season.pos == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.pos" v-if="item1.away_season.pos == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.pos" v-if="item1.away_season.pos != 0 && item1.away_season.pos != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.pos/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.sav" v-if="item1.home_season.sav != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.sav}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.pas" v-if="item1.away_season.pas == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.pas" v-if="item1.away_season.pas == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.pas" v-if="item1.away_season.pas != 0 && item1.away_season.pas != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.pas/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.sbst" v-if="item1.home_season.sbst != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.sbst}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.acc" v-if="item1.away_season.acc == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.acc" v-if="item1.away_season.acc == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.acc" v-if="item1.away_season.acc != 0 && item1.away_season.acc != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.acc/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.fou" v-if="item1.home_season.fou != 0 && item1.home_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.fou}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.atk" v-if="item1.away_season.atk == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.atk" v-if="item1.away_season.atk == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.atk" v-if="item1.away_season.atk != 0 && item1.away_season.atk != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.atk/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.g_att" v-if="item1.home_season.g_att != 0 && item1.home_season.g_att != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.g_att}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.ofs" v-if="item1.away_season.ofs == 0" class="detail season-detail"  style="color: red">
=======
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe == 0" class="detail season-detail"  style="color: red">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.ofs" v-if="item1.away_season.ofs == null" class="detail season-detail" >
=======
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe == null" class="detail season-detail" >
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.ofs" v-if="item1.away_season.ofs != 0 && item1.away_season.ofs != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.ofs/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sav" v-if="item1.away_season.sav == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sav" v-if="item1.away_season.sav == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sav" v-if="item1.away_season.sav != 0 && item1.away_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.sav/item1.away_p).toFixed(1)}}
=======
                                                <div :key="item1.home_season.safe" v-if="item1.home_season.safe != 0 && item1.home_season.safe != null" class="detail season-detail" style="color: green">
                                                    {{item1.home_season.safe}}
                                                </div>
                                            </transition>

                                         </div>
                                    </div>
                                    <div class="detail_total" style="width: 20%; height: 30px; float: left; border-left: 1px solid #e2e2e2;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="(item1.home.on + item1.home.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.on) + parseInt(item1.home.off))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="(item1.home.on + item1.home.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.on) + parseInt(item1.home.off))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(item1.home.on + item1.home.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.on) + parseInt(item1.home.off))/10).toFixed(2)}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.sbst" v-if="item1.away_season.sbst == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sbst" v-if="item1.away_season.sbst == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sbst" v-if="item1.away_season.sbst != 0 && item1.away_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.sbst/item1.away_p).toFixed(1)}}
=======
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="item1.home.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.on))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="item1.home.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.on))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="item1.home.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.on))/10).toFixed(2)}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.fou" v-if="item1.away_season.fou == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.fou" v-if="item1.away_season.fou == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.fou" v-if="item1.away_season.fou != 0 && item1.away_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.fou/item1.away_p).toFixed(1)}}
=======
                                                <div v-if="parseInt(item1.away.on) + parseInt(item1.away.off) != 0 && item1.home.blk != null" :key="((parseInt(item1.home.blk))/(parseInt(item1.away.on)+ parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.blk))/(parseInt(item1.away.on) + parseInt(item1.away.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.away.on) + parseInt(item1.away.off) == 0 && item1.home.blk != null" :key="((parseInt(item1.home.blk))/(parseInt(item1.away.on)+ parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.blk == null" :key="item1.home.blk" class="detail index_detail" style="color: green">
                                                    -
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div :key="item1.away_season.g_att" v-if="item1.away_season.g_att == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.g_att" v-if="item1.away_season.g_att == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.g_att" v-if="item1.away_season.g_att != 0 && item1.away_season.g_att != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.g_att/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.safe" v-if="item1.away_season.safe == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.safe" v-if="item1.away_season.safe == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.safe" v-if="item1.away_season.safe != 0 && item1.away_season.safe != null" class="detail season-detail" style="color: green">
                                                    {{(item1.away_season.safe/item1.away_p).toFixed(1)}}
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
                                    <div class="detail_total season-stats-part" style="width: 37.5%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.goals" v-if="item1.away_season.goals == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.goals" v-if="item1.away_season.goals == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.goals" v-if="item1.away_season.goals != 0 && item1.home_season.goals != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.goals}}
                                                </div>
                                            </transition>

=======
                                                <div v-if="item1.home.on != 0" :key="(parseInt(item1.home.score))/parseInt(item1.home.on)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.home.goal))/parseInt(item1.home.on)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.on == 0" :key="(parseInt(item1.home.score))/parseInt(item1.home.on)" class="detail index_detail" style="color: green;">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="((parseInt(item1.home.da))/parseInt(item1.home.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.da))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="((parseInt(item1.home.da))/parseInt(item1.home.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(parseInt(item1.home.da))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.home.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.home.on) + parseInt(item1.home.off)) != 0" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.home.on) + parseInt(item1.home.off)) == 0" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.pas != 0 && item1.home.pas != null" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.home.acc)/parseInt(item1.home.pas)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.pas == 0 && item1.home.pas != null" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.pas == null" :key="(parseInt(item1.home.on)/(parseInt(item1.home.on) + parseInt(item1.home.off)))" class="detail index_detail" style="color: green">
                                                    -
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
                                    <!--  away team data part  last 10 minutes-->
                                    <div style="width: 15%; height: 30px; float: left; border-bottom: 1px solid lightgray;">
                                        <div style="width: 60px; float: left; color: white;">.</div>
                                    </div>
                                    <div style="width: 5%; height: 30px; float: left; border-bottom: 1px solid lightgray; border-left: 1px solid lightgray;">
                                        <div style="text-align: center;">{{item1.away_p}}</div>
                                    </div>
                                    <div class="detail_total" style="width: 60%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.on" v-if="item1.away_season.on == 0" class="detail season-detail" style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.on" v-if="item1.away_season.on == null" class="detail season-detail" style="color: red">
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.on" v-if="item1.away_season.on != null && item1.home_season.on != 0" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.on}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.off" v-if="item1.away_season.off == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.off" v-if="item1.away_season.off == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.off" v-if="item1.away_season.off != 0 && item1.away_season.off != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.off}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.blk" v-if="item1.away_season.blk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.blk" v-if="item1.away_season.blk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.blk" v-if="item1.away_season.blk != 0 && item1.home_season.blk != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.blk}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.in" v-if="item1.away_season.in == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.in" v-if="item1.away_season.in == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.in" v-if="item1.away_season.in != 0 && item1.away_season.in != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.in}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.out" v-if="item1.away_season.out == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.out" v-if="item1.away_season.out == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.out" v-if="item1.away_season.out != 0 && item1.away_season.out != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.out}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.cnr" v-if="item1.away_season.cnr == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.cnr" v-if="item1.away_season.cnr == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.cnr" v-if="item1.away_season.cnr != 0 && item1.away_season.cnr != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.cnr}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.da" v-if="item1.away_season.da == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.da" v-if="item1.away_season.da == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.da" v-if="item1.away_season.da != 0 && item1.away_season.da != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.da}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.pos" v-if="item1.away_season.pos == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.pos" v-if="item1.away_season.pos == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.pos" v-if="item1.away_season.pos != 0 && item1.away_season.pos != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.pos}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.pas" v-if="item1.away_season.pas == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.pas" v-if="item1.away_season.pas == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.pas" v-if="item1.away_season.pas != 0 && item1.away_season.pas != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.pas}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.acc" v-if="item1.away_season.acc == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.acc" v-if="item1.away_season.acc == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.acc" v-if="item1.away_season.acc != 0 && item1.away_season.acc != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.acc}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.atk" v-if="item1.away_season.atk == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.atk" v-if="item1.away_season.atk == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.atk" v-if="item1.away_season.atk != 0 && item1.away_season.atk != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.atk}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.ofs" v-if="item1.away_season.ofs == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.ofs" v-if="item1.away_season.ofs == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.ofs" v-if="item1.away_season.ofs != 0 && item1.away_season.ofs != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.ofs}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sav" v-if="item1.away_season.sav == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sav" v-if="item1.away_season.sav == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sav" v-if="item1.away_season.sav != 0 && item1.away_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.sav}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sbst" v-if="item1.away_season.sbst == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sbst" v-if="item1.away_season.sbst == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.sbst" v-if="item1.away_season.sbst != 0 && item1.away_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.sbst}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.fou" v-if="item1.away_season.fou == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.fou" v-if="item1.away_season.fou == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.fou" v-if="item1.away_season.fou != 0 && item1.away_season.sav != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.fou}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.g_att" v-if="item1.away_season.g_att == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.g_att" v-if="item1.away_season.g_att == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.g_att" v-if="item1.away_season.g_att != 0 && item1.away_season.g_att != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.g_att}}
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.safe" v-if="item1.away_season.safe == 0" class="detail season-detail"  style="color: red">
                                                    0
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.safe" v-if="item1.away_season.safe == null" class="detail season-detail" >
                                                    -
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div :key="item1.away_season.safe" v-if="item1.away_season.safe != 0 && item1.away_season.safe != null" class="detail season-detail" style="color: green">
                                                    {{item1.away_season.safe}}
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
<<<<<<< HEAD
                                    <div class="detail_total season-stats-part" style="width: 18%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.on + item1.away_season.off)/90/item1.away_p).toFixed(2)}}
=======
                                    <div class="detail_total" style="width: 20%; height: 30px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray;">
                                        <div style="width: 100%; padding: 3px 7px; color: black;">
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="(item1.away.on + item1.away.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.on) + parseInt(item1.away.off))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="(item1.away.on + item1.away.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.on) + parseInt(item1.away.off))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(item1.away.on + item1.away.off)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.on) + parseInt(item1.away.off))/10).toFixed(2)}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.on)/90/item1.away_p).toFixed(2)}}
=======
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="item1.away.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.on))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="item1.away.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.on))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="item1.away.on" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.on))/10).toFixed(2)}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div v-if="item1.away_season.blk" class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.blk)/item1.away_p).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="!item1.away_season.blk" class="detail index_detail" style="color: green;">
=======
                                                <div v-if="parseInt(item1.home.on) + parseInt(item1.home.off) != 0 && item1.away.blk != null" :key="item1.away.blk" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.blk))/(parseInt(item1.home.on) + parseInt(item1.home.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.on) + parseInt(item1.home.off) == 0 && item1.away.blk != null" :key="item1.away.blk" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.blk == null" class="detail index_detail" style="color: green">
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                    -
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.goals)/(item1.away_season.on)).toFixed(2)}}
=======
                                                <div v-if="item1.away.on != 0" :key="(parseInt(item1.away.score))/parseInt(item1.away.on)" class="detail index_detail" style="color: green;">
                                                    {{((parseInt(item1.away.goal))/parseInt(item1.away.on)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.on == 0" :key="(parseInt(item1.away.score))/parseInt(item1.away.on)" class="detail index_detail" style="color: green;">
                                                    0.00
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.da)/90/item1.away_p).toFixed(2)}}
=======
                                                <div v-if="parseInt(item1.home.time) < 10 && item1.home.time != 'HT'" :key="((parseInt(item1.away.da))/parseInt(item1.away.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.da))/parseInt(item1.home.time)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="parseInt(item1.home.time) >= 10 && item1.home.time != 'HT'" :key="((parseInt(item1.away.da))/parseInt(item1.away.time))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.da))/10).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.home.time === 'HT'" :key="(parseInt(item1.away.da))" class="detail index_detail" style="color: green">
                                                    {{((parseInt(item1.away.da))/10).toFixed(2)}}
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.on)/(item1.away_season.on + item1.away_season.off)).toFixed(2)}}
=======
                                                <div v-if="(parseInt(item1.away.on) + parseInt(item1.away.off)) != 0" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off))).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="(parseInt(item1.away.on) + parseInt(item1.away.off)) == 0" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    0.00
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>

                                            <transition name="slide-fade" mode="out-in">
<<<<<<< HEAD
                                                <div class="detail index_detail" style="color: green;">
                                                    {{((item1.away_season.acc)/(item1.away_season.pas)).toFixed(2)}}
=======
                                                <div v-if="item1.away.pas != 0 && item1.away.pas != null" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    {{(parseInt(item1.away.acc)/parseInt(item1.away.pas)).toFixed(2)}}
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.pas == 0 && item1.away.pas != null" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    0.00
                                                </div>
                                            </transition>
                                            <transition name="slide-fade" mode="out-in">
                                                <div v-if="item1.away.pas == null" :key="(parseInt(item1.away.on)/(parseInt(item1.away.on) + parseInt(item1.away.off)))" class="detail index_detail" style="color: green">
                                                    -
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                </div>
                                            </transition>
                                        </div>
                                    </div>
                                </div>
                            </CCollapse>
                        </div>
                    </div>
                </CTab>
                <CTab :title="'Finished Games('+finishedLength+')'">
                    <div v-for="item in finishedArray" :key="item.league" class="finished-tab">
                        <div v-if="item.events.length > 0 && item.league"  class="header" style="width: 50%; height: 50px;">
                            <div class="header-content" style="width: 30%; height: 50px; float: left; text-align: left;">
                                {{item.league}}
                            </div>
                            <div class="header-content" style="width: 55%; height: 50px; float: left; border-left: 1px solid whitesmoke">
                                Total Game
                                <div style="width: 100%">
                                    <div class="detail">
                                        On
                                    </div>
                                    <div class="detail">
                                        Off
                                    </div>
                                    <div class="detail">
                                        Blk
                                    </div>
                                    <div class="detail">
                                        In
                                    </div>
                                    <div class="detail">
                                        Out
                                    </div>
                                    <div class="detail">
                                        Cnr
                                    </div>
                                    <div class="detail">
                                        DA
                                    </div>
                                    <div class="detail">
                                        Poss
                                    </div>
                                    <div class="detail">
                                        Rtg
                                    </div>
                                </div>
                            </div>
                            <div class="header-content" style="width: 15%; height: 50px; float: left; border-left: 1px solid whitesmoke">
                                <p style="text-align: center;">Cards</p>
                                <img src="/img/box-yellow.png" width="20px;" style="position: relative; top: -15px; left: -10px;"/>
                                <img src="/img/box-red.png" width="20px;" style="position: relative; top: -15px; left: 10px"/>
                            </div>
                        </div>
                        <div v-for="item1 in item.events" :key="item1.away_id" class="content" style="width: 50%; height: 62px; font-weight: 600;">
                            <!--                             home team data part  -->
                            <div style="width: 30%; height: 31px; float: left;">
                                <div style="width: 40px; float: left;position: relative; top:  23px; left: 15px; font-size: 17px; font-weight: normal">{{item1.time.status}}</div>
                                <div style="width: calc(100% - 70px); float: left;">{{item1.localTeamName}}</div>
                            </div>
                            <div style="width: 55%; height: 31px; float: left; border-left: 1px solid #e2e2e2;">
                                <div style="width: 100%; padding: 3px 7px; color: black;">

                                    <div class="detail" style="color: black;">
                                        {{item1.stats[0].shots.ongoal}}
                                    </div>

                                    <div class="detail" style="color: black">
                                        {{item1.stats[0].shots.offgoal}}
                                    </div>

                                    <div v-if="item1.stats[0].shots.blocked != null" class="detail" style="color: black">
                                        {{item1.stats[0].shots.blocked}}
                                    </div>
                                    <div v-else class="detail" style="color: black;">
                                        -
                                    </div>

                                    <div v-if="item1.stats[0].shots.insidebox != null" class="detail" style="color: black">
                                        {{item1.stats[0].shots.insidebox}}
                                    </div>
                                    <div v-else class="detail" style="color: black">
                                        -
                                    </div>

                                    <div v-if="item1.stats[0].shots.outsidebox != null" class="detail" style="color: black;">
                                        {{item1.stats[0].shots.outsidebox}}
                                    </div>
                                    <div v-else class="detail">
                                        -
                                    </div>

                                    <div v-if="item1.stats[0].corners != null" class="detail" style="color: black">
                                        {{item1.stats[0].corners}}
                                    </div>
                                    <div v-else class="detail">
                                        -
                                    </div>

                                    <div v-if="item1.stats[0].attacks != null" class="detail" style="color: black">
                                        {{item1.stats[0].attacks.dangerous_attacks}}
                                    </div>
                                    <div v-else class="detail" style="color: black">
                                        -
                                    </div>

                                    <div v-if="item1.stats[0].possessiontime != null" class="detail" style="color: black;">
                                        {{item1.stats[0].possessiontime}}
                                    </div>
                                    <div v-else class="detail">
                                        -
                                    </div>
                                    <div class="detail">
                                        -
                                    </div>
                                </div>
                            </div>
                            <div style="width: 15%; height: 31px; float: left; border-left: 1px solid #e2e2e2; border-right: 1px solid #e2e2e2; padding: 0px 10px; text-align: center;">
                                <div class="detail" style="width: 50%; position: relative; left: -4px;">{{item1.stats[0].yellowcards}}</div>
                                <div class="detail" style="width: 50%; position: relative; left: 3px;">{{item1.stats[0].redcards}}</div>
                            </div>
                            <!--                             away team data part  -->
                            <div style="width: 30%; height: 31px; float: left; border-bottom: 1px solid lightgray">
                                <div style="width: 40px; float: left; color: white;">.</div>
                                <div style="width: calc(100% - 70px); float: left;">{{item1.visitorTeamName}}</div>
                                <div style="width: 30px; float: left; font-size: 17px; font-weight: 600; position: relative; top: -15px; left: -10px;">{{item1.scores.localteam_score}} - {{item1.scores.visitorteam_score}}</div>
                            </div>
                            <div style="width: 55%; height: 31px; float: left; border-left: 1px solid #e2e2e2; border-bottom: 1px solid lightgray">
                                <div style="width: 100%; padding: 3px 7px; color: black;">

                                    <div class="detail" style="color: black;">
                                        {{item1.stats[1].shots.ongoal}}
                                    </div>

                                    <div class="detail" style="color: black">
                                        {{item1.stats[1].shots.offgoal}}
                                    </div>

                                    <div v-if="item1.stats[1].shots.blocked != null" class="detail" style="color: black">
                                        {{item1.stats[1].shots.blocked}}
                                    </div>
                                    <div v-else class="detail" style="color: black;">
                                        -
                                    </div>

                                    <div v-if="item1.stats[1].shots.insidebox != null" class="detail" style="color: black">
                                        {{item1.stats[1].shots.insidebox}}
                                    </div>
                                    <div v-else class="detail" style="color: black">
                                        -
                                    </div>

                                    <div v-if="item1.stats[1].shots.outsidebox != null" class="detail" style="color: black;">
                                        {{item1.stats[1].shots.outsidebox}}
                                    </div>
                                    <div v-else class="detail">
                                        -
                                    </div>

                                    <div v-if="item1.stats[1].corners != null" class="detail" style="color: black">
                                        {{item1.stats[1].corners}}
                                    </div>
                                    <div v-else class="detail">
                                        -
                                    </div>

                                    <div v-if="item1.stats[1].attacks.dangerous_attacks != null" class="detail" style="color: black">
                                        {{item1.stats[1].attacks.dangerous_attacks}}
                                    </div>
                                    <div v-else class="detail" style="color: black">
                                        -
                                    </div>


                                    <div v-if="item1.stats[1].possessiontime != null" class="detail" style="color: black;">
                                        {{item1.stats[1].possessiontime}}
                                    </div>
                                    <div v-else class="detail">
                                        -
                                    </div>
                                    <div class="detail">
                                        -
                                    </div>
                                </div>
                            </div>
                            <div style="width: 15%; height: 31px; float: left; border-left: 1px solid #e2e2e2; border-right: 1px solid #e2e2e2; padding: 0px 10px; text-align: center; border-bottom: 1px solid lightgray">
                                <div class="detail" style="width: 50%; position: relative; left: -4px;">{{item1.stats[1].yellowcards}}</div>
                                <div class="detail" style="width: 50%; position: relative; left: 3px;">{{item1.stats[1].redcards}}</div>
                            </div>
                        </div>
                    </div>
                </CTab>
                <CTab title="My Games">
                    My game content tabs
<!--                    <Plotly :data="data" :layout="layout" :display-mode-bar="false"></Plotly>-->
<!--                    <vue-plotly :data="data" :layout="layout" :options="options"/>-->
                </CTab>
            </CTabs>
        </CCard>
    </div>
</template>

<script>
    // import { Plotly } from 'vue-plotly'
    import VuePlotly from '@statnett/vue-plotly'
    export default {
        name: 'LiveStats',
        components: {
            // Plotly
            // VuePlotly
        },
        data () {
            return {
                eventArray:[],
                scheduleArray:[],
                liveNumbers: 0,
                liveDataArray:[],
                scheduleLength:0,
                finishedArray:[],
                finishedLength:0,
                collapsed1:[],
                // data:[
                //     {
                //         x: [1,2,3,4],
                //         y: [10,15,13,17],
                //         type:"bar",
                //         name: 'Trace1',
                //         showarrow: false,
                //         marker: {
                //             color: 'rgba(50,171, 96, 0.7)',
                //             line: {
                //                 color: 'rgba(50,171,96,1.0)',
                //                 width: 1
                //             }
                //         }
                //     },
                //     {
                //         x: [1,2,3,4],
                //         y: [-10,-15,-13,-17],
                //         overlaying: 'y',
                //         type:"bar",
                //         name: 'Trace2',
                //         showarrow: false
                //     },
                // ],
                // layout:{
                //     title: "My graph",
                //     showlegend: true,
                //     barmode: 'relative',
                //     showarrow: false
                // }
                data: [{ x: [1, 3], y: [2, 4] },{ x: [1, 4], y: [2, 6] }],
                layout: {},
                options: {}
            }
        },
        methods: {
            isCollapsed1(id){
                return this.collapsed1.indexOf(id)>-1?true:false;
            },
            SetCollapse1(id){
                if (this.isCollapsed1(id)){
                    this.collapsed1.splice(this.collapsed1.indexOf(id), 1)
                }
                else{
                    this.collapsed1.push(id)
                }
            },
            isPlus(id){
                return this.collapsed1.indexOf(id)>-1?false:true;
            },
            isMinus(id){
                return this.collapsed1.indexOf(id)>-1?true:false;
            },
            readData(){
                window.axios.post(`${process.env.VUE_APP_URL}getLiveStats`).then(({data})=> {
                    console.log('data', data.data[0], data.data[1], data.data[2])
                    this.liveDataArray = data.data[1]
                    let main_data = data.data[0]
                    let competitionArray = []
                    let index = 0
                    for(let i = 0 ; i < main_data.length ; i++){
                        // console.log(main_data[i].time.status)
                        if((main_data[i].time.status == 'LIVE' || main_data[i].time.status == 'HT' || main_data[i].time.status == 'ET') && main_data[i].stats.length > 0){
                            index++
                            competitionArray[index - 1] = main_data[i].competitions[0].name
                        }
                    }
                    competitionArray = Array.from(new Set (competitionArray))

                    let k = 0
                    this.eventArray = []
                    for(let i = 0 ; i < competitionArray.length ; i++){
                        this.eventArray.push({'league': competitionArray[i], 'events': []})
                        for(let j = 0 ; j < main_data.length ; j++) {
                            if(main_data[j].stats.length > 0){
                                if((main_data[j].competitions[0].name == competitionArray[i] && main_data[j].time.status == 'LIVE') || (main_data[j].competitions[0].name == competitionArray[i] && main_data[j].time.status == 'HT') || (main_data[j].competitions[0].name == competitionArray[i] && main_data[j].time.status == 'ET')){
                                    let home = {
                                        'id': 0,
                                        'on': 0,
                                        'off': 0,
                                        'blk': 0,
                                        'in': 0,
                                        'out': 0,
                                        'cnr': 0,
                                        'da': 0,
                                        'goal': 0,
                                        'rtg': 0,
                                        'time': '',
                                        'score': 0,
                                        'flash': 0,
                                        'poss': 0,
                                        'pas': 0,
                                        'acc': 0,
                                        'atk': 0,
                                        'ofs': 0,
                                        'sav': 0,
                                        'sbst': 0,
                                        'red': 0,
                                        'fou': 0,
                                        'g_att': 0,
                                        'safe': 0
                                    }
                                    let homeT = {
                                        'on': 0,
                                        'off': 0,
                                        'blk': 0,
                                        'in': 0,
                                        'out': 0,
                                        'cnr': 0,
                                        'da': 0,
                                        'poss': 0,
                                        'flash': 0,
                                        'pas': 0,
                                        'acc': 0,
                                        'atk': 0,
                                        'ofs': 0,
                                        'sav': 0,
                                        'sbst': 0,
                                        'red': 0,
                                        'fou': 0,
                                        'g_att': 0,
                                        'safe': 0
                                    }
                                    let away = {
                                        'id': 0,
                                        'on': 0,
                                        'off': 0,
                                        'blk': 0,
                                        'in': 0,
                                        'out': 0,
                                        'cnr': 0,
                                        'da': 0,
                                        'goal': 0,
                                        'rtg': 0,
                                        'time': 0,
                                        'score': 0,
                                        'poss': 0,
                                        'pas': 0,
                                        'acc': 0,
                                        'atk': 0,
                                        'ofs': 0,
                                        'sav': 0,
                                        'sbst': 0,
                                        'red': 0,
                                        'fou': 0,
                                        'g_att': 0,
                                        'safe': 0
                                    }
                                    let awayT = {
                                        'on': 0,
                                        'off': 0,
                                        'blk': 0,
                                        'in': 0,
                                        'out': 0,
                                        'cnr': 0,
                                        'da': 0,
                                        'poss': 0,
                                        'pas': 0,
                                        'acc': 0,
                                        'atk': 0,
                                        'ofs': 0,
                                        'sav': 0,
                                        'sbst': 0,
                                        'red': 0,
                                        'fou': 0,
                                        'g_att': 0,
                                        'safe': 0
                                    }
                                    let home_season = {
                                        'on': 0,
                                        'off': 0,
                                        'block': 0,
                                        'in': 0,
                                        'out': 0,
                                        'cnr': 0,
                                        'da': 0,
                                        'pos': 0,
                                        'pas': 0,
                                        'acc': 0,
                                        'atk': 0,
                                        'ofs': 0,
                                        'sav': 0,
                                        'sbst': 0,
                                        'fou': 0 ,
                                        'g_att': 0 ,
<<<<<<< HEAD
                                        'safe': 0,
                                        'goals':0
=======
                                        'safe': 0
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                    }
                                    let away_season = {
                                        'on': 0,
                                        'off': 0,
                                        'block': 0,
                                        'in': 0,
                                        'out': 0,
                                        'cnr': 0,
                                        'da': 0,
                                        'pos': 0,
                                        'pas': 0,
                                        'acc': 0,
                                        'atk': 0,
                                        'ofs': 0,
                                        'sav': 0,
                                        'sbst': 0,
                                        'fou': 0 ,
                                        'g_att': 0 ,
<<<<<<< HEAD
                                        'safe': 0,
                                        'goals': 0
=======
                                        'safe': 0
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                    }
                                    let home_p = 0
                                    let away_p = 0
                                    home.id = main_data[j].home_id
                                    away.id = main_data[j].away_id
                                    let home_poss_index = 0
                                    let away_poss_index = 0
                                    if(main_data[j].season_stats.length > 0){
                                        for(let u = 0 ; u < main_data[j].season_stats.length ; u++){
                                            if(main_data[j].season_stats[u].stats){
                                                if(main_data[j].season_stats[u].stats.length > 0){
                                                    for(let uu = 0 ; uu < main_data[j].season_stats[u].stats.length ; uu++){
                                                        if(main_data[j].season_stats[u].stats[uu][0]){
                                                            if(main_data[j].season_stats[u].stats[uu][0].team_id == home.id){
                                                                home_p++
<<<<<<< HEAD
                                                                console.log(main_data[j], main_data[j].season_stats[u].stats, u)
=======
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                                if(main_data[j].season_stats[u].stats[uu][0].shots){
                                                                    home_season.on = home_season.on + main_data[j].season_stats[u].stats[uu][0].shots.ongoal
                                                                    home_season.off = home_season.off + main_data[j].season_stats[u].stats[uu][0].shots.offgoal
                                                                    home_season.block = home_season.block + main_data[j].season_stats[u].stats[uu][0].shots.block
                                                                    home_season.in = home_season.in + main_data[j].season_stats[u].stats[uu][0].shots.insidebox
                                                                    home_season.out = home_season.out + main_data[j].season_stats[u].stats[uu][0].shots.outsidebox
                                                                }
<<<<<<< HEAD

                                                                if(main_data[j].season_stats[u].stats[uu][0].goals){
                                                                    home_season.goals = home_season.goals + main_data[j].season_stats[u].stats[uu][0].goals
                                                                }
=======
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                                if(main_data[j].season_stats[u].stats[uu][0].corners != null){
                                                                    home_season.cnr = home_season.cnr + main_data[j].season_stats[u].stats[uu][0].corners
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].attacks != null){
                                                                    home_season.da = home_season.da + main_data[j].season_stats[u].stats[uu][0].attacks.dangerous_attacks
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].possessiontime){
                                                                    home_poss_index++
                                                                    home_season.pos = home_season.pos + main_data[j].season_stats[u].stats[uu][0].possessiontime
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].passes){
                                                                    home_season.pas = home_season.pas + main_data[j].season_stats[u].stats[uu][0].passes.total
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].passes){
                                                                    home_season.acc = home_season.acc + main_data[j].season_stats[u].stats[uu][0].passes.accurate
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].attacks){
                                                                    home_season.atk = home_season.atk + main_data[j].season_stats[u].stats[uu][0].attacks.attacks
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].offsides){
                                                                    home_season.ofs = home_season.ofs + main_data[j].season_stats[u].stats[uu][0].offsides
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].saves){
                                                                    home_season.sav = home_season.sav + main_data[j].season_stats[u].stats[uu][0].saves
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].saves){
                                                                    home_season.sbst = home_season.sbst + main_data[j].season_stats[u].stats[uu][0].substitutions
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].fouls){
                                                                    home_season.fou = home_season.fou + main_data[j].season_stats[u].stats[uu][0].fouls
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].goal_attempts){
                                                                    home_season.g_att = home_season.g_att + main_data[j].season_stats[u].stats[uu][0].goal_attempts
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].ball_safe){
                                                                    home_season.safe = home_season.safe + main_data[j].season_stats[u].stats[uu][0].ball_safe
                                                                }
                                                            }
<<<<<<< HEAD
                                                            if(main_data[j].season_stats[u].stats[uu][1].team_id == away.id){
                                                                away_p++

                                                                away_season.on = home_season.on + main_data[j].season_stats[u].stats[uu][1].shots.ongoal
                                                                away_season.off = home_season.off + main_data[j].season_stats[u].stats[uu][1].shots.offgoal
                                                                if(main_data[j].season_stats[u].stats[uu][0].shots.block != null){
                                                                    away_season.block = home_season.block + main_data[j].season_stats[u].stats[uu][1].shots.block
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].shots.insidebox != null){
                                                                    away_season.in = home_season.in + main_data[j].season_stats[u].stats[uu][1].shots.insidebox
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][1].goals){
                                                                    away_season.goals = away_season.goals + main_data[j].season_stats[u].stats[uu][1].goals
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].shots.outsidebox != null){
                                                                    away_season.out = home_season.out + main_data[j].season_stats[u].stats[uu][1].shots.outsidebox
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].corners != null){
                                                                    away_season.cnr = home_season.cnr + main_data[j].season_stats[u].stats[uu][1].corners
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].attacks != null){
                                                                    away_season.da = home_season.da + main_data[j].season_stats[u].stats[uu][1].attacks.dangerous_attacks
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].possessiontime){
                                                                    away_poss_index++
                                                                    away_season.pos = home_season.pos + main_data[j].season_stats[u].stats[uu][1].possessiontime
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].passes){
                                                                    away_season.pas = home_season.pas + main_data[j].season_stats[u].stats[uu][1].passes.total
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].passes){
                                                                    away_season.acc = home_season.acc + main_data[j].season_stats[u].stats[uu][1].passes.accurate
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].attacks){
                                                                    away_season.atk = home_season.atk + main_data[j].season_stats[u].stats[uu][1].attacks.attacks
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].offsides){
                                                                    away_season.ofs = home_season.ofs + main_data[j].season_stats[u].stats[uu][1].offsides
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].saves){
                                                                    away_season.sav = home_season.sav + main_data[j].season_stats[u].stats[uu][1].saves
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].saves){
                                                                    away_season.sbst = home_season.sbst + main_data[j].season_stats[u].stats[uu][1].substitutions
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].fouls){
                                                                    away_season.fou = home_season.fou + main_data[j].season_stats[u].stats[uu][1].fouls
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].goal_attempts){
                                                                    away_season.g_att = home_season.g_att + main_data[j].season_stats[u].stats[uu][1].goal_attempts
                                                                }
                                                                if(main_data[j].season_stats[u].stats[uu][0].ball_safe){
                                                                    away_season.safe = home_season.safe + main_data[j].season_stats[u].stats[uu][1].ball_safe
                                                                }
                                                            }
=======
                                                            
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }

                                    home.score = main_data[j].scores.localteam_score
                                    away.score = main_data[j].scores.visitorteam_score

                                    home.time = main_data[j].time.minute
                                    if (main_data[j].time.injury_time > 0) {
                                        home.time = main_data[j].time.minute + '+' + main_data[j].time.injury_time + "'"
                                    }
                                    if (main_data[j].time.status == 'HT') {
                                        home.time = 'HT'
                                    }

                                    //---------Last 10 min Part----------//
                                    if (main_data[j].stats_ten) {
                                        if(!main_data[j].stats_ten[0]){return}
                                        if (main_data[j].home_id == main_data[j].stats_ten[0][0].team_id) {
                                            if(main_data[j].stats[0].shots){
                                                home.on = main_data[j].stats[0].shots.ongoal - main_data[j].stats_ten[0][0].shots.ongoal
                                                away.on = main_data[j].stats[1].shots.ongoal - main_data[j].stats_ten[0][1].shots.ongoal
                                                home.off = main_data[j].stats[0].shots.offgoal - main_data[j].stats_ten[0][0].shots.offgoal
                                                away.off = main_data[j].stats[1].shots.offgoal - main_data[j].stats_ten[0][1].shots.offgoal
                                                home.blk = main_data[j].stats[0].shots.blocked - main_data[j].stats_ten[0][0].shots.blocked
                                                away.blk = main_data[j].stats[1].shots.blocked - main_data[j].stats_ten[0][1].shots.blocked
                                            }
                                            if (!main_data[j].stats[0].shots.blocked) {
                                                home.blk = null
                                                away.blk = null
                                            }
                                            home.in = main_data[j].stats[0].shots.insidebox - main_data[j].stats_ten[0][0].shots.insidebox
                                            away.in = main_data[j].stats[1].shots.insidebox - main_data[j].stats_ten[0][1].shots.insidebox
                                            if (!main_data[j].stats[0].shots.insidebox) {
                                                home.in = null
                                                away.in = null
                                            }
                                            home.out = main_data[j].stats[0].shots.outsidebox - main_data[j].stats_ten[0][0].shots.outsidebox
                                            away.out = main_data[j].stats[1].shots.outsidebox - main_data[j].stats_ten[0][1].shots.outsidebox
                                            if (!main_data[j].stats[0].outsidebox) {
                                                home.out = null
                                                away.out = null
                                            }
                                            home.cnr = main_data[j].stats[0].corners - main_data[j].stats_ten[0][0].corners
                                            away.cnr = main_data[j].stats[1].corners - main_data[j].stats_ten[0][1].corners
                                            if (!main_data[j].stats[0].corners) {
                                                home.cnr = null
                                                away.cnr = null
                                            }

                                            if(main_data[j].stats[0].attacks && main_data[j].stats_ten[0][0].attacks){
                                                home.da = main_data[j].stats[0].attacks.dangerous_attacks - main_data[j].stats_ten[0][0].attacks.dangerous_attacks
                                                away.da = main_data[j].stats[1].attacks.dangerous_attacks - main_data[j].stats_ten[0][1].attacks.dangerous_attacks

                                                home.atk = main_data[j].stats[0].attacks.attacks - main_data[j].stats_ten[0][0].attacks.attacks
                                                away.atk = main_data[j].stats[1].attacks.attacks - main_data[j].stats_ten[0][1].attacks.attacks
                                            }

                                            home.goal = main_data[j].stats[0].goals - main_data[j].stats_ten[0][0].goals
                                            away.goal = main_data[j].stats[1].goals - main_data[j].stats_ten[0][1].goals

                                            home.poss = main_data[j].stats_ten[0][0].possessiontime
                                            away.poss = 100 - home.poss
                                            if (home.poss === null || home.poss === 0) {
                                                away.poss = 0
                                            }

                                            if (main_data[j].stats[0].passes && main_data[j].stats_ten[0][0].passes) {
                                                console.log('**************************************', main_data[j].stats_ten[0][0].passes)
                                                home.pas = main_data[j].stats[0].passes.total - main_data[j].stats_ten[0][0].passes.total
                                                away.pas = main_data[j].stats[1].passes.total - main_data[j].stats_ten[0][1].passes.total
                                            } else {
                                                home.pas = null
                                                away.pas = null
                                            }

                                            if (main_data[j].stats[0].passes && main_data[j].stats_ten[0][0].passes) {
                                                home.acc = main_data[j].stats[0].passes.accurate - main_data[j].stats_ten[0][0].passes.accurate
                                                away.acc = main_data[j].stats[1].passes.accurate - main_data[j].stats_ten[0][1].passes.accurate
                                            } else {
                                                home.acc = null
                                                away.acc = null
                                            }

                                            home.ofs = main_data[j].stats[0].offsides - main_data[j].stats_ten[0][0].offsides
                                            away.ofs = main_data[j].stats[1].offsides - main_data[j].stats_ten[0][1].offsides

                                            if (!main_data[j].stats[0].offsides) {
                                                home.ofs = null
                                                away.ofs = null
                                            }
                                            home.sav = main_data[j].stats[0].saves - main_data[j].stats_ten[0][0].saves
                                            away.sav = main_data[j].stats[1].saves - main_data[j].stats_ten[0][1].saves
                                            if (!main_data[j].stats[0].saves) {
                                                home.sav = null
                                                away.sav = null
                                            }
                                            if (main_data[j].stats[0].substitutions != null) {
                                                home.sbst = main_data[j].stats[0].substitutions - main_data[j].stats_ten[0][0].substitutions
                                                away.sbst = main_data[j].stats[1].substitutions - main_data[j].stats_ten[0][1].substitutions
                                            } else {
                                                home.sbst = null
                                                away.sbst = null
                                            }

                                            home.red = main_data[j].stats[0].redcards - main_data[j].stats_ten[0][0].redcards
                                            away.red = main_data[j].stats[1].redcards - main_data[j].stats_ten[0][1].redcards
                                            if (!main_data[j].stats[0].redcards) {
                                                home.red = null
                                                away.red = null
                                            }
                                            home.fou = main_data[j].stats[0].fouls - main_data[j].stats_ten[0][0].fouls
                                            away.fou = main_data[j].stats[1].fouls - main_data[j].stats_ten[0][1].fouls

                                            if (!main_data[j].stats[0].fouls) {
                                                home.fou = null
                                                away.fou = null
                                            }
                                            if (main_data[j].stats[0].goal_attempts != null) {
                                                home.g_att = main_data[j].stats[0].goal_attempts - main_data[j].stats_ten[0][0].goal_attempts
                                                away.g_att = main_data[j].stats[1].goal_attempts - main_data[j].stats_ten[0][1].goal_attempts
                                            } else {
                                                home.g_att = null
                                                away.g_att = null
                                            }

                                            if (main_data[j].stats[0].ball_safe != null) {
                                                home.safe = main_data[j].stats[0].ball_safe - main_data[j].stats_ten[0][0].ball_safe
                                                away.safe = main_data[j].stats[1].ball_safe - main_data[j].stats_ten[0][1].ball_safe
                                            } else {
                                                home.safe = null
                                                away.safe = null
                                            }
                                        } else {
                                            home.on = main_data[j].stats[1].shots.ongoal - main_data[j].stats_ten[0][1].shots.ongoal
                                            away.on = main_data[j].stats[0].shots.ongoal - main_data[j].stats_ten[0][0].shots.ongoal
                                            home.off = main_data[j].stats[1].shots.offgoal - main_data[j].stats_ten[0][1].shots.offgoal
                                            away.off = main_data[j].stats[0].shots.offgoal - main_data[j].stats_ten[0][0].shots.offgoal
                                            home.blk = main_data[j].stats[1].shots.blocked - main_data[j].stats_ten[0][1].shots.blocked
                                            away.blk = main_data[j].stats[0].shots.blocked - main_data[j].stats_ten[0][0].shots.blocked
                                            if (!main_data[j].stats[0].shots.blocked) {
                                                home.blk = null
                                                away.blk = null
                                            }
                                            home.in = main_data[j].stats[1].shots.insidebox - main_data[j].stats_ten[0][1].shots.insidebox
                                            away.in = main_data[j].stats[0].shots.insidebox - main_data[j].stats_ten[0][0].shots.insidebox
                                            if (!main_data[j].stats[0].shots.insidebox) {
                                                home.in = null
                                                away.in = null
                                            }
                                            home.out = main_data[j].stats[1].shots.outsidebox - main_data[j].stats_ten[0][1].shots.outsidebox
                                            away.out = main_data[j].stats[0].shots.outsidebox - main_data[j].stats_ten[0][0].shots.outsidebox
                                            if (!main_data[j].stats[0].outsidebox) {
                                                home.out = null
                                                away.out = null
                                            }
                                            home.cnr = main_data[j].stats[1].corners - main_data[j].stats_ten[0][1].corners
                                            away.cnr = main_data[j].stats[0].corners - main_data[j].stats_ten[0][0].corners
                                            if (!main_data[j].stats[0].corners) {
                                                home.cnr = null
                                                away.cnr = null
                                            }

                                            if(main_data[j].stats[1].attacks && main_data[j].stats_ten[0][1].attacks){
                                                home.da = main_data[j].stats[1].attacks.dangerous_attacks - main_data[j].stats_ten[0][1].attacks.dangerous_attacks
                                                away.da = main_data[j].stats[0].attacks.dangerous_attacks - main_data[j].stats_ten[0][0].attacks.dangerous_attacks

                                                home.atk = main_data[j].stats[1].attacks.attacks - main_data[j].stats_ten[0][1].attacks.attacks
                                                away.atk = main_data[j].stats[0].attacks.attacks - main_data[j].stats_ten[0][0].attacks.attacks
                                            }

                                            home.goal = main_data[j].stats[1].goals - main_data[j].stats_ten[0][1].goals
                                            away.goal = main_data[j].stats[0].goals - main_data[j].stats_ten[0][0].goals

                                            home.poss = main_data[j].stats_ten[0][0].possessiontime
                                            away.poss = 100 - home.poss
                                            if (home.poss === null || home.poss === 0) {
                                                away.poss = 0
                                            }

                                            if (main_data[j].stats[0].passes != null) {
                                                home.pas = main_data[j].stats[1].passes.total - main_data[j].stats_ten[0][1].passes.total
                                                away.pas = main_data[j].stats[0].passes.total - main_data[j].stats_ten[0][0].passes.total
                                            } else {
                                                home.pas = null
                                                away.pas = null
                                            }

                                            if (main_data[j].stats[0].passes != null) {
                                                home.acc = main_data[j].stats[1].passes.accurate - main_data[j].stats_ten[0][1].passes.accurate
                                                away.acc = main_data[j].stats[0].passes.accurate - main_data[j].stats_ten[0][0].passes.accurate
                                            } else {
                                                home.acc = null
                                                away.acc = null
                                            }

                                            home.ofs = main_data[j].stats[1].offsides - main_data[j].stats_ten[0][1].offsides
                                            away.ofs = main_data[j].stats[0].offsides - main_data[j].stats_ten[0][0].offsides

                                            if (!main_data[j].stats[0].offsides) {
                                                home.ofs = null
                                                away.ofs = null
                                            }
                                            home.sav = main_data[j].stats[1].saves - main_data[j].stats_ten[0][1].saves
                                            away.sav = main_data[j].stats[0].saves - main_data[j].stats_ten[0][0].saves
                                            if (!main_data[j].stats[0].saves) {
                                                home.sav = null
                                                away.sav = null
                                            }
                                            if (main_data[j].stats[0].substitutions != null) {
                                                home.sbst = main_data[j].stats[1].substitutions - main_data[j].stats_ten[0][1].substitutions
                                                away.sbst = main_data[j].stats[0].substitutions - main_data[j].stats_ten[0][0].substitutions
                                            } else {
                                                home.sbst = null
                                                away.sbst = null
                                            }

                                            home.red = main_data[j].stats[1].redcards - main_data[j].stats_ten[0][1].redcards
                                            away.red = main_data[j].stats[0].redcards - main_data[j].stats_ten[0][0].redcards
                                            if (!main_data[j].stats[0].redcards) {
                                                home.red = null
                                                away.red = null
                                            }
                                            home.fou = main_data[j].stats[1].fouls - main_data[j].stats_ten[0][1].fouls
                                            away.fou = main_data[j].stats[0].fouls - main_data[j].stats_ten[0][0].fouls

                                            if (!main_data[j].stats[0].fouls) {
                                                home.fou = null
                                                away.fou = null
                                            }
                                            if (main_data[j].stats[0].goal_attempts != null) {
                                                home.g_att = main_data[j].stats[1].goal_attempts - main_data[j].stats_ten[0][1].goal_attempts
                                                away.g_att = main_data[j].stats[0].goal_attempts - main_data[j].stats_ten[0][0].goal_attempts
                                            } else {
                                                home.g_att = null
                                                away.g_att = null
                                            }

                                            if (main_data[j].stats[0].ball_safe != null) {
                                                home.safe = main_data[j].stats[1].ball_safe - main_data[j].stats_ten[0][1].ball_safe
                                                away.safe = main_data[j].stats[0].ball_safe - main_data[j].stats_ten[0][0].ball_safe
                                            } else {
                                                home.safe = null
                                                away.safe = null
                                            }

                                        }
                                    }
                                    //-------------Total Part------------//
                                    if (main_data[j].home_id === main_data[j].stats[0].team_id) {
                                        homeT.on = main_data[j].stats[0].shots.ongoal
                                        awayT.on = main_data[j].stats[1].shots.ongoal
                                        homeT.off = main_data[j].stats[0].shots.offgoal
                                        awayT.off = main_data[j].stats[1].shots.offgoal
                                        homeT.blk = main_data[j].stats[0].shots.blocked
                                        awayT.blk = main_data[j].stats[1].shots.blocked
                                        homeT.in = main_data[j].stats[0].shots.insidebox
                                        awayT.in = main_data[j].stats[1].shots.insidebox
                                        homeT.out = main_data[j].stats[0].shots.outsidebox
                                        awayT.out = main_data[j].stats[1].shots.outsidebox
                                        homeT.cnr = main_data[j].stats[0].corners
                                        awayT.cnr = main_data[j].stats[1].corners
                                        homeT.da = main_data[j].stats[0].attacks.dangerous_attacks
                                        awayT.da = main_data[j].stats[1].attacks.dangerous_attacks
                                        homeT.poss = main_data[j].stats[0].possessiontime
                                        awayT.poss = main_data[j].stats[1].possessiontime
                                        if (main_data[j].stats[0].passes != null) {
                                            homeT.pas = main_data[j].stats[0].passes.total
                                            awayT.pas = main_data[j].stats[1].passes.total
                                        } else {
                                            homeT.pas = null
                                            awayT.pas = null
                                        }

                                        if (main_data[j].stats[0].passes != null) {
                                            homeT.acc = main_data[j].stats[0].passes.accurate
                                            awayT.acc = main_data[j].stats[1].passes.accurate
                                        } else {
                                            homeT.acc = null
                                            awayT.acc = null
                                        }
                                        homeT.atk = main_data[j].stats[0].attacks.attacks
                                        awayT.atk = main_data[j].stats[1].attacks.attacks
                                        homeT.ofs = main_data[j].stats[0].offsides
                                        awayT.ofs = main_data[j].stats[1].offsides
                                        homeT.sav = main_data[j].stats[0].saves
                                        awayT.sav = main_data[j].stats[1].saves
                                        homeT.sbst = main_data[j].stats[0].substitutions
                                        awayT.sbst = main_data[j].stats[1].substitutions
                                        homeT.red = main_data[j].stats[0].redcards
                                        awayT.red = main_data[j].stats[1].redcards
                                        homeT.fou = main_data[j].stats[0].fouls
                                        awayT.fou = main_data[j].stats[1].fouls
                                        homeT.g_att = main_data[j].stats[0].goal_attempts
                                        awayT.g_att = main_data[j].stats[1].goal_attempts
                                        homeT.safe = main_data[j].stats[0].ball_safe
                                        awayT.safe = main_data[j].stats[1].ball_safe
                                    } else {
                                        homeT.on = main_data[j].stats[1].shots.ongoal
                                        awayT.on = main_data[j].stats[0].shots.ongoal
                                        homeT.off = main_data[j].stats[1].shots.offgoal
                                        awayT.off = main_data[j].stats[0].shots.offgoal
                                        homeT.blk = main_data[j].stats[1].shots.blocked
                                        awayT.blk = main_data[j].stats[0].shots.blocked
                                        homeT.in = main_data[j].stats[1].shots.insidebox
                                        awayT.in = main_data[j].stats[0].shots.insidebox
                                        homeT.out = main_data[j].stats[1].shots.outsidebox
                                        awayT.out = main_data[j].stats[0].shots.outsidebox
                                        homeT.cnr = main_data[j].stats[1].corners
                                        awayT.cnr = main_data[j].stats[0].corners
                                        homeT.da = main_data[j].stats[1].attacks.dangerous_attacks
                                        awayT.da = main_data[j].stats[0].attacks.dangerous_attacks
                                        homeT.poss = main_data[j].stats[1].possessiontime
                                        awayT.poss = main_data[j].stats[0].possessiontime
                                        if (main_data[j].stats[0].passes != null) {
                                            homeT.pas = main_data[j].stats[1].passes.total
                                            awayT.pas = main_data[j].stats[0].passes.total
                                        } else {
                                            homeT.pas = null
                                            awayT.pas = null
                                        }

                                        if (main_data[j].stats[0].passes != null) {
                                            homeT.acc = main_data[j].stats[1].passes.accurate
                                            awayT.acc = main_data[j].stats[0].passes.accurate
                                        } else {
                                            homeT.acc = null
                                            awayT.acc = null
                                        }
                                        homeT.atk = main_data[j].stats[1].attacks.attacks
                                        awayT.atk = main_data[j].stats[0].attacks.attacks
                                        homeT.ofs = main_data[j].stats[1].offsides
                                        awayT.ofs = main_data[j].stats[0].offsides
                                        homeT.sav = main_data[j].stats[1].saves
                                        awayT.sav = main_data[j].stats[0].saves
                                        homeT.sbst = main_data[j].stats[1].substitutions
                                        awayT.sbst = main_data[j].stats[0].substitutions
                                        homeT.red = main_data[j].stats[1].redcards
                                        awayT.red = main_data[j].stats[0].redcards
                                        homeT.fou = main_data[j].stats[1].fouls
                                        awayT.fou = main_data[j].stats[0].fouls
                                        homeT.g_att = main_data[j].stats[1].goal_attempts
                                        awayT.g_att = main_data[j].stats[0].goal_attempts
                                        homeT.safe = main_data[j].stats[1].ball_safe
                                        awayT.safe = main_data[j].stats[0].ball_safe
                                    }
                                    //-----------------------------------//
<<<<<<< HEAD
                                    // home_season.pos = parseInt(home_season.pos/home_poss_index)
                                    // away_season.pos = 100 - home_season.pos
=======
                                    home_season.pos = parseInt(home_season.pos/home_poss_index)
                                    away_season.pos = 100 - home_season.pos
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
                                    this.eventArray[i].events.push({
                                        'index0': k,
                                        'main_data': main_data[j],
                                        'home': home,
                                        'away': away,
                                        'home_p': home_p,
                                        'away_p': away_p,
                                        'homeT': homeT,
                                        'awayT': awayT,
                                        'home_season': home_season,
                                        'away_season': away_season
                                    })
                                    k++
                                    //-----------------------------------//
                                }
                            }
                        }
                    }
                    let self = this
                    this.sortJSON(self.eventArray,'league', '123');
                    this.liveNumbers = k

                    let eventList = data.data[2]
                    let competitionArray1 = []
                    for(let i = 0 ; i < eventList.length; i++){
                        let competitionName = eventList[i].competitions[0].name
                        competitionArray1[i] = competitionName
                    }
                    competitionArray1 = Array.from(new Set (competitionArray1))

                    this.scheduleArray = []
                    this.scheduleLength = 0
                    for(let j = 0 ; j < competitionArray1.length ; j++){
                        this.scheduleArray.push({'league': competitionArray1[j], 'events': []})
                        for(let k = 0 ;  k < eventList.length ; k++){
                            if(eventList[k].competitions[0].name == competitionArray1[j] && eventList[k].time.status == 'NS'){
                                this.scheduleLength++
                                this.scheduleArray[j].events.push(eventList[k])
                            }
                        }
                    }

                    this.finishedArray = []
                    this.finishedLength = 0
                    for(let j = 0 ; j < competitionArray1.length ; j++){
                        this.finishedArray.push({'league': competitionArray1[j], 'events': []})
                        for(let k = 0 ;  k < eventList.length ; k++){
                            if(eventList[k].competitions[0].name == competitionArray1[j] && eventList[k].time.status == 'FT'){
                                this.finishedLength++
                                this.finishedArray[j].events.push(eventList[k])
                            }
                        }
                    }
                    for(let j = 0 ; j < this.finishedArray.length ; j++){
                        for(let jj = 0 ; jj < this.finishedArray[j].events.length ; jj++){
                            if(!this.finishedArray[j].events[jj].stats[0]){
                                let index = this.finishedArray[j].events.indexOf(this.finishedArray[j].events[jj]);
                                if (index > -1) {
                                    jj = jj - 1
                                    this.finishedArray[j].events.splice(index, 1);
                                }
                            }
                        }
                    }

                })
            },
            sortJSON(data, key){
                return data.sort(function(a, b) {
                    var x = a[key]; var y = b[key];
                    return ((x < y) ? -1 : ((x > y) ? 1 : 0));
                });
            },
        },
        created() {
            this.readData()
            this.sockets.listener.subscribe('UpdateStats', (data1) => {
                let data = []
                let cData = []
                for(let i = 0 ; i < data1.length ; i++){
                    data[i] = data1[i].updateArray
                    cData[i] = data1[i].currentData
                }

                for(let i = 0 ; i < data.length ; i++){
                    if(data[i]){
                        let check_new = 0
                        for(let j = 0 ; j < this.eventArray.length ; j++){
                            for(let k = 0 ; k < this.eventArray[j].events.length ; k++){
                                if(this.eventArray[j].events[k].main_data._id == data[i]._id && cData[i].stats[0]){
                                    check_new = 1
                                    if(cData[i].time.status != 'LIVE' && cData[i].time.status != 'ET'){
                                        this.readData()
                                    }
                                    this.eventArray[j].events[k].home.time = cData[i].time.minute
                                    if(cData[i].time.injury_time != null){
                                        this.eventArray[j].events[k].home.time = cData[i].time.minute + '+' + cData[i].time.injury_time
                                    }
                                    if(cData[i].time.status == 'HT'){
                                        this.eventArray[j].events[k].home.time == 'HT'
                                    }

                                    if(this.eventArray[j].events[k].home.id === data[i].stats[0].team_id){
                                        this.eventArray[j].events[k].home.score = data[i].scores.localteam_score
                                        this.eventArray[j].events[k].away.score = data[i].scores.visitorteam_score
                                        console.log('on-goal===>', data[i])
                                        this.eventArray[j].events[k].home.on = data[i].stats[0].shots.ongoal - data[i].stats_ten[0][0].shots.ongoal
                                        this.eventArray[j].events[k].away.on = data[i].stats[1].shots.ongoal - data[i].stats_ten[0][1].shots.ongoal
                                        this.eventArray[j].events[k].home.off = data[i].stats[0].shots.offgoal - data[i].stats_ten[0][0].shots.offgoal
                                        this.eventArray[j].events[k].away.off = data[i].stats[1].shots.offgoal - data[i].stats_ten[0][1].shots.offgoal
                                        this.eventArray[j].events[k].home.blk = data[i].stats[0].shots.blocked - data[i].stats_ten[0][0].shots.blocked
                                        this.eventArray[j].events[k].away.blk = data[i].stats[1].shots.blocked - data[i].stats_ten[0][1].shots.blocked
                                        this.eventArray[j].events[k].home.in = data[i].stats[0].shots.insidebox - data[i].stats_ten[0][0].shots.insidebox
                                        this.eventArray[j].events[k].away.in = data[i].stats[1].shots.insidebox - data[i].stats_ten[0][1].shots.insidebox
                                        this.eventArray[j].events[k].home.out = data[i].stats[0].shots.outsidebox - data[i].stats_ten[0][0].shots.outsidebox
                                        this.eventArray[j].events[k].away.out = data[i].stats[1].shots.outsidebox - data[i].stats_ten[0][1].shots.outsidebox
                                        this.eventArray[j].events[k].home.cnr = data[i].stats[0].corners - data[i].stats_ten[0][0].corners
                                        this.eventArray[j].events[k].away.cnr = data[i].stats[1].corners - data[i].stats_ten[0][1].corners
                                        this.eventArray[j].events[k].home.da = data[i].stats[0].attacks.dangerous_attacks - data[i].stats_ten[0][0].attacks.dangerous_attacks
                                        this.eventArray[j].events[k].away.da = data[i].stats[1].attacks.dangerous_attacks - data[i].stats_ten[0][1].attacks.dangerous_attacks

                                        this.eventArray[j].events[k].home.poss =data[i].stats_ten[0][0].possessiontime
                                        this.eventArray[j].events[k].away.poss =data[i].stats_ten[0][1].possessiontime

                                        if(data[i].stats[0].passes && data[i].stats_ten[0][0]){
                                            if(data[i].stats_ten[0][0].passes){
                                                this.eventArray[j].events[k].home.pas = data[i].stats[0].passes.total - data[i].stats_ten[0][0].passes.total
                                                this.eventArray[j].events[k].away.pas = data[i].stats[1].passes.total - data[i].stats_ten[0][1].passes.total

                                                this.eventArray[j].events[k].home.acc = data[i].stats[0].passes.accurate - data[i].stats_ten[0][0].passes.accurate
                                                this.eventArray[j].events[k].away.acc = data[i].stats[1].passes.accurate - data[i].stats_ten[0][1].passes.accurate
                                            }
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.pas = null
                                            this.eventArray[j].events[k].away.pas = null
                                            this.eventArray[j].events[k].home.acc = null
                                            this.eventArray[j].events[k].away.acc = null
                                        }

                                        this.eventArray[j].events[k].home.atk = data[i].stats[0].attacks.attacks - data[i].stats_ten[0][0].attacks.attacks
                                        this.eventArray[j].events[k].away.atk = data[i].stats[1].attacks.attacks - data[i].stats_ten[0][1].attacks.attacks
                                        this.eventArray[j].events[k].home.ofs = data[i].stats[0].offsides - data[i].stats_ten[0][0].offsides
                                        this.eventArray[j].events[k].away.ofs = data[i].stats[1].offsides - data[i].stats_ten[0][1].offsides
                                        this.eventArray[j].events[k].home.sav = data[i].stats[0].saves - data[i].stats_ten[0][0].saves
                                        this.eventArray[j].events[k].away.sav = data[i].stats[1].saves - data[i].stats_ten[0][1].saves
                                        if(data[i].stats[0].substitutions != null){
                                            this.eventArray[j].events[k].home.sbst = data[i].stats[0].substitutions - data[i].stats_ten[0][0].substitutions
                                            this.eventArray[j].events[k].away.sbst = data[i].stats[1].substitutions - data[i].stats_ten[0][1].substitutions
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.sbst = null
                                            this.eventArray[j].events[k].away.sbst = null
                                        }
                                        this.eventArray[j].events[k].home.red = data[i].stats[0].redcards - data[i].stats_ten[0][0].redcards
                                        this.eventArray[j].events[k].away.red = data[i].stats[1].redcards - data[i].stats_ten[0][1].redcards
                                        this.eventArray[j].events[k].home.fou = data[i].stats[0].fouls - data[i].stats_ten[0][0].fouls
                                        this.eventArray[j].events[k].away.fou = data[i].stats[1].fouls - data[i].stats_ten[0][1].fouls
                                        if(data[i].stats[0].goal_attempts != null){
                                            this.eventArray[j].events[k].home.g_att = data[i].stats[0].goal_attempts - data[i].stats_ten[0][0].goal_attempts
                                            this.eventArray[j].events[k].away.g_att = data[i].stats[1].goal_attempts - data[i].stats_ten[0][1].goal_attempts
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.g_att = null
                                            this.eventArray[j].events[k].away.g_att = null
                                        }
                                        if(data[i].stats[0].ball_safe != null){
                                            this.eventArray[j].events[k].home.safe = data[i].stats[0].ball_safe - data[i].stats_ten[0][0].ball_safe
                                            this.eventArray[j].events[k].away.safe = data[i].stats[1].ball_safe - data[i].stats_ten[0][1].ball_safe
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.safe = null
                                            this.eventArray[j].events[k].away.safe = null
                                        }

                                        if(data[i].stats[0].goals > this.eventArray[j].events[k].home.goal){
                                            this.eventArray[j].events[k].home.flash = 1
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.flash = 0
                                        }

                                        if(data[i].stats[1].goals > this.eventArray[j].events[k].away.goal){
                                            this.eventArray[j].events[k].away.flash = 1
                                        }
                                        else{
                                            this.eventArray[j].events[k].away.flash = 0
                                        }

                                        this.eventArray[j].events[k].home.goal = data[i].stats[0].goals - data[i].stats_ten[0][0].goals
                                        this.eventArray[j].events[k].away.goal = data[i].stats[1].goals - data[i].stats_ten[0][1].goals
                                    }
                                    else{
                                        this.eventArray[j].events[k].home.score = data[i].stats[1].goals - data[i].stats_ten[0][1].goals
                                        this.eventArray[j].events[k].away.score = data[i].stats[0].goals - data[i].stats_ten[0][0].goals
                                        this.eventArray[j].events[k].home.on = data[i].stats[1].shots.ongoal - data[i].stats_ten[0][1].shots.ongoal
                                        this.eventArray[j].events[k].away.on = data[i].stats[0].shots.ongoal - data[i].stats_ten[0][0].shots.ongoal
                                        this.eventArray[j].events[k].home.off = data[i].stats[1].shots.offgoal - data[i].stats_ten[0][1].shots.offgoal
                                        this.eventArray[j].events[k].away.off = data[i].stats[0].shots.offgoal - data[i].stats_ten[0][0].shots.offgoal
                                        this.eventArray[j].events[k].home.blk = data[i].stats[1].shots.blocked - data[i].stats_ten[0][1].shots.blocked
                                        this.eventArray[j].events[k].away.blk = data[i].stats[0].shots.blocked - data[i].stats_ten[0][0].shots.blocked
                                        this.eventArray[j].events[k].home.in = data[i].stats[1].shots.insidebox - data[i].stats_ten[0][1].shots.insidebox
                                        this.eventArray[j].events[k].away.in = data[i].stats[0].shots.insidebox - data[i].stats_ten[0][0].shots.insidebox
                                        this.eventArray[j].events[k].home.out = data[i].stats[1].shots.outsidebox - data[i].stats_ten[0][1].shots.outsidebox
                                        this.eventArray[j].events[k].away.out = data[i].stats[0].shots.outsidebox - data[i].stats_ten[0][0].shots.outsidebox
                                        this.eventArray[j].events[k].home.cnr = data[i].stats[1].corners - data[i].stats_ten[0][1].corners
                                        this.eventArray[j].events[k].away.cnr = data[i].stats[0].corners - data[i].stats_ten[0][0].corners
                                        this.eventArray[j].events[k].home.da = data[i].stats[1].attacks.dangerous_attacks - data[i].stats_ten[0][1].attacks.dangerous_attacks
                                        this.eventArray[j].events[k].away.da = data[i].stats[0].attacks.dangerous_attacks - data[i].stats_ten[0][0].attacks.dangerous_attacks

                                        this.eventArray[j].events[k].home.poss =data[i].stats_ten[0][1].possessiontime
                                        this.eventArray[j].events[k].away.poss =data[i].stats_ten[0][0].possessiontime

                                        if(data[i].stats[0].passes != null){
                                            this.eventArray[j].events[k].home.pas = data[i].stats[1].passes.total - data[i].stats_ten[0][1].passes.total
                                            this.eventArray[j].events[k].away.pas = data[i].stats[0].passes.total - data[i].stats_ten[0][0].passes.total
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.pas = null
                                            this.eventArray[j].events[k].away.pas = null
                                        }
                                        if(data[i].stats[0].passes != null){
                                            this.eventArray[j].events[k].home.acc = data[i].stats[1].passes.accurate - data[i].stats_ten[0][1].passes.accurate
                                            this.eventArray[j].events[k].away.acc = data[i].stats[0].passes.accurate - data[i].stats_ten[0][0].passes.accurate
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.acc = null
                                            this.eventArray[j].events[k].away.acc = null
                                        }
                                        this.eventArray[j].events[k].home.atk = data[i].stats[1].attacks.attacks - data[i].stats_ten[0][1].attacks.attacks
                                        this.eventArray[j].events[k].away.atk = data[i].stats[0].attacks.attacks - data[i].stats_ten[0][0].attacks.attacks
                                        this.eventArray[j].events[k].home.ofs = data[i].stats[1].offsides - data[i].stats_ten[0][1].offsides
                                        this.eventArray[j].events[k].away.ofs = data[i].stats[0].offsides - data[i].stats_ten[0][0].offsides
                                        this.eventArray[j].events[k].home.sav = data[i].stats[1].saves - data[i].stats_ten[0][1].saves
                                        this.eventArray[j].events[k].away.sav = data[i].stats[0].saves - data[i].stats_ten[0][0].saves
                                        if(data[i].stats[0].substitutions != null){
                                            this.eventArray[j].events[k].home.sbst = data[i].stats[1].substitutions - data[i].stats_ten[0][1].substitutions
                                            this.eventArray[j].events[k].away.sbst = data[i].stats[0].substitutions - data[i].stats_ten[0][0].substitutions
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.sbst = null
                                            this.eventArray[j].events[k].away.sbst = null
                                        }
                                        this.eventArray[j].events[k].home.red = data[i].stats[1].redcards - data[i].stats_ten[0][1].redcards
                                        this.eventArray[j].events[k].away.red = data[i].stats[0].redcards - data[i].stats_ten[0][0].redcards
                                        this.eventArray[j].events[k].home.fou = data[i].stats[1].fouls - data[i].stats_ten[0][1].fouls
                                        this.eventArray[j].events[k].away.fou = data[i].stats[0].fouls - data[i].stats_ten[0][0].fouls
                                        if(data[i].stats[0].goal_attempts != null){
                                            this.eventArray[j].events[k].home.g_att = data[i].stats[1].goal_attempts - data[i].stats_ten[0][1].goal_attempts
                                            this.eventArray[j].events[k].away.g_att = data[i].stats[0].goal_attempts - data[i].stats_ten[0][0].goal_attempts
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.g_att = null
                                            this.eventArray[j].events[k].away.g_att = null
                                        }
                                        if(data[i].stats[0].ball_safe != null){
                                            this.eventArray[j].events[k].home.safe = data[i].stats[1].ball_safe - data[i].stats_ten[0][1].ball_safe
                                            this.eventArray[j].events[k].away.safe = data[i].stats[0].ball_safe - data[i].stats_ten[0][0].ball_safe
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.safe = null
                                            this.eventArray[j].events[k].away.safe = null
                                        }

                                        if(data[i].stats[0].goals > this.eventArray[j].events[k].home.goal){
                                            this.eventArray[j].events[k].home.flash = 1
                                        }
                                        else{
                                            this.eventArray[j].events[k].home.flash = 0
                                        }

                                        if(data[i].stats[1].goals > this.eventArray[j].events[k].away.goal){
                                            this.eventArray[j].events[k].away.flash = 1
                                        }
                                        else{
                                            this.eventArray[j].events[k].away.flash = 0
                                        }

                                        this.eventArray[j].events[k].home.goal = data[i].stats[1].goals - data[i].stats_ten[0][1].goals
                                        this.eventArray[j].events[k].away.goal = data[i].stats[0].goals - data[i].stats_ten[0][0].goals
                                    }
                                    //-----------------------------------------------------------------------------------------------
                                    if(data[i].stats[0].goals - data[i].stats_ten[0][0].goals > this.eventArray[j].events[k].home.goal){
                                        this.eventArray[j].events[k].home.flash = 1
                                    }
                                    else{
                                        this.eventArray[j].events[k].home.flash = 0
                                    }
                                    this.eventArray[j].events[k].home.goal = data[i].stats[0].goals - data[i].stats_ten[0][0].goals

                                    if(data[i].stats[1].goals - data[i].stats_ten[0][1].goals > this.eventArray[j].events[k].away.goal){
                                        this.eventArray[j].events[k].away.flash = 1
                                    }
                                    else{
                                        this.eventArray[j].events[k].away.flash = 0
                                    }
                                    this.eventArray[j].events[k].away.goal = data[i].stats[1].goals - data[i].stats_ten[0][1].goals
                                    //---------------------------------------Total Part-------------------------------------------
                                    if(this.eventArray[j].events[k].home.id === data[i].stats[0].team_id){
                                        this.eventArray[j].events[k].homeT.on = data[i].stats[0].shots.ongoal
                                        this.eventArray[j].events[k].awayT.on = data[i].stats[1].shots.ongoal
                                        this.eventArray[j].events[k].homeT.off = data[i].stats[0].shots.offgoal
                                        this.eventArray[j].events[k].awayT.off = data[i].stats[1].shots.offgoal
                                        this.eventArray[j].events[k].homeT.blk = data[i].stats[0].shots.blocked
                                        this.eventArray[j].events[k].awayT.blk = data[i].stats[1].shots.blocked
                                        this.eventArray[j].events[k].homeT.in = data[i].stats[0].shots.insidebox
                                        this.eventArray[j].events[k].awayT.in = data[i].stats[1].shots.insidebox
                                        this.eventArray[j].events[k].homeT.out = data[i].stats[0].shots.outsidebox
                                        this.eventArray[j].events[k].awayT.out = data[i].stats[1].shots.outsidebox
                                        this.eventArray[j].events[k].homeT.cnr = data[i].stats[0].corners
                                        this.eventArray[j].events[k].awayT.cnr = data[i].stats[1].corners
                                        this.eventArray[j].events[k].homeT.da = data[i].stats[0].attacks.dangerous_attacks
                                        this.eventArray[j].events[k].awayT.da = data[i].stats[1].attacks.dangerous_attacks
                                        this.eventArray[j].events[k].homeT.goal = data[i].stats[0].goals
                                        this.eventArray[j].events[k].awayT.goal = data[i].stats[1].goals

                                        this.eventArray[j].events[k].homeT.poss = data[i].stats[0].possessiontime
                                        this.eventArray[j].events[k].awayT.poss = data[i].stats[1].possessiontime
                                        if(data[i].stats[0].passes != null){
                                            this.eventArray[j].events[k].homeT.pas = data[i].stats[0].passes.total
                                            this.eventArray[j].events[k].awayT.pas = data[i].stats[1].passes.total
                                        }
                                        else{
                                            this.eventArray[j].events[k].homeT.pas = null
                                            this.eventArray[j].events[k].awayT.pas = null
                                        }
                                        if(data[i].stats[0].passes != null){
                                            this.eventArray[j].events[k].homeT.acc = data[i].stats[0].passes.accurate
                                            this.eventArray[j].events[k].awayT.acc = data[i].stats[1].passes.accurate
                                        }
                                        else{
                                            this.eventArray[j].events[k].homeT.acc = null
                                            this.eventArray[j].events[k].awayT.acc = null
                                        }
                                        this.eventArray[j].events[k].homeT.atk = data[i].stats[0].attacks.attacks
                                        this.eventArray[j].events[k].awayT.atk = data[i].stats[1].attacks.attacks
                                        this.eventArray[j].events[k].homeT.ofs = data[i].stats[0].offsides
                                        this.eventArray[j].events[k].awayT.ofs = data[i].stats[1].offsides
                                        this.eventArray[j].events[k].homeT.sav = data[i].stats[0].saves
                                        this.eventArray[j].events[k].awayT.sav = data[i].stats[1].saves
                                        this.eventArray[j].events[k].homeT.sbst = data[i].stats[0].substitutions
                                        this.eventArray[j].events[k].awayT.sbst = data[i].stats[1].substitutions
                                        this.eventArray[j].events[k].homeT.red = data[i].stats[0].redcards
                                        this.eventArray[j].events[k].awayT.red = data[i].stats[1].redcards
                                        this.eventArray[j].events[k].homeT.fou = data[i].stats[0].fouls
                                        this.eventArray[j].events[k].awayT.fou = data[i].stats[1].fouls
                                        this.eventArray[j].events[k].homeT.g_att = data[i].stats[0].goal_attempts
                                        this.eventArray[j].events[k].awayT.g_att = data[i].stats[1].goal_attempts
                                        this.eventArray[j].events[k].homeT.safe = data[i].stats[0].ball_safe
                                        this.eventArray[j].events[k].awayT.safe = data[i].stats[1].ball_safe
                                    }
                                    else{
                                        this.eventArray[j].events[k].homeT.on = data[i].stats[1].shots.ongoal
                                        this.eventArray[j].events[k].awayT.on = data[i].stats[0].shots.ongoal
                                        this.eventArray[j].events[k].homeT.off = data[i].stats[1].shots.offgoal
                                        this.eventArray[j].events[k].awayT.off = data[i].stats[0].shots.offgoal
                                        this.eventArray[j].events[k].homeT.blk = data[i].stats[1].shots.blocked
                                        this.eventArray[j].events[k].awayT.blk = data[i].stats[0].shots.blocked
                                        this.eventArray[j].events[k].homeT.in = data[i].stats[1].shots.insidebox
                                        this.eventArray[j].events[k].awayT.in = data[i].stats[0].shots.insidebox
                                        this.eventArray[j].events[k].homeT.out = data[i].stats[1].shots.outsidebox
                                        this.eventArray[j].events[k].awayT.out = data[i].stats[0].shots.outsidebox
                                        this.eventArray[j].events[k].homeT.cnr = data[i].stats[1].corners
                                        this.eventArray[j].events[k].awayT.cnr = data[i].stats[0].corners
                                        this.eventArray[j].events[k].homeT.da = data[i].stats[1].attacks.dangerous_attacks
                                        this.eventArray[j].events[k].awayT.da = data[i].stats[0].attacks.dangerous_attacks
                                        this.eventArray[j].events[k].homeT.goal = data[i].stats[1].goals
                                        this.eventArray[j].events[k].awayT.goal = data[i].stats[0].goals

                                        this.eventArray[j].events[k].homeT.poss = data[i].stats[1].possessiontime
                                        this.eventArray[j].events[k].awayT.poss = data[i].stats[0].possessiontime
                                        if(data[i].stats[0].passes != null){
                                            this.eventArray[j].events[k].homeT.pas = data[i].stats[1].passes.total
                                            this.eventArray[j].events[k].awayT.pas = data[i].stats[0].passes.total
                                        }
                                        else{
                                            this.eventArray[j].events[k].homeT.pas = null
                                            this.eventArray[j].events[k].awayT.pas = null
                                        }
                                        if(data[i].stats[0].passes != null){
                                            this.eventArray[j].events[k].homeT.acc = data[i].stats[1].passes.accurate
                                            this.eventArray[j].events[k].awayT.acc = data[i].stats[0].passes.accurate
                                        }
                                        else{
                                            this.eventArray[j].events[k].homeT.acc = null
                                            this.eventArray[j].events[k].awayT.acc = null
                                        }
                                        this.eventArray[j].events[k].homeT.atk = data[i].stats[1].attacks.attacks
                                        this.eventArray[j].events[k].awayT.atk = data[i].stats[0].attacks.attacks
                                        this.eventArray[j].events[k].homeT.ofs = data[i].stats[1].offsides
                                        this.eventArray[j].events[k].awayT.ofs = data[i].stats[0].offsides
                                        this.eventArray[j].events[k].homeT.sav = data[i].stats[1].saves
                                        this.eventArray[j].events[k].awayT.sav = data[i].stats[0].saves
                                        this.eventArray[j].events[k].homeT.sbst = data[i].stats[1].substitutions
                                        this.eventArray[j].events[k].awayT.sbst = data[i].stats[0].substitutions
                                        this.eventArray[j].events[k].homeT.red = data[i].stats[1].redcards
                                        this.eventArray[j].events[k].awayT.red = data[i].stats[0].redcards
                                        this.eventArray[j].events[k].homeT.fou = data[i].stats[1].fouls
                                        this.eventArray[j].events[k].awayT.fou = data[i].stats[0].fouls
                                        this.eventArray[j].events[k].homeT.g_att = data[i].stats[1].goal_attempts
                                        this.eventArray[j].events[k].awayT.g_att = data[i].stats[0].goal_attempts
                                        this.eventArray[j].events[k].homeT.safe = data[i].stats[1].ball_safe
                                        this.eventArray[j].events[k].awayT.safe = data[i].stats[0].ball_safe
                                    }
                                    //------------------------------------------------------------------------------------------------
                                }
                            }
                        }
                        if(check_new == 0 && data[i].time.status == 'LIVE'){
                            this.readData()
                        }
                    }
                }
            })
            //---------------------------------------------------------------
        }
    }
</script>
<style>
    .season-detail{
<<<<<<< HEAD
        width: 5.5%!important;
        min-width: 24px!important;
        font-size: 10px!important;
    }
    .bottom-part.bottom-part1 .detail{
        width: 11%!important;
    }
    .bottom-part.bottom-part1 .index_detail{
        width: 14%!important;
=======
        width: 5.85%!important;
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
    }
    .live-stats-container .nav-item a{
        height: 30px;
        margin-bottom: 1px;
        padding-top: 5px;
    }
    .c-subheader{
        padding: 0;
        height: 30px!important;
        min-height: 30px!important;
    }
    .breadcrumb{
        padding: 0!important;
        padding-top: 4px!important;
    }
    .season-part .detail{
        width: 5%;
    }
    .c-header-nav {
        min-height: 45px!important;
        height: 45px!important;
    }
    @media (min-width: 992px){
        html:not([dir="rtl"]) .c-sidebar.c-sidebar-lg-show:not(.c-sidebar-right).c-sidebar-fixed ~ .c-wrapper, html:not([dir="rtl"]) .c-sidebar.c-sidebar-show:not(.c-sidebar-right).c-sidebar-fixed ~ .c-wrapper {
            margin-left: 180px;
        }
    }
    .c-sidebar{
        width: 180px;
    }
    @media (min-width: 992px){
        .c-sidebar-minimized.c-sidebar-fixed {
            z-index: 1031;
            width: 56px;
        }
    }
    @media (min-width: 992px){
        html:not([dir="rtl"]) .c-sidebar.c-sidebar-lg-show:not(.c-sidebar-right), html:not([dir="rtl"]) .c-sidebar.c-sidebar-show:not(.c-sidebar-right) {
            margin-left: 0;
        }
    }
    @media (min-width: 992px){
        html:not([dir="rtl"]) .c-sidebar.c-sidebar-lg-show:not(.c-sidebar-right).c-sidebar-fixed.c-sidebar-minimized ~ .c-wrapper, html:not([dir="rtl"]) .c-sidebar.c-sidebar-show:not(.c-sidebar-right).c-sidebar-fixed.c-sidebar-minimized ~ .c-wrapper {
            margin-left: 56px;
        }
    }

    .live-stats-container .nav-item{
        font-size: 14px!important;
    }
    .live-stats-container .card{
        border: none
    }
    .live-stats-container div{
        font-size: 12px!important;
    }
<<<<<<< HEAD
    .live-stats-container .season-detail{
        font-size: 10px!important;
    }
=======
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
    .live-stats-container .card-body{
        padding: 5px;
    }
    .c-main{
        padding: 0;
    }
    .c-main .container-fluid{
        padding: 0;
    }
    .live-stats-container .nav-item{
        width: 25%;
        text-align: center;
        font-size: 16px;
    }
    .live-stats-container .tab-content{
        padding: 0px;
    }
    .header .header-content{
        font-size: 16px;
        font-weight: 600;
        padding: 2px 6px;
        text-align: center;
        background: #cecece;
    }
    .detail{
        width: 10%;
        min-width: 26px;
        float: left;
        padding:0;
        text-align: center;
        font-size: 12px;
    }
    .detail_total .detail{
        min-width: 28px;
    }
    .finished-tab .detail{
        width: 11%;
    }
    .index_detail{
<<<<<<< HEAD
        width: 14%!important;
=======
        width: 14%;
>>>>>>> 09b413546515adaac4a5af376284e057434dbddc
    }
    .time_manner{
        animation: splash infinite 1.5s;
    }
    .goal_manner{
        animation: splash1 infinite 1.5s;
    }
    @keyframes splash {
        0% {
            color: white;
        }
        25% {
            color: #dd524f;
        }
        50% {
            color: #fa1121;
        }
        70%{
            color:#dd524f;
        }
        100%{
            color:white;
        }
    }
    @keyframes splash1 {
        0% {
            color: white;
        }
        25% {
            color: #16ad57;
        }
        50% {
            color: #199e69;
        }
        70%{
            color: #28b06f;
        }
        100%{
            color:white;
        }
    }
    .slide-fade-enter-active {
        -webkit-animation-name: example;
        -webkit-animation-duration: 3s;
        -webkit-animation-iteration-count: 1;
        animation-name: example;
        animation-duration: 3s;
        animation-iteration-count: 1;
    }

    .livenow {
        -webkit-animation-name: example;
        -webkit-animation-duration: 3s;
        -webkit-animation-iteration-count: 1;
        animation-name: example;
        animation-duration: 3s;
        animation-iteration-count: 1;
    }
    @keyframes example {
        0% {
            background-color: rgba(166, 216, 255, 0.53);
        }
        50% {
            background-color: rgba(18, 18, 18, 0.34);
        }
        100% {
            background-color: rgba(250, 201, 209, 0.53);
        }
        100% {
            background-color: rgba(243, 196, 0, 0.5)!important;
        }
    }
    @media screen and (max-width: 600px) {
        .table-cell input{
            max-width: 44px;
        }
    }
</style>
