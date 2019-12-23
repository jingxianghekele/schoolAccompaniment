<template>
	<view class="app">
		<view class="head">
			<view v-for="(item,index) in array" :key="index" class="heads"  :class="{active:index==isShow}" @click="change(index)">
				<view class="type">
					<view class="type_title">{{item.type}}</view>
				</view>
			</view>
		</view><!--nav导航-->
		<view class="list">
			<view class="biyezhao" v-show="isShow===0">
				<biyezhao></biyezhao>
			</view>
			<view class="banjia" v-show="isShow===1">
				<banjia></banjia>
			</view>
			<view class="banjia" v-show="isShow===2">
				<zufang></zufang>
			</view>
			<view class="biyeliucheng" v-show="isShow===3">
				<biyeliucheng></biyeliucheng>
			</view>
			<view class="lunwenfuwu" v-show="isShow===4">
				<lunwenfuwu></lunwenfuwu>
			</view>
			<view class="qiugouzhuanqu" v-show="isShow===5">
				<qiugouzhuanqu></qiugouzhuanqu>
			</view>
			<view class="qiugouzhuanqu" v-show="isShow===6">
				<zhuanmai></zhuanmai>
			</view>
		</view><!--list列表内容-->
	</view>
</template>

<script>
	import biyezhao from '../../../components/index/biyezhiyin/biyezhao.vue'
	import banjia from '../../../components/index/biyezhiyin/banjia.vue'
	import biyeliucheng  from '../../../components/index/biyezhiyin/biyeliucheng.vue'
	import qiugouzhuanqu  from '../../../components/index/biyezhiyin/qiugouzhuanqu.vue'
	import zufang  from '../../../components/index/biyezhiyin/zufang.vue'
	import lunwenfuwu  from '../../../components/index/biyezhiyin/lunwenfuwu.vue'
	import zhuanmai  from '../../../components/index/biyezhiyin/zhuanmai.vue'
	
	export default{
		components:{biyezhao,banjia,biyeliucheng,qiugouzhuanqu,zufang,lunwenfuwu,zhuanmai},
		data(){
			return{
				isShow: 0,
				array: [
					{'type':"毕业照"}, 
					{'type':"搬家服务"}, 
					{'type':"租房服务"}, 
					{'type':"毕业流程 "}, 
					{'type':"论文服务"}, 
					{'type':"求购专区"},
					{'type':"转卖专区"},
					{'type':"其他"},
				]
				
			}
		},
		methods: {
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
	}
	/*导航*/
	.head{
		width:24%;
		border:0rpx solid red;
		background:#FAFAFA;
		height:100vh;
	}
	.heads{
		border:1rpx solid #FAFAFA
	}
	.type{
		width:100%;
		margin:24rpx 0;
		border-left:8rpx solid #FAFAFA;
	}
	.type_title{
		width:72%;
		text-align: center;
		line-height:48rpx;
		color:#B8B4B4;
		font-size:32rpx;
		border:0rpx solid #FAFAFA;
		margin:0 23rpx;
	}
	/*动态样式*/
	.active{
		.type{
			border-left-color:#FFC300;
		}
		.type_title{
			color:#FFC300;
		}
		background: #fff;
		border-color: #ffffff;
	}
	/*商品列表*/
	.list{
		width:72%;
		display: flex;
		flex-direction: column;
		border:0rpx solid red;
	}
	
</style>
