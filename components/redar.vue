
<template>
    <div class="redar">
        <div class="xiangmu">基础分析</div>
        <div class="leida">
            <div id="main2" ></div>
        </div>
    </div>
</template>
<script>
// 雷达图组件
import echarts from 'echarts'
export default {
    name:"redar",
    methods:{
        leida(){
            var myChart1 = echarts.init(document.getElementById('main2')) 
          var  option1 = {
    title: {
        text: ''
    },
    tooltip: {},
    legend: {
        data: []
    },
    radar: {
        // shape: 'circle',
        name: {
            textStyle: {
                color: '#fff',
                borderRadius: 3,
                padding: [3, 5]
           }
        },
          // 设置雷达图中间射线的颜色
        axisLine: {
            lineStyle: {
                color: '#272B49',
                },
        },
        indicator: [
           { name: '价格', max: 6500},
           { name: '指数', max: 16000},
           { name: '同比', max: 30000},
           { name: '环比', max: 38000}
        //    { name: '消防材料', max: 52000},
        //    { name: '建筑用材', max: 25000}
        ],
      splitArea : {
                show : true,
                areaStyle : {
                    color: ["#00062A","#00062A"]  // 图表背景网格区域的颜色
                }
            },
             splitLine : {
                show : true,
                lineStyle : {
                    width : 1,
                    color : '#272B49' // 图表背景网格线的颜色
                }
            }
    },
    series: [{
        name: '',
        type: 'radar',
        // areaStyle: {normal: {}},
        data : [
            {
                value : [4300, 10000, 28000, 35000, 50000, 19000],
                name : '',
                symbol:'none',
                 itemStyle: {
                        normal:{
                            color : "#0CDAFB",  // 图表中各个图区域的边框线颜色
                        lineStyle:{
                            width:16
                        }
                        }
                    }
            },
             {
                value : [5000, 14000, 28000, 31000, 42000, 21000],
                name : '',
                symbol:'none',
                 itemStyle: {
                        normal: {
                            color : "#FBB329"   // 图表中各个图区域的边框线颜色
                        }
                    }
            }
        ]
    }]
};
      myChart1.setOption(option1);
        }
    },
    mounted(){
        this.leida()
    }
}
</script>
<style lang="stylus" scoped>
px2vw(px) 
    px/1920*100 vw 

px2vh(px)
    px/1080*100 vh

.redar
    width px2vw(380)
    height px2vh(400) 
    margin-top px2vh(20)

.xiangmu
    width px2vw(380) 
    height px2vh(50) 
    background url(../static/img/right.png)
    background-size 100% 100%
    line-height px2vh(50)
    font-size 16px
    font-family MicrosoftYaHei-Bold
    font-weight bold
    color rgba(255,255,255,1) 
.leida
    width px2vw(380) 
    height px2vh(340) 
    background url(../static/img/lei.png)
    background-size 100% 100%
    margin-top px2vh(10)

#main2
    height px2vh(340)
    div 
        height 100% 
        canvas
           width px2vw(364) 
           height px2vh(291) 
</style>