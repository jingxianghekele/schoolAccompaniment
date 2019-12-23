<template>
	<view>
		<view class="round" v-for="(item,index) in arr" :key="index" >
			<view class="rou_inner">
				<view class="round1" @click="toPage(item.a)">
						<image class="img" :src="item.src"></view>
						<view class="school">
							<view class="name">{{item.name}}</view>
							<view class="desc">{{item.desc}}</view>
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
					{'name':'清华大学','desc':'清华大学是我国985 211重点 大学...','src':'/static/img/kaoyan1.png','a':'/pages/index/xinshengzhiyin/details'},
					{'name':'北京大学','desc':'北京大学是我国985 211重点 大学...','src':'/static/img/kaoyan3.png','a':'/pages/index/xinshengzhiyin/details'},
					{'name':'上海交通大学','desc':'上海交通大学是我国985 211重点 大学...','src':'/static/img/kaoyan2.png','a':'/pages/index/xinshengzhiyin/details'}
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
		width:95%;
		border-bottom:1rpx solid #E1E1E1;
		display:flex;
		flex-direction: column;
		align-items: center;
	}
	.rou_inner{
		width:98%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin:32rpx 0  20rpx 0;
		margin-left:12rpx;
		border:0rpx solid red;
		height:190rpx
	}
	.round1{
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.round2{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}
	.school{
		display: flex;
		flex-direction: column;
		border:0rpx solid red;
		margin-left:20rpx;
		margin-bottom:37rpx;
		justify-content: space-between
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
	.desc{
		color:#B8B4B4;
		font-size:26rpx;
	}
</style>
