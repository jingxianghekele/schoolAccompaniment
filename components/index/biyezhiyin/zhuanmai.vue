<template>
	<view>
		<view v-for="(item,index) in arr" :key="index" class="listRound" @click="jump(item.a)">
			<view><image :src="item.src" class="img"></image></view>
			<view class="text">
				<view class="name">{{item.name}}</view>
				<view class="price">￥{{item.price}}</view>
				<view class="user">
					发布人：{{item.user}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				arr:[
					{'src':'/static/img/resell2.png','name':'360 N4 9成新手机','price':'299','user':'大雄','a':'/pages/index/biyezhiyin/zhuanmai_details'},
					{'src':'/static/img/resell2.png','name':'360 N4 9成新手机','price':'199','user':'静香','a':'/pages/index/biyezhiyin/zhuanmai_details'},
					{'src':'/static/img/resell2.png','name':'360 N4 9成新手机','price':'199','user':'胖虎','a':'/pages/index/biyezhiyin/zhuanmai_details'},
					{'src':'/static/img/resell2.png','name':'360 N4 9成新手机','price':'199','user':'小夫','a':'/pages/index/biyezhiyin/zhuanmai_details'}
				]
			}
		},
		methods:{
			jump(a){
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
		border-radius: 20rpx;
	}
	.text{
		margin-top:6rpx;
		display: flex;
		flex-direction: column;
	}
	.name{
		font-size:26rpx;
		color:#212121;
		margin-bottom: 14rpx;
		line-height: 36rpx;
	}
	.price{
		font-size:26rpx;
		color:#F90A0A;
		margin-bottom:16rpx;
		font-weight:bold;
		line-height: 42rpx;
	}
	.user{
		font-size:24rpx;
		color: #212121;
		border:0rpx solid red;
		line-height: 34rpx;
	}
</style>
