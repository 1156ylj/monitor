
<template>
    <div class="link">
         <div class="cate-price">材料价格环比</div>
        <div class="huanbi">
            <div id="mains" style="width: 280px;height:200px;"></div>
        </div>
    </div>
</template>
<script>
// 材料环比组件
import echarts from 'echarts'
export default {
    name:"cate-price",
    methods:{
        huanbi(){
            var myCharts = echarts.init(document.getElementById('mains'))
            var  options = {
                title : {
                    text: '材料价格环比图',
                    x:'left',
                    textStyle:{
                        color:'#AAABBC',
                        fontSize:12
                    }
                },
                tooltip : {
                    trigger: 'item',
                    formatter: "{a} <br/>{b} : {c} ({d}%)"
                },
                color:['#13f5ff','#3405ff','#b225ff'],   //环形颜色
                legend: {
                    show:false,
                    orient: 'vertical',
                    x:'left',
                    y:'center',
                },
                series: [
                    {
                        name:'',
                        type:'pie',
                        radius: ['50%', '70%'],
                        avoidLabelOverlap: false,
                        clockWise:false,
                        label: {
                            normal: {
                                show: false,
                                position: 'center'
                            },
                            emphasis: {
                                show: true,
                                textStyle: {
                                    fontSize: '30',
                                    fontWeight: 'bold'
                                }
                            }
                        },
                        labelLine: {
                            normal: {
                                show: false
                            }
                        },
                        data:[
                        {value:335, name:'钢材'},
                        {value:310, name:'地区材料'},
                        {value:234, name:'管材'},
                        ],
                        itemStyle: {
                            emphasis: {
                                shadowBlur: 10,
                                shadowOffsetX: 0,
                                shadowColor: 'rgba(0, 0, 0, 0.2)'
                            }
                        },
                        labelLine:{  
                            normal:{  
                                length:8,  // 改变标示线的长度
                            },
                        },
                    label: {
                        normal: {
                            textStyle: {
                                    color: 'white'  // 改变标示文字的颜色
                            },
                            formatter:'{b}:\n{d}%',
                        
                        }
                    }
                    }
                ]
            };
            myCharts.setOption(options);
        }
    },
    mounted(){
        this.huanbi( )
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

.link
    width px2vw(380) 
    height px2vh(300) 
    margin-top  px2vh(20) 
    margin-left px2vw(20) 

.cate-price
    width px2vw(380) 
    height px2vh(50) 
    background url(../static/img/right.png)
    background-size 100% 100%
    line-height px2vh(50)
    font-size 16px
    font-family MicrosoftYaHei-Bold
    font-weight bold
    color rgba(255,255,255,1) 

.huanbi
    width px2vw(380) 
    height px2vh(240)
    background url(../static/img/price.png)
    background-size 100% 100%
    box-sizing border-box   
    margin-top px2vh(10) 
#mains
    height px2vh(240)
    padding-top px2vh(23)
    padding-left px2vw(30)
    div 
        height 100%
</style>