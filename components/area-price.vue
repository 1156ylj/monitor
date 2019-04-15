
<template>
    <div class="area">
        <div class="dizhou">各地州市价格情况</div>
        <div class="adxbox">
            <el-table
                :data="tableData"
                style="width: 100%">
                    <el-table-column
                    prop="name"
                    label="地区"
                    width="100">
                </el-table-column>
                <el-table-column
                    prop="date"
                    label="2018.01"
                    width="100">
                </el-table-column>
                <!-- <el-table-column
                    prop="name"
                    label="姓名"
                    width="180">
                </el-table-column> -->
                <el-table-column
                    prop="date"
                    label="2018.02"
                    width="100">
                </el-table-column>
                <el-table-column
                    prop="date"
                    label="2018.03"
                    width="100">
                </el-table-column>
                    <el-table-column
                    prop="date"
                    label="2018.04"
                    width="100">
                </el-table-column>
                    <el-table-column
                    prop="date"
                    label="2018.05"
                    width="100">
                </el-table-column>
                    <el-table-column
                    prop="date"
                    label="2018.06"
                    width="100">
                </el-table-column>
                    <el-table-column
                    prop="date"
                    label="2018.07"
                    width="100">
                </el-table-column>
                    <el-table-column
                    prop="date"
                    label="2018.08"
                    width="100">
                </el-table-column>
                    <el-table-column
                    prop="date"
                    label="2018.09"
                    width="100">
                </el-table-column>
            </el-table>
        </div>
    </div>
</template>
<script>
// 地区价格组件
import $ from 'jquery'
export default {
   data() {
        return {
            tableData: [],
            area:[{"id":"530100000000","name":"昆明市","level":"2","pid":"53","geocode":"102.832891,24.880095"},{"id":"530300000000","name":"曲靖市","level":"2","pid":"53","geocode":"103.796167,25.489999"},{"id":"530400000000","name":"玉溪市","level":"2","pid":"53","geocode":"102.546543,24.352036"},{"id":"530500000000","name":"保山市","level":"2","pid":"53","geocode":"99.161761,25.112046"},{"id":"530600000000","name":"昭通市","level":"2","pid":"53","geocode":"103.717465,27.338257"},{"id":"530700000000","name":"丽江市","level":"2","pid":"53","geocode":"100.227750,26.855047"},{"id":"530800000000","name":"普洱市","level":"2","pid":"53","geocode":"100.966512,22.825065"},{"id":"530900000000","name":"临沧市","level":"2","pid":"53","geocode":"100.079583,23.877573"},{"id":"532300000000","name":"楚雄州","level":"2","pid":"53","geocode":"101.528068,25.045532"},{"id":"532500000000","name":"红河州","level":"2","pid":"53","geocode":"103.374799,23.363130"},{"id":"532600000000","name":"文山州","level":"2","pid":"53","geocode":"104.216248,23.400733"},{"id":"532800000000","name":"西双版纳州","level":"2","pid":"53","geocode":"100.797777,22.007351"},{"id":"532900000000","name":"大理州","level":"2","pid":"53","geocode":"100.267638,25.606486"},{"id":"533100000000","name":"德宏州","level":"2","pid":"53","geocode":"98.584895,24.433353"},{"id":"533300000000","name":"怒江州","level":"2","pid":"53","geocode":"98.853097,25.852547"},{"id":"533400000000","name":"迪庆州","level":"2","pid":"53","geocode":"99.702234,27.818882"}],

        }
      },
      created() {
          this.area.forEach(item => {
              item.date = 2018.01
          })
          this.tableData = this.area
      },
      methods:{
          scrollAuto() { //滚动		
            let h = -1;
            this.timer = setInterval(function() {
                        //获取当前滚动条高度  
                        const current = $('.adxbox')[0].scrollTop;
                        if (current === h) {
                            //滚动到底端，刷新屏幕，并返回顶端   
                            clearInterval(this.timer);

                        } else {
                            //以25ms/3.5px的速度滚动   
                            h = current;
                            $('.adxbox')[0].scrollTop = h + 3.5;
                        }
                    }, 250)
        }
      },
      mounted() {
            let that = this
            setTimeout(() => {
				that.scrollAuto()
            }, 3000)
  }
}

    
</script>
<style lang="stylus" scoped>
px2vw(px) 
    px/1920*100 vw 

px2vh(px)
    px/1080*100 vh
.area
    height px2vh(240)
    padding px2vh(20) px2vw(20) 0
.dizhou
    height px2vh(50)
    background url(../static/img/xia.png)
    background-size 100% 100%
    font-size 16px
    font-family MicrosoftYaHei-Bold
    font-weight bold
    color rgba(255,255,255,1)
    line-height px2vh(50) 
.adxbox
    width px2vw(1080)
    height px2vh(180)
    background url(../static/img/adss.png)
    background-size 100% 100%
    margin-top px2vh(10)
    padding-top px2vh(20)
    // overflow auto
    overflow-y scroll
    padding-bottom px2vh(5)
    box-sizing border-box
    overflow-x hidden
    padding-left px2vh(30)   
    
.ads-data
    width px2vw(1080) 
    display  flex
    justify-content space-around
    font-size 14px
    font-family MicrosoftYaHei
    font-weight 400
    color rgba(255,255,255,1)
    padding-bottom px2vh(10)
.data_date
    margin-right px2vw(42)
    margin-left  px2vw(11)

tr
    translate .5s
// .el-table
//     background  none
//     color #fff
</style>