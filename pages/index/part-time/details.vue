<template>
	<view class="app">
		<view style="box-shadow: inset 0px 15px 8px -15px #ccc;width:100%;height:19rpx;position: fixed;top:0"></view>
		<view class="body">
			<view class="job">
				<view class="job1">
					<view class="job1s">
						<view class="name">{{name}}</view>
						<view class="price">{{price}}</view>
						<view class="time">{{time}}</view>
					</view>
				</view>
				<view class="job2">
					<view class="job2s">
						<view class="work"><span>职位：</span>{{work}}</view>
						<view class="number"><span>人数：</span>{{number}}</view>
						<view class="area"><span>地区：</span>{{area}}</view>
					</view>
				</view>
			</view><!--job兼职名称、地点、工资……-->
			<view style="width:100%;height:20rpx;background-color:#FAFAFA"></view><!--中间灰色空白-->
			<view class="desc">
				<view class="descs">
					<view class="title">{{desc}}</view>
				</view><!--title信息描述-->
				<view class="text">
					<view class="txt">
						<view>{{zhiweimiaoshu}}</view>
						<view>{{one}}</view>
						<view>{{two}}</view>
						<view>{{three}}</view>
						<view>{{four}}</view>
						<view>{{five}}</view>
						<view>{{six}}</view>
					</view><!--txt大段文字-->
				</view><!--text描述的内容-->
				<view></view>
			</view><!--desc兼职信息描述-->
		</view><!--body-->
		<view class="call">
			<view class="calls">
				<view class="but">
					<img src="/static/img/commodity_phone.png" >拨打电话
				</view>
			</view>
		</view><!--call致电-->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"name":'崂山中韩送餐员兼职日结',
				"price":'150/天',
				"time":'发布：2019-10-24',
				"work":'生活配送员',
				"number":'80人',
				"area":'青岛',
				"desc":'信息描述',
				"zhiweimiaoshu":'职位描述： 岗位职责：',
				"one":' 1、在董事长的领导下，全面负责公司各项工作；',
				"two":' 2、协助决策层制定公司发展战略，负责其功能领域内中长期决策和目标制定； 3、制定企业发展规划和经营计划，负责协调部署各职能部门落实执行与经营目标达成；',
				"three":'4、全面组织生产经营管理；建立健全公司各项管理制度和流程，并组织贯彻执行，提升公司运营效率与管理水平，维护公司正常的工作秩序；',
				"four":' 5、负责公司运营体系及架构的建设、落实及实施，监督并检查推行情况； 6、分解落实公司各项考核指标，并组织完成；',
				"five":'7、及时掌握公司运营情况，并进行系统分析，定期向董事长汇报管理情况； 8、维护与开拓合作伙伴及相关企业间的积极交流与良好合作；',
				"six":' 9、管理培养部门员工，打造团结、高效、执行力强、敬业的团队；10、完成董事长交办的其他工作 '
			}
		},
		methods:{
			
		}
	}
</script>

<style>
	.app{
		width:750rpx;height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative;
		border:0rpx solid red;
		position: absolute;
	}
	.body{
		width:100%;
		border:0rpx solid red;
	}
	/*兼职主要信息--------------------------------*/
	.job{
		width:100%;
		border:0rpx solid red;
	}
	.job1{
		border-bottom:1rpx solid #E1E1E1
	}
	.job1,.job2{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		
	}
	.job1s,.job2s{
		width:94%;
		height:136rpx;
		border:0rpx solid green;
		display:flex;
		flex-direction: column;
		justify-content: space-between;
		margin:14rpx 0
	}
	.name{
		font-size:36rpx;
		color:#212121;
	}
	.price{
		font-size:30rpx;
		color:#F90A0A;
	}
	.time{
		font-size:24rpx;
		color:#666666;
	}
	.work{
		font-size:26rpx;
		color:#212121;
	}
	.number{
		font-size:26rpx;
		color:#212121;
	}
	.area{
		font-size:26rpx;
		color:#212121;
	}
	.work span ,.number span,.area span{
		color:#666666
	}
	/*信息描述的部分----------------------------------------*/
	.desc{
		width:100%;
		display: flex;
		flex-direction: column;
	}
	.descs{
		width:100%;
		height:66rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		border:0rpx solid red;
		border-bottom:1rpx solid #E1E1E1
	}
	.title{
		width:94%;
		font-size:28rpx;
		color:#212121;
		margin-left:24rpx;
		font-weight:bold
	}
	.text{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.txt{
		margin-top:8rpx;
		width:94%;
		font-size:28rpx;
		color:#212121;
		line-height:40rpx
	}
	/*拨打电话----------------------------------------------*/
	.call{
		position: fixed;
		left:0;
		bottom:0rpx;
		width:100%;
		box-shadow:0px 1rpx 8px -4px #ccc;
		border:0rpx solid red;
		height:98rpx;
	}
	.calls{
		width:100%;
		height:100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.but{
		width:94%;
		height:80rpx;
		background:rgba(255,195,0,1);
		opacity:1;
		border-radius:44rpx;
		display: flex;
		flex-direction: row;
		align-items:center ;
		justify-content: center;
		font-size:30rpx;
		color:#212121;
		font-weight:bold
	}
	.but img{
		width:40rpx;
		height:40rpx;
		border:0rpx solid green;
		margin-right:40rpx;
	}
</style>
