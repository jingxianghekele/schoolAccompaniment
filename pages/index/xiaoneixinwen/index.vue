<template>
	<view class="app">
		<view class="nav">
			<view class="nav_inner">
				<view class="news_title">
					<view v-for="(item,index) in array" :key="index" class="title_round" :class="{active:index==isShow}" @click="change(index)">
						<view class="round_name">{{item.name}}</view>
						<view class="huakuai"></view>
					</view>
				</view>
			</view><!--body_inner标题选择部分-->
		</view>
		<view class="jiaowuxinwen" v-show="isShow===0">
			<jiaowuxinwen></jiaowuxinwen>
		</view>
	</view>
</template>

<script>
	import jiaowuxinwen from '../../../components/index/xiaoneixinwen/jiaowuxinwen.vue'
	export default{
		components:{jiaowuxinwen},
		data(){
			return{
				isShow:0,
				"array":[
					{'name':'教务新闻'},
					{'name':'学院新闻'},
					{'name':'后勤公告'},
					{'name':'后勤消息'}
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
		display: flex;
		flex-direction: column;
		align-items: center;
		width:750rpx;
		border:0rpx solid red;
	}
	/*资讯、新闻、消息--------------------------------*/
	.nav{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		border:0rpx solid red
	}
	.nav_inner{
		width:94%;
		border:0rpx solid green;
	}
	.news_title{
		height:82rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		font-size:26rpx;
	}
	.title_round{
		margin-right:60rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.huakuai{
		width:100rpx;
		height:6rpx;
	}
	.active{
		font-size:32rpx;
		font-weight:bold;
		.title_round{
			margin-right:42rpx;
		}
		.huakuai{
			background:#FFC300;
			border-radius: 20rpx;
		}
	}
	.jiaowuxinwen{
		width:94%;
		display: flex;
		flex-direction: column;
		border:0rpx solid green;
	}
</style>
