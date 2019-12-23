<template>
	<view class="app">
		<view style="box-shadow: inset 0px 15px 8px -15px #ccc;width:100%;height:19rpx;position: fixed;"></view>
		<view class="all_pingjia">
			<view class="mid" v-for="(item,index1) in arrList" :key="index1">
				<view class="mid_user">
					<view style="display: flex;flex-direction: row;align-items: center;">
						<image :src="item.user" class="userimg"></image>
						<view class="username">{{item.username}}</view>
						<view v-for="(item,index) in array" :key="index" class="star">
							<image :src="item.src"></image>
						</view>
					</view>
					<view class="times">{{item.times}}</view>
				</view><!--mid_user-->
				<view class="mid_inner">
					<view class="innertxt">{{item.innertxt}}</view>
					<view style="display: flex;flex-direction: row;margin-top:30rpx;margin-bottom:32rpx;">
						<view class="inner_pingjia">
							<image :src="item.inner" v-if="item.inner != ''"></image>
						</view>
					</view>
				</view><!--mid_inner-->
			</view>
		</view><!--all-pingjia全部评价内容-->
	</view>
</template>

<script>
	import uniPopup from "../../components/uni-popup/uni-popup.vue"
	export default {
		components: {
			uniPopup
		},
		data() {
			return {
				"array":[
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'}
				],
				"arrList":[
					{"user":'/static/img/user.png',"username":'海绵宝宝喝水',"times":'2019-12-16',"innertxt":'一直都在用小苏打牙膏，这次买了一箱，好用再来！',"inner":'/static/img/biye1.png'},
					{"user":'/static/img/user1.png',"username":'章鱼哥吹笛子',"times":'2019-12-3',"innertxt":'一直都在用，这次买了一箱，好用再来！',"inner":''},
					{"user":'/static/img/user2.png',"username":'蟹老板卖汉堡',"times":'2019-11-15',"innertxt":'一直都在用工小苏打牙膏，这次买了一箱，好用再来！',"inner":'/static/img/biye4.png'},
					{"user":'/static/img/user1.png',"username":'章鱼哥吹笛子',"times":'2019-12-3',"innertxt":'一直都在用，这次买了一箱，好用再来！',"inner":''}
				]
			}
		},
		methods:{
			
		}
	}
</script>

<style>
	.app {
		width: 750rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 100%;
		position: relative;
	}

	.all_pingjia{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.mid{
		display: flex;
		flex-direction: column;
		width:100%;
		justify-content: center;
		align-items: center;
		margin-top:30rpx;
		border-bottom:1rpx solid;
		color:#FAFAFA;
	}
	.mid_user{
		width:94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border:0rpx solid red;
		align-items: center;
	}
	.userimg{
		width:60rpx;
		height:60rpx;
		margin-right:12rpx;
	}
	.username{
		font-size:24rpx;
		color:#B8B4B4;
		font-weight:600;
		margin-right:32rpx;
	}
	.star{
		display: flex;
		flex-direction: row;
	}
	.star image{
		width:20rpx;
		height:20rpx;
	}
	.times{
		color:#B8B4B4;
		font-size:24rpx;
	}
	.mid_inner{
		width:75%;
		border:0rpx solid red;
		margin-top:10rpx;
	}
	.innertxt{
		font-size:24rpx;
		color:#666666;
	}
	.inner_pingjia{
		display: flex;
		flex-direction: row;
		border:0rpx solid red;
	}
	.inner_pingjia image{
		width:200rpx;
		height:200rpx;
		margin-right:20rpx;
	}
	
</style>
