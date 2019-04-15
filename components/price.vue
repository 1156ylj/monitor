
<template>
    <div class="price">
        <div class="jiage">价格对比</div>
        <div class="duibi">
             <div id="main"></div>
        </div>
    </div>
</template>
<script>
// 价格对比组件
import echarts from 'echarts'
export default {
    name:"price",
    data() {
        return {
            area:[{"id":"530100000000","name":"昆明市","level":"2","pid":"53","geocode":"102.832891,24.880095"},{"id":"530300000000","name":"曲靖市","level":"2","pid":"53","geocode":"103.796167,25.489999"},{"id":"530400000000","name":"玉溪市","level":"2","pid":"53","geocode":"102.546543,24.352036"},{"id":"530500000000","name":"保山市","level":"2","pid":"53","geocode":"99.161761,25.112046"},{"id":"530600000000","name":"昭通市","level":"2","pid":"53","geocode":"103.717465,27.338257"},{"id":"530700000000","name":"丽江市","level":"2","pid":"53","geocode":"100.227750,26.855047"},{"id":"530800000000","name":"普洱市","level":"2","pid":"53","geocode":"100.966512,22.825065"},{"id":"530900000000","name":"临沧市","level":"2","pid":"53","geocode":"100.079583,23.877573"},{"id":"532300000000","name":"楚雄彝族自治州","level":"2","pid":"53","geocode":"101.528068,25.045532"},{"id":"532500000000","name":"红河哈尼族彝族自治州","level":"2","pid":"53","geocode":"103.374799,23.363130"},{"id":"532600000000","name":"文山壮族苗族自治州","level":"2","pid":"53","geocode":"104.216248,23.400733"},{"id":"532800000000","name":"西双版纳傣族自治州","level":"2","pid":"53","geocode":"100.797777,22.007351"},{"id":"532900000000","name":"大理白族自治州","level":"2","pid":"53","geocode":"100.267638,25.606486"},{"id":"533100000000","name":"德宏傣族景颇族自治州","level":"2","pid":"53","geocode":"98.584895,24.433353"},{"id":"533300000000","name":"怒江傈僳族自治州","level":"2","pid":"53","geocode":"98.853097,25.852547"},{"id":"533400000000","name":"迪庆藏族自治州","level":"2","pid":"53","geocode":"99.702234,27.818882"}],
            areaList:[]
        }
    },
    methods:{
        reset_area() {
           // this.area.
            //this.areaList.push(list)
        },
        inits(){
            var myChart = echarts.init(document.getElementById('main'))
            var  option = {
                title: {
                    text: '',
                    subtext: ''
                },
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: 'shadow'
                    },
                },
                legend: {
                    icon : 'circle',
                    data: ['2018年', '2019年'],
                    textStyle:{
                        color:'#AAABBC'
                    }
                },
                grid: {
                    top:'15%',//距上边距
                    left:'5%',//距离左边距
                    right:'15%',//距离右边距
                    bottom:'5%',//距离下边距
                    containLabel: true
                },
                xAxis: {
                    show:false,
                    type: 'value',
                    boundaryGap: [0, 0.01],
                    splitLine:{
                        show:true   //去掉网格线
                        },
                        lineStyle:{
                            type:"solid"
                        }
                },
                yAxis: {
                    type: 'category',
                    data: ['昆明','曲靖','大理','丽江'],
                    axisLine:{     
                                    show:false,//y轴坐标轴
                                    lineStyle:{
                                        color:'#AAABBC',
                                    }
                                } ,
                        axisTick: {
                        show:false //刻度线
                    },

                },
                series: [
                    {
                        name: '2018年',
                        type: 'bar',
                        barGap:'80%',/*多个并排柱子设置柱子之间的间距*/
                        barCategoryGap:'20%',/*多个并排柱子设置柱子之间的间距*/
                        data: [18203, 13489, 29034, 104970],
                        itemStyle:{
                            normal:{
                                color:'#302ffe',
                                label: {
                                    show: true,
                                    position: 'right',
                                    textStyle: {
                                        color: '#AAABBC'
                                }
                            }
                                }
                        }         
                    },
                    {
                        name: '2019年',
                        type: 'bar',
                        barGap:'80%',
                        barCategoryGap:'20%',
                        data: [19325, 23438, 31000, 121594],
                        itemStyle:{
                            normal:{
                                color:'#10bfe3',
                                label: {
                                    show: true,
                                    position: 'right',
                                    textStyle: {
                                        color: '#AAABBC'
                                }
                            }
                                }
                        }
                    },

                ]
            };
         myChart.setOption(option);
        }
      
    },
    mounted(){
        this.inits()
    }
}
</script>
<style lang="stylus" scoped>
px2vw(px) 
    px/1920*100 vw 

px2vh(px)
    px/1080*100 vh

px2vh(px)
    px/1080*100 vh

.price
    width px2vw(380) 
    height px2vh(300) 
    margin-top  px2vh(20) 
    margin-left px2vw(20) 

.jiage
    width px2vw(380) 
    height px2vh(50) 
    background url(../static/img/right.png)
    background-size 100% 100%
    line-height px2vh(50)
    font-size 16px
    font-family MicrosoftYaHei-Bold
    font-weight bold
    color rgba(255,255,255,1) 

.duibi
    width px2vw(380) 
    height px2vh(240)
    background url(../static/img/price.png)
    background-size 100% 100%
    padding-top px2vh(15) 
    box-sizing border-box
    overflow auto
    margin-top px2vh(10) 
#main
    height px2vh(220)
    padding-top px2vh(10) 
    div 
        height 100%
</style>