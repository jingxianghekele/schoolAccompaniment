<template>
	<view class="app">
		<view class="nav">
			<view v-for="(item,index) in array" :key="index" @click="change(index)" :class="{active:index==isShow}" class="nav_round">
				<text>{{item}}</text>
				<view class="huakuai"></view>
			</view>
		</view><!--nav导航-->
		<view class="goodsList" v-show="isShow===0">
			<view class="listRound" v-for="(item,index) in arr" :key="index" @click="toPage(item.a)">
				<view style="height:360rpx;display: flex;flex-direction: column;justify-content: center;align-items: center;">
					<image :src="item.src" class="roundImg" mode="widthFix"></image>
				</view>
				<view class="roundName">{{item.name}}</view>
				<view class="roundBottom">
					<view class="roundPrice">{{item.price}}</view>
					<view class="roundNumber">{{item.number}}</view>
				</view><!--roundBottom价格和件数一个view-->
				
			</view><!--listRound列表循环-->
		</view><!--goodsList商品列表--> 
	</view>
</template>

<script>
	export default{
		data(){
			return{
				isShow: 0,
				array: ["全部", "运动", "手机", "数码", "美妆", "衣物"],
				"arr":[
					{'src':'/static/img/goods1.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'},
					{'src':'/static/img/goods2.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'},
					{'src':'/static/img/goods3.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'},
					{'src':'/static/img/goods4.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'},
					{'src':'/static/img/goods3.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'},
					{'src':'/static/img/goods2.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'},
					{'src':'/static/img/goods1.png','name':'临沂大学城附近体育馆足球篮球租赁','price':'￥2/时','number':'剩余112件','a':'/pages/index/rent/details'}
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
		height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		background: #FAFAFA;
	}
	/*导航-------------------------------*/
	.nav{
		margin:32rpx 0;
		width:100%;
		display: flex;
		flex-direction: row;
		border:0rpx solid red;
		justify-content: space-between;
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
	/*列表----------------------------------*/
	.goodsList{
		margin-top:30rpx;
		width:94%;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: space-between;
	}
	.listRound{
		width:336rpx;
		height:482rpx;
		border:0rpx solid green;
		margin-bottom:30rpx;
		background:#FFF;
		border-radius:20rpx;
	}
	.roundImg{
		width:278rpx ;
		height:auto;
		border:0rpx solid red;
	}
	.roundName{
		font-size:26rpx;
		color:#212121;
		margin-left:10rpx;
		letter-spacing: 60;
		border:0rpx solid red
	}
	.roundBottom{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin:12rpx 6rpx 0 6rpx;
	}
	.roundNumber{
		font-size:24rpx;
		color:#666666;
	}
	.roundPrice{
		font-size:26rpx;
		color:#F90A0A;
	}
</style>
