
<template>
    <div class="ditu">
        <div class="shuzi">
            <div class="jiance">
                <span>监测地区</span>
                <p class="font">1,789,654</p>
            </div>
            <div class="caiyang">
                <span>采样数据</span>
                <p class="font">198,895,054,03</p>
            </div>
        </div>
        <!-- <div class="hov">
            <p>昆明</p>
            <p>材料数据<span class='font'>68,805条</span></p>
            <p>更新时间<span class='font'>2018.01.01</span></p>
        </div> -->
        <div class="map">
            <!--YN @choseMap='chose_map' v-if='!city_code || city_code.length ==0'></YN>
            <DQ v-if='city_code == "533400000000"' @showIfra = 'show_ifra'></DQ>
            <NJ v-if='city_code == "533300000000"' @showIfra = 'show_ifra'></NJ>
            <DH v-if='city_code == "533100000000"' @showIfra = 'show_ifra'></DH>
            <DL v-if='city_code == "532900000000"' @showIfra = 'show_ifra'></DL>
            <BN v-if='city_code == "532800000000"' @showIfra = 'show_ifra'></BN>
            <WS v-if='city_code == "532600000000"' @showIfra = 'show_ifra'></WS>
            <HH v-if='city_code == "532500000000"' @showIfra = 'show_ifra'></HH>
            <CX v-if='city_code == "532300000000"' @showIfra = 'show_ifra'></CX>
            <LC v-if='city_code == "530900000000"' @showIfra = 'show_ifra'></LC>
            <PE v-if='city_code == "530800000000"' @showIfra = 'show_ifra'></PE>
            <LJ v-if='city_code == "530700000000"' @showIfra = 'show_ifra'></LJ>
            <ZT v-if='city_code == "530600000000"' @showIfra = 'show_ifra'></ZT>
            <BS v-if='city_code == "530500000000"' @showIfra = 'show_ifra'></BS>
            
            <KM v-if='city_code == "530100000000"' @showIfra = 'show_ifra'></KM>
            <QJ v-if='city_code == "530300000000"' @showIfra = 'show_ifra'></QJ>
            <YX v-if='city_code == "530400000000"' @showIfra = 'show_ifra'></YX-->
        </div>
    </div>

</template>
<script>

import yn from '../static/YNprovince.json'
import echarts from 'echarts'
// 地图组件
import YN from './maps/ynMap.vue'//云南省
import KM from './maps/kunming.vue'//昆明
import QJ from './maps/qujing.vue'//曲靖
import YX from './maps/yuxi.vue'//玉溪
import BS from './maps/baoshan.vue'//保山
import ZT from './maps/zhaotong.vue'//昭通
import LJ from './maps/lijiang.vue'//丽江
import PE from './maps/puer.vue'//普洱
import LC from './maps/lincang.vue'//临沧
import CX from './maps/chuxiong.vue'//楚雄
import HH from './maps/honghe.vue'//红河
import WS from './maps/wenshan.vue'//文山
import BN from './maps/banna.vue'//版纳
import DL from './maps/dali.vue'//大理
import DH from './maps/dehong.vue'//德宏
import NJ from './maps/nujiang.vue'//怒江
import DQ from './maps/diqin.vue'//迪庆
import $ from 'jquery'

