<template>
	<view>
		<view v-for="(item,index) in arr" :key="index" class="listRound" @click="toPage(item.a)">
			<view ><image :src="item.src" class="img"></image></view>
			<view class="text">
				<view class="name">{{item.name}}</view>
				<view class="number">人数：{{item.number}}人</view>
				<view class="area">
					<image :src="img"></image>
					{{item.area}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				img:'/static/img/commodity_address@2x.png',
				arr:[
					{'src':'/static/img/banjia1.png','name':'租房','number':'10','area':'北京大学商学圈','a':'../../../pages/index/biyezhiyin/zufang_details'},
					{'src':'/static/img/banjia2.png','name':'租房','number':'10','area':'北京大学商学圈','a':'../../../pages/index/biyezhiyin/zufang_details'},
					{'src':'/static/img/banjia3.png','name':'租房','number':'10','area':'北京大学商学圈','a':'../../../pages/index/biyezhiyin/zufang_details'},
					{'src':'/static/img/banjia4.png','name':'租房','number':'10','area':'北京大学商学圈','a':'../../../pages/index/biyezhiyin/zufang_details'},
					{'src':'/static/img/banjia5.png','name':'租房','number':'10','area':'北京大学商学圈','a':'../../../pages/index/biyezhiyin/zufang_details'}
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
	
	.listRound{
		display:flex;
		flex-direction: row;
		border-bottom:1rpx solid #E1E1E1;
		padding:32rpx 0 34rpx 0;
	}
	.img{
		margin-left:12rpx;
		width:176rpx;
		height:178rpx;
		margin-right:20rpx;
	}
	.text{
		margin-top:6rpx;
		display: flex;
		flex-direction: column;
	}
	.name{
		font-size:30rpx;
		color:#212121;
		margin-bottom: 28rpx;
		font-weight:bold;
	}
	.number{
		font-size:26rpx;
		color: #B8B4B4;
		margin-bottom:28rpx
	}
	.area{
		font-size:26rpx;
		color: #666;
		border:0rpx solid red;
		display: flex;
		flex-direction: row;
		justify-content: center;
	}
	.area image{
		width:28rpx;
		height:32rpx;
		margin-right:10rpx;
	}
</style>
