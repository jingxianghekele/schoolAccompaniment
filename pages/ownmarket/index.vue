<template>
	<view class="app">
		<view class="nav">
			<view v-for="(item,index) in array" :key="index" @click="change(index)" :class="{active:index==isShow}" class="nav_round">
				<text>{{item}}</text>
				<view class="huakuai"></view>
			</view>
		</view><!--nav导航-->
		<view class="bottom">
			<view class="bottom_inner">
				<view class="shop" v-show="isShow===0">
					<view v-for="(item,index5) in shop" :key="index5" class="shop_round" @click="to(item.a)">
						<view class="round_box">
							<view class="img_box">
								<image :src="item.src" class="shop_img" mode="widthFix"></image>
							</view>
							<view class="shop_name">{{item.name}}</view>
							<view class="shop_bottom">
								<view class="shop_price">{{item.price}}</view>
								<view class="shop_buy">{{item.buy}}</view>
							</view>
						</view><!--round_box循环里的盒子-->
					</view><!--shop-round商品循环-->
				</view><!--shop商品陈列-->
			</view><!--bottom_inner底部内容-->
		</view><!--bottom底部商品-->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				isShow: 0,
				array: ["全部", "日用品", "洗漱用品", "文具", "体育器材"],
				"shop":[
					{'src':'/static/img/shop1.png','name':'电动牙刷充电式学生党女生男全自动牙刷','price':'￥119.0','buy':'立即购买','a':'/pages/ownmarket/details'},
					{'src':'/static/img/shop2.png','name':'纯棉毛巾家用男女洗澡洗脸实惠','price':'￥19.00','buy':'立即购买'},
					{'src':'/static/img/shop3.png','name':'正品纳爱斯牙膏鲜浓果味120g防蛀护龈','price':'￥19.00','buy':'立即购买'},
					{'src':'/static/img/shop4.png','name':'福百年本色竹浆卫生纸卷纸批发','price':'￥119.0','buy':'立即购买'}
				]
			}
		},
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url:'../index/search'
			})
		},
		onNavigationBarButtonTap(){
			uni.navigateTo({
				url:'./gouwuche'
			})
		},
		methods:{
			change(index) {
				if (this.isShow != index) {
					this.isShow = index;
				}
			},
			to(a){
				uni.navigateTo({
					url:a
				})
			}
		}
	}
</script>

<style lang="scss" >
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
	
	/*底部商品---------------------------------------------*/
	.bottom{
		width:100%;
		border:0rpx solid red;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.bottom_inner{
		width:94%;
	}
	.inner_title{
		margin:30rpx 0;
		color:#FFC300;
		font-size:30rpx;
		border-left:4rpx solid #FFC300;
		padding-left:14rpx
		
	}
	.shop{
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		border:0rpx solid red;
	}
	.shop_round{
		width:336rpx;
		background-color:#FFF;
		margin-bottom:30rpx;
		display: flex;
		flex-direction: column;
		align-items: center;border-radius: 20rpx;;
		border:0rpx solid black
		
	}
	.round_box{
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.img_box{
		width:100%;
		height:300rpx;
		border:0rpx solid pink;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.shop_img{
		width:236rpx;
		height:auto;
		border:0rpx solid green
	}
	.shop_name{
		width:312rpx;
		font-size:26rpx;
		color:#666666;
		margin-top:8rpx;
		border:0rpx solid red
	}
	.shop_price{
		width:110rpx;
		color:#F90A0A;
		font-size:24rpx;
		line-height:40rpx;
		border:0rpx solid red;
		text-align: center;
	}
	.shop_buy{
		line-height:40rpx;
		color:#F90A0A;
		font-size:24rpx;
		border:1rpx solid red;
		border-radius: 20rpx;
		padding:0 22rpx;
		text-align: center;
	}
	.shop_bottom{
		width:310rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin-top:8rpx;
		margin-bottom:24rpx ;
	}
</style>
