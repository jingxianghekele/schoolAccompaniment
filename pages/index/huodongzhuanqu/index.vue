<template>
	<view class="app">
		<view class="head">
			<view v-for="(item,index) in arrlist" :key="index" class="heads"  :class="{active:index==isShow}" @click="change(index)">
				<view class="type">
					<view class="type_title">{{item.type}}</view>
				</view>
			</view>
		</view><!--search搜索兼职-->
		<view class="huodongzhuanqu" v-show="isShow===0">
			<huodongzhuanqu></huodongzhuanqu>
		</view><!--jobList兼职列表-->
		<view class="shixi" v-show="isShow===1">
			hahah
		</view>
		<view class="jianzhi" v-show="isShow===2">
			hahah
		</view>
		<view class="zhaopin" v-show="isShow===3">
			hahah
		</view>
		<view class="qita" v-show="isShow===4">
			hahah
		</view>
	</view>
</template>

<script>
	import huodongzhuanqu from '../../../components/index/huodongzhuanqu/details.vue'
	export default{
		components:{huodongzhuanqu},
		data(){
			return{
				isShow:0,
				"arrlist":[
					{'type':'校内活动'},{'type':'社区活动'},{'type':'学生活动'},
					{'type':'其他'}
				]
			}
		},
		methods:{
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
		display: flex;
		flex-direction: row;
		height: 100vh;
	}
	/*头部选择类型-----------------------------*/
	.head{
		width:24%;
		border:0rpx solid red;
		background:#FAFAFA;
		height:100%;
		border:0rpx solid red
	}
	.heads{
		border:1rpx solid #FAFAFA;
	}
	.type{
		width:100%;
		border-left:8rpx solid #FAFAFA;
		margin:24rpx 0;
	}
	.type_title{
		text-align: center;
		width:80%;
		line-height:48rpx;
		font-size:32rpx;
		border:0rpx solid red;
		margin-left:10rpx
	}
	/*动态样式*/
	.active{
		.type{
			border-left:8rpx solid #FFC300;
		}
		border-color: #ffffff;
		color:#FFC300;
		background: #fff;
	}
	/*兼职列表--------------------------------------*/
	.huodongzhuanqu,.shixi,.jianzhi,.zhaopin,.qita{
		width:72%;
		display: flex;
		flex-direction: column;
		border:0rpx solid red;
	}
	
	.call{
		width:80rpx;
		height:80rpx;
	}
	
	
</style>
