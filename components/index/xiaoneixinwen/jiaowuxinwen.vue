<template>
	<view>
		<view class="sch1">
			<view class="sch1Name">{{sch1Name}}</view>
			<view class="sch1_img">
				<view v-for="(item,index3) in arrList" :key="index3">
					<image :src="item.src" class="img_img"></image>
				</view>
			</view><!--sch1_img第一篇资讯的图片-->
		</view><!--sch1第一篇学校资讯-->
		<view class="sch2">
			<view class="sch2Name">{{sch2Name}}</view>
			<view class="sch2Text">{{sch2Text}}</view>
		</view><!--sch2校内资讯第二篇-->
		<view class="sch345">
			<view v-for="(item,index4) in arrAy" :key="index4" class="sch345_round" @click="toPage(item.a)">
				<view >
					<view class="sch345_name">{{item.sch345Name}}</view>
					<view class="sch345_text">{{item.sch345Text}}</view>
				</view>
				<view>
					<image :src="item.src" class="sch345_img"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				sch1Name:'大学里存在的“阴暗交易”,触目惊心,本该单纯的……',
				sch2Name:'十年大赛促百余个大学生创业项目落地事先产值超亿元',
				sch2Text:'为贯彻落实国家、省、市创新创业部署、有效推进……',
				"arrList":[
					{'src':'/static/img/sch1-1.png'},
					{'src':'/static/img/sch1-2.png'},
					{'src':'/static/img/sch1-1.png'}
				],
				"arrAy":[
					{
						'sch345Name':'长安大学举行“创青春”大学生创业系列培训会',
						'sch345Text':'大学生与创业之间一直备受争议的,支持与反对的……',
						'src':'/static/img/sch3.png',
						'a':'/pages/index/news'
					},
					{
						'sch345Name':'刚毕业的大学生想创业但是没有启动资金怎么办？',
						'sch345Text':'近几年大学生就业压力越来越大,有部分毕业两年内……',
						'src':'/static/img/sch4.png',
						'a':'/pages/index/news'
					},
					{
						'sch345Name':'大学生创业新趋势：六成学生想创业,需要关注的七种经验',
						'sch345Text':'人人想要实现创业梦，为实现创业梦我',
						'src':'/static/img/sch5.png',
						'a':'/pages/index/news'
					}
				]
			}
		},
		methods:{
			toPage(a){
				uni.navigateTo({
					url:a
				})
			}
		}
	}
</script>

<style>
	/*校内资讯第一篇*/
	.sch1{
		width:100%;
		padding:40rpx 0 ;
		border-bottom:1rpx solid #E1E1E1
	}
	.sch1Name{
		font-weight:bold;
		width:100%;
		font-size:28rpx;
		color:#212121;
		margin-bottom:8rpx;
	}
	.sch1_img{
		width:100%;
		display:flex ;
		flex-direction: row;
		border:0rpx solid #3F536E;
		justify-content: space-between;
		border:0rpx solid #008000
	}
	.img_img{
		width:220rpx;
		height:140rpx;
		border:0rpx solid red
	}
	/*校内资讯第二篇*/
	.sch2{
		width:100%;
		display: flex;
		flex-direction: column;
		padding:40rpx 0 ;
		border-bottom:1rpx solid #E1E1E1
	}
	.sch2Name{
		font-weight:bold;
		width:100%;
		font-size:28rpx;
		color:#212121;
		margin-bottom:8rpx
	}
	.sch2Text{
		width:100%;
		font-size:24rpx;
		color:#A5A5A5
	}
	/*第三四五篇文章*/
	.sch345{
		border:0rpx solid red;
		width:100%
	}
	.sch345_round{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border:0rpx solid blue;
		padding:40rpx 0;
		border-bottom:1rpx solid #E1E1E1
	}
	.sch345_name{
		font-weight:bold;
		font-size:28rpx;
		color:#212121;
		margin-bottom:8rpx;
		width:432rpx;
	}
	.sch345_text{
		font-size:24rpx;
		color:#A5A5A5;
		width:432rpx;
	}
	.sch345_img{
		width:220rpx;
		height:140rpx;
	}
</style>
