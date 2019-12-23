<template>
	<view>
		<view v-for="(item,index) in arr" :key="index" class="listRound">
			<view ><image :src="item.src" class="img"></image></view>
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
					{'src':'/static/img/qiugou1.png','name':'碎花灯笼袖过膝长春秋上衣 外搭色T桖衫','price':'199','user':'哆啦A梦'},
					{'src':'/static/img/qiugou2.png','name':'碎花灯笼袖过膝长春秋上衣 外搭色T桖衫','price':'199','user':'哆啦A梦'},
					{'src':'/static/img/qiugou1.png','name':'碎花灯笼袖过膝长春秋上衣 外搭色T桖衫','price':'199','user':'哆啦A梦'},
					{'src':'/static/img/qiugou2.png','name':'碎花灯笼袖过膝长春秋上衣 外搭色T桖衫','price':'199','user':'哆啦A梦'}
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