export default {
      data() {
        return {
            qu_url:'',
            city_code:'',
            show_qu:false
        }
    },
    props:{
        area: String
    },
    watch: {
        area(val) {
            console.log(val,90909)
            val.length == 0? this.city_code ='':''
        }
    },
    mounted() {
        this.init_map()
    },
    methods:{
        chose_map(val) {
            this.city_code = val.id
            this.$emit('chose_area', val)
        },
        show_ifra() {

        },
        init_map() {
            echarts.registerMap('yn', yn);
            const chart = echarts.init(document.getElementsByClassName('map')[0]);
            chart.setOption({
                series: [{
                    type: 'map',
                    map: 'yn',
                    itemStyle: {
                        normal: {
                            show:true,
                            label: {
                                show: true,//默认是否显示省份名称  
                                color:'#7284B2',//修改字体颜色
                                fontSiae:'14px' 
                            },
                            areaColor:'#142b66',//设置背景颜色
                            areaStyle:{
                                color:'red',
                            },
                            borderWidth:1,
                            borderColor:'#43bcff',//设置边框颜色
                        },
                        emphasis: {//鼠标移入动态的时候显示的默认样式
                            show:false,
                            label: {
                                show: true,//选中状态是否显示省份名称
                                color:'#fff',//修改字体颜色
                                fontSiae:'14px' 
                            },
                            textStyle:{
                                color:'red',
                            },
                            areaColor:'#43bcff',
                        },
                    },
                    //layoutCenter: ['100%', '100%'],
                    // 如果宽高比大于 1 则宽度为 100，如果小于 1 则高度为 100，保证了不超过 100x100 的区域
                    layoutSize: 100
                }],
                tooltip: {
                    trigger: `item`,
                    backgroundColor:'rgba(50,50,50,0)',
                    formatter:  `<div class='hov' style=" width:230px;
                                    height:112px;
                                    border:1px solid rgba(38, 57, 234, 1);
                                    border-radius:0px 10px 10px 10px; 
                                    podition:relative;
                                ">
                            <img src='static/img/hov.png' style='position:absolute;top:0;
                            left:0;width:100%;height:100%'/>
                            <p style="font-size:16px;
                            position: relative;
                            font-family:MicrosoftYaHei;
                            font-weight:400;
                            color:rgba(255,255,255,1);
                            display:block;
                            padding-left:22px;
                            padding-top:15px;
                            text-align:left">昆明</p>
                        <p style="font-size:16px;
                            position: relative;
                            font-family:MicrosoftYaHei;
                            font-weight:400;
                            color:rgba(255,255,255,1);
                            display:block;
                            padding-left:22px;
                            padding-top:15px;
                            text-align:left;">
                            材料价格
                            <span class='font' style="font-size:20px;
                            color:rgba(0,255,198,1);
                            margin-left:20px;">68,805</span>
                            <img src='static/img/downs.png'/>
                            </p>
                        <p style="font-size:16px;
                            position: relative;
                            font-family:MicrosoftYaHei;
                            font-weight:400;
                            color:rgba(255,255,255,1);
                            display:block;
                            padding-left:22px;
                            padding-top:15px;
                            text-align:left;">更新时间<span class='font' style="font-size:20px;
                            color:rgba(0,255,198,1);
                            margin-left:20px;">2018.01.01</span></p>
                    </div>`
                },
                grid:[{
                    left:"10%",
                    top:'10%',
                    bottom:'10%',
                    right:'10%'
                }]
            });
            chart.on('click', function (param){
                var selected = param.selected;
                console.log(param.name)
            });
        }
    },
    components:{
        YN,
        KM,
        QJ,
        YX,
        BS,
        ZT,
        LJ,
        PE,
        LC,
        CX,
        HH,
        WS,
        BN,
        DL,
        DH,
        NJ,
        DQ
    }
}
</script>
<style lang="stylus" scoped>
px2vw(px) 
    px/1920*100 vw 

px2vh(px)
    px/1080*100 vh

.ditu
    height px2vh(700) 
    padding px2vh(20) px2vw(20)
    overflow hidden
    box-sizing border-box
.shuzi
    width px2vw(1080)
    height px2vh(65) 
    margin-top px2vh(20)
    display flex
    justify-content space-around

.jiance,.caiyang
	text-align left
 
.jiance span,.caiyang span
    font-size 16px
    font-family MicrosoftYaHei
    font-weight 400
    color rgba(255,255,255,1)

.jiance p,.caiyang p
    font-size 50px
    color rgba(0,255,198,1)
.map
    width 100%
    height px2vh(605)
    margin 0 auto
    padding-top px2vh(30)
    box-sizing border-box
    div
       width 100%
       height 100%
       display flex
       justify-content center
       canvas
        width 100%
        height 100%

.hov
    width:230px;
    height:112px;
    border:1px solid rgba(38, 57, 234, 1);
    border-radius:0px 10px 10px 10px; 
    background  url(../static/img/hov.png)

.hov p
    font-size 16px
    font-family MicrosoftYaHei
    font-weight 400
    color rgba(255,255,255,1)
    display block
    padding-left px2vw(22)
    padding-top  px2vh(15)
    text-align left

.hov p>span
    font-size 20px
    color rgba(0,255,198,1)
    margin-left px2vw(20)
</style>
