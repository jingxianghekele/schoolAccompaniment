<template>
	<view>
		<view class="round" v-for="(item,index) in arr" :key="index" >
			<view class="rou_inner">
				<view class="round1" @click="toPage(item.a)">
						<image class="img" :src="item.src"></view>
						<view class="desc">
							<view class="name">{{item.name}}</view>
							<view class="time">报名时间：<span>{{item.time}}</span></view>
							<view class="number">需参与人数：<span>{{item.number}}人</span></view>
						</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"arr":[
					{'name':'清华大学法律演讲活动','time':'11.12-11.21','number':'140','src':'/static/img/banjia1.png','a':'/pages/index/huodongzhuanqu/details'},
					{'name':'北京大学','time':'11.12-11.21','number':'140','src':'/static/img/banjia3.png','a':'/pages/index/huodongzhuanqu/details'},
					{'name':'上海交通大学','time':'11.12-11.21','number':'140','src':'/static/img/banjia2.png','a':'/pages/index/huodongzhuanqu/details'}
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
	.round{
		width:100%;
		border-bottom:1rpx solid #E1E1E1;
		display:flex;
		flex-direction: column;
		align-items: center;
	}
	.rou_inner{
		width:100%;
		display: flex;
		flex-direction: row;
		margin:32rpx 0  20rpx 0;
		margin-left:12rpx;
		border:0rpx solid red;
		height:190rpx
	}
	.round1{
		display: flex;
		flex-direction: column;
	}
	.desc{
		display: flex;
		flex-direction: column;
		border:0rpx solid red;
		margin-left:20rpx;
		justify-content: space-between;
		margin-bottom:20rpx;
	}
	.name{
		font-size:30rpx;
		color:#212121;
		font-weight:bold;
	}
	.img{
		width:176rpx;
		height:178rpx;
	}
	.number{
		color:#666666;
		font-size:26rpx;
		
	}
	.number span{
		font-size:25rpx;
		color:#FF0000
	}
	.time{
		color:#666666;
		font-size:26rpx;
		
	}
	.time span{
		font-size:25rpx;
		color:#FF0000
	}
</style>
