
<template>
    <div class="cate-list">
        <div class="cailiao">材料名称</div>
        <div class="leiming">
          <el-tree default-expand-all  :data="cate" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
        </div>
    </div>
</template>
<script>
// 材料名称组件
export default {
  data() {
    return {
        cate: [{
						id: "1",
						name: "钢材",
						pid: "0",
						sort: "1",
						children: [{
								id: "11",
								name: "钢筋",
								pid: "1",
								sort: "1"
							},
							{
								id: "12",
								name: "钢板",
								pid: "1",
								sort: "2"
							},
							{
								id: "13",
								name: "钢管",
								pid: "1",
								sort: "3"
							},
							{
								id: "14",
								name: "型钢",
								pid: "1",
								sort: "3"
							},
							{
								id: "15",
								name: "钢绞线",
								pid: "1",
								sort: "3"
							},
							{
								id: "16",
								name: "钢丝绳",
								pid: "1",
								sort: "3"
							},
						]
					},
					{
						id: "3",
						name: "地区材料",
						pid: "0",
						sort: "2",
						children: [{
								id: "31",
								name: "钢筋水泥",
								pid: "3",
								sort: "1"
							},
							{
								id: "32",
								name: "砌体材料",
								pid: "3",
								sort: "2"
							},
							{
								id: "33",
								name: "建筑用砂",
								pid: "3",
								sort: "3"
							},
								{
								id: "34",
								name: "建筑用石",
								pid: "3",
								sort: "3"
							},
								{
								id: "35",
								name: "轻骨料",
								pid: "3",
								sort: "3"
							},
								{
								id: "36",
								name: "地基用材",
								pid: "3",
								sort: "3"
							},
								{
								id: "37",
								name: "混凝土",
								pid: "3",
								sort: "3"
							},
								{
								id: "38",
								name: "建筑砂浆",
								pid: "3",
								sort: "3"
							},
						]
					},
					{
						id: "4",
						name: "电线电缆及光纤光缆",
						pid: "0",
						sort: "3",
						children: [{
								id: "41",
								name: "电力电缆",
								pid: "4",
								sort: "1"
							},
							{
								id: "42",
								name: "电气装备用电",
								pid: "4",
								sort: "2"
							},
							{
								id: "43",
								name: "其他电气材料",
								pid: "4",
								sort: "3"
							},
						]
					},
					{
						id: "5",
						name: "管材",
						pid: "0",
						sort: "4",
						children: [{
								id: "51",
								name: "非金属管",
								pid: "5",
								sort: "1"
							},
							{
								id: "52",
								name: "复合管",
								pid: "5",
								sort: "2"
							},
							{
								id: "53",
								name: "金属管",
								pid: "5",
								sort: "3"
							},
						]
					},
					{
						id: "6",
						name: "防水材料",
						pid: "0",
						sort: "5",
						children: [{
								id: "61",
								name: "防水卷材",
								pid: "6",
								sort: "1"
							},
							{
								id: "62",
								name: "防水涂料",
								pid: "6",
								sort: "2"
							},
							{
								id: "63",
								name: "防水砂浆",
								pid: "6",
								sort: "3"
							},
						]
					},
					{
						id: "7",
						name: "建筑玻璃",
						pid: "0",
						sort: "6",
						children: [{
								id: "71",
								name: "特种琉璃",
								pid: "7",
								sort: "1"
						},
						]
					},
					{
						id: "31",
						name: "混凝土预制件",
						pid: "0",
						sort: "7",
						children: [{
								id: "81",
								name: "混凝土管",
								pid: "31",
								sort: "1"
							},
							{
								id: "82",
								name: "混凝土预制桩",
								pid: "31",
								sort: "2"
							},
						]
					}
        ],
        defaultProps:{
          children: 'children',
          label: 'name'
        }
    }
  },
   name:"cate-list",
    	
    methods: {
      handleNodeClick(data) {
        console.log(data);
      }
    } 
}
</script>
<style lang="stylus" scoped>
px2vw(px) 
    px/1920*100 vw 

px2vh(px)
    px/1080*100 vh

.cate-list
    width px2vw(380) 
    height px2vh(300) 
    margin-top  px2vh(20) 
    margin-left px2vw(20) 
.cailiao
    width px2vw(380) 
    height px2vh(50) 
    background url(../static/img/right.png)
    background-size 100% 100%
    line-height px2vh(50)
    font-size 16px
    font-family MicrosoftYaHei-Bold
    font-weight bold
    color rgba(255,255,255,1)

.leiming
    width px2vw(380) 
    height px2vh(240)
    background url(../static/img/cailiao.png)
    background-size 100% 100%
    margin-top px2vh(10) 
    overflow hidden
    padding-top px2vh(30) 
    box-sizing border-box
    overflow  auto
.el-tree
    background  none
    color #fff
</style>