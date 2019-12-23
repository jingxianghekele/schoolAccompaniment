<template>
	<view>
		<view v-for="(item,index) in arr" :key="index" class="listRound">
			<view ><image :src="item.src" class="img"></image></view>
			<view class="text">
				<view class="name">{{item.name}}</view>
				<view class="desc">{{item.desc}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"arr":[
					{'src':'/static/img/banjia1.png','name':'论文指导','desc':'盘子女人坊毕业季搞活动啦！ 只要到店拍毕业照优惠到底...'},
					{'src':'/static/img/banjia2.png','name':'论文指导','desc':'伯爵旅拍毕业季搞活动啦！ 只要到店拍毕业照优惠到底...'}
				]
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
		margin-bottom: 50rpx;
		font-weight:bold;
	}
	.desc{
		font-size:26rpx;
		color: #B8B4B4;
	}
</style>
