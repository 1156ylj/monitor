<template>
    <div class="page-index">    	 
       <div class='header'>
       <div class="wen">
           <div class="tuwen">
                 <img src="../static/img/loginlogo.png" class="logo"/>
                 <span>云南省建筑工程材料及设备价格监测系统</span> 
           </div>
            <p>2018-04-08 10:08</P>
       </div>
    
       </div>
       <div class='content'>
           <div class='left'>
               <cate></cate>
               <price></price>
               <huanbi></huanbi>
           </div>
           <div class='center'>
               <maps></maps>
                <areas> </areas>
           </div>
           <div class='right'>
               <exponent></exponent>
               <redar></redar>
           </div>
       </div>
    </div>
</template>

<script>
import redar from '../components/redar'
import cate from '../components/cate-list'
import price from '../components/price'
import huanbi from '../components/cate-price'
import exponent from '../components/cate-price-zs'
import maps from '../components/map'
import areas from '../components/area-price'


function setState(store) {}

export default {
    name: 'index',
    metaInfo: {
        title: 'Home',
        titleTemplate: '%s - Lavas',
        meta: [
            {name: 'keywords', content: 'lavas PWA'},
            {name: 'description', content: '基于 Vue 的 PWA 解决方案，帮助开发者快速搭建 PWA 应用，解决接入 PWA 的各种问题'}
        ]
    },

    components:{
        redar,
        cate,
        price,
        huanbi,
        exponent,
        maps,
        areas
    }
};
</script>

<style lang="stylus" scoped>
px2vw(px) 
    px/1920*100 vw 

px2vh(px)
    px/1080*100 vh

.content
    display flex
    //padding 0 20px
.left
    height px2vh(50)
.header
    width px2vw(1920)
    height px2vh(80)
    padding-top  px2vh(20)
    display  flex
    justify-content center
    background url(../static/img/top.png) 
    background-size 100% 100%
.tuwen img
    width px2vw(32)
    margin-right px2vw(8)
.tuwen span 
    font-size 22px
    font-family MicrosoftYaHei-Bold
    font-weight bold
    color rgba(255,255,255,1)
    display block
    margin-left px2vm(8)
.wen p{
    margin-top px2vh(10)
    font-size 14px
    font-family MicrosoftYaHei
    font-weight 400
    color rgba(0,222,255,1)
}
.tuwen 
    display flex
    align-items center
.page-index,.right
    margin-right px2vw(20)
</style>
