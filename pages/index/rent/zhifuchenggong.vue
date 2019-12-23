<template>
	<view class="app">
		<view class="icon">
			<image :src="icon" class="img"></image>
			<view class="success">{{success}}</view>
		</view><!--支付成功图标-->
		<view class="details">
			<view class="title">{{title}}</view>
			<view class="order">
				<view class="number">订单编号：<span>{{number}}</span></view>
				<view class="price">支付金额：<span>{{price}}</span></view>
				<view class="how">支付方式：<span>{{how}}</span></view>
			</view><!--订单-->
			<view class="people">
				<view class="name">收货人姓名：<span>{{name}}</span></view>
				<view class="tel">收货人手机：<span>{{tel}}</span></view>
			</view><!--收货人-->
		</view><!--订单详细信息部分-->
		<view class="but">
			<button class="but1">查看详情</button>
			<button class="but2">返回首页</button>
		</view><!--按钮部分-->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"icon":'/static/img/sucessful@2x.png',
				"success":'订单支付成功',
				"title":'订单信息',
				"number":'2019110812345678',
				"price":'2.00元',
				"how":'微信支付',
				"name":'某某某',
				"tel":'15244309876'
			}
		},
		onNavigationBarButtonTap() {
			uni.showToast({
				title:'确定取消本次租赁吗？'
			})
		},
		methods:{
			
		}
	}
</script>

<style>
	.app{
		width:750rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	/*支付成功icon--------------------*/
	.icon{
		width:100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		border:0rpx solid red;
	}
	.img{
		width:200rpx;
		height:200rpx;
		margin:80rpx 0 48rpx 0
	}
	.success{
		font-size:48rpx;
		font-weight:bold;
		margin-bottom:72rpx;
	}
	/*订单详细信息-----------------------------*/
	.details{
		width:94%;
		
	}
	.title{
		font-size:36rpx;
		color:#666666;
		font-weight:bold;
		padding-bottom:20rpx;
		border-bottom:1rpx solid #E1E1E1;
	}
	.order{
		border-bottom:1rpx solid #E1E1E1;
		padding:20rpx 0;
	}
	.number,.price,.how{
		color:#B8B4B4;
		font-size:32rpx;
	}
	.number,.price{
		margin-bottom:20rpx
	}
	.number span,.how span{
		font-size:32rpx;
		color:#212121
	}
	.price span{
		font-size:32rpx;
		font-weight:400;
		color:rgba(249,10,10,1);
	}
	/*收货人信息----------------------*/
	.name,.tel{
		color:#B8B4B4;
		font-size:32rpx;
		margin-top:20rpx;
	}
	.name span,.tel span{
		font-size:32rpx;
		color:#212121
	}
	/*底部按钮---------------------*/
	.but{
		border:0rpx solid red;
		margin-top:58rpx;
	}
	.but1{
		width:648rpx;
		height:80rpx;
		font-size:28rpx;
		background:rgba(255,195,0,1);
		opacity:1;
		border-radius:40rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin-bottom:40rpx;
	}
	.but2{
		width:648rpx;
		height:80rpx;
		font-size:28rpx;
		border:2px solid rgba(255,195,0,1);
		opacity:1;
		border-radius:40rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		background: #ffffff;
	}
</style>
