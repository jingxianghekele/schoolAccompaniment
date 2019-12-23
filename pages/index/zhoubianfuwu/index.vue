<template>
	<view class="app">
		<view class="nav">
			<view v-for="(item,index) in array" :key="index" @click="change(index)" :class="{active:index==isShow}" class="nav_round">
				<text>{{item}}</text>
				<view class="huakuai"></view>
			</view>
		</view><!--nav导航-->
		<view class="text">
			<view class="text_round" v-for="(item,index) in arr" :key="index" @click="toPage(item.a)" v-show="isShow===0">
				<image :src="item.src" class="img"></image>
				<view class="title">{{item.title}}</view>
				<view class="txt">{{item.txt}}</view>
			</view>
		</view><!--txt文章列表-->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				isShow: 0,
				array: ["餐饮", "住宿", "娱乐", "培训", "优惠", "快递"],
				"arr":[
					{'src':'/static/img/youhui1.png','title':'醉鹃城火锅店优惠啦，99元抢限量套餐','txt':'【华阳/航空巷2店通用】13荤13素,惊艳全城,五星好评，99元=4人抢原价277元醉鹃城市井火锅超值套餐!牛油火锅底+农夫山泉,好吃不上火！市井老火锅,味道醉倾城!','a':'/pages/index/zhoubianfuwu/details'},
					{'src':'/static/img/youhui2.png','title':'香格里拉理发店限时抢288元套餐啦！','txt':'【香格里拉】开在五星级酒店里的高端理发会所！288元抢原价860元张艺兴同款烫发！洗剪吹+一次护理，美发整容，时尚减龄！','a':'/pages/index/zhoubianfuwu/details'},
					{'src':'/static/img/youhui1.png','title':'香格里拉理发店限时抢288元套餐啦！','txt':'【香格里拉】开在五星级酒店里的高端理发会所！288元抢原价860元张艺兴同款烫发！洗剪吹+一次护理，美发整容，时尚减龄！','a':'/pages/index/zhoubianfuwu/details'},
					{'src':'/static/img/youhui2.png','title':'香格里拉理发店限时抢288元套餐啦！','txt':'【香格里拉】开在五星级酒店里的高端理发会所！288元抢原价860元张艺兴同款烫发！洗剪吹+一次护理，美发整容，时尚减龄！','a':'/pages/index/zhoubianfuwu/details'}
				]
			}
		},
		methods:{
			toPage(a){
				uni.navigateTo({
					url:a
				})
			},
			change(index) {
				if (this.isShow != index) {
					this.isShow = index;
				}
			}
		}
	}
</script>

<style lang="scss">
	.app{
		width:750rpx;
		height:100%;
		background:#FAFAFA;
		border:1rpx solid #FAFAFA;
	}
	/*导航--------------------------------*/
	.nav{
		margin:32rpx 0;
		width:100%;
		display: flex;
		flex-direction: row;
		border:0rpx solid red;
		justify-content: space-between;
		background:#FAFAFA;
	}
	.nav_round{
		line-height:44rpx;
		margin:0 24rpx;
		font-size:26rpx;
		color:#212121;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.huakuai{
		width:50rpx;
		height:6rpx;
	}
	.active{
		font-weight:bold;
		font-size:32rpx;
		.huakuai{
			background:#FFC300;
			border-radius: 20rpx;
		}
	}
	/*文章列表----------------------------------*/
	.text{
		width:100%;
		border:0rpx solid red;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin-top:20rpx;
		
	}
	.text_round{
		width:94%;
		height:520rpx;
		border:0rpx solid red;
		margin-bottom:20rpx;
		border-radius:20rpx;
		background: #fff;
	}
	.img{
		width:100%;
		height:304rpx;
		border-radius:20rpx;
	}
	.title{
		font-size:32rpx;
		color:#212121;
		font-weight:bold;
		margin:20rpx 0 22rpx 32rpx;
	}
	.txt{
		font-size:26rpx;
		color:#212121;
		margin:0 22rpx 0 28rpx;
		height:102rpx;
		border:0rpx solid green
	}
</style>
