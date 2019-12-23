<template>
	<view>
		<view class="round" v-for="(item,index) in arr" :key="index" >
			<view class="rou_inner">
				<view class="round1" @click="toPage(item.a)">
						<view class="name">{{item.name}}</view>
						<view class="job">{{item.job}}</view>
						<view class="company">{{item.company}}</view>
						<view class="price">{{item.price}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"arr":[
					{'name':'崂山中韩送餐员兼职日结','job':'青岛 | 生活配送员','company':'青岛比兔快物流有限公司','price':'150元/天','src':'/static/img/part_time_phone.png','a':'/pages/index/part-time/details'},
					{'name':'闪送紧急招募兼职配送员','job':'市南 | 生活配送员','company':'北京闪送科技有限公司','price':'133元/天','src':'/static/img/part_time_phone.png','a':'/pages/index/part-time/details'},
					{'name':'短期工男女不限','job':'黄岛 | 其他兼职','company':'青岛恒众源企业管理有限公司','price':'133元/天','src':'/static/img/part_time_phone.png','a':'/pages/index/part-time/details'},
					{'name':'崂山中韩送餐员兼职日结','job':'青岛 | 生活配送员','company':'青岛比兔快物流有限公司','price':'150元/天','src':'/static/img/part_time_phone.png','a':'/pages/index/part-time/details'},
					{'name':'闪送紧急招募兼职配送员','job':'市南 | 生活配送员','company':'北京闪送科技有限公司','price':'133元/天','src':'/static/img/part_time_phone.png','a':'/pages/index/part-time/details'}
				]
			}
		},
		methods:{
			toPage(a){
				uni.navigateTo({
					url:a
				})
			}
		}
	}
</script>

<style>
	.round{
		width:100%;
		border-bottom:1rpx solid #E1E1E1;
		display:flex;
		flex-direction: column;
		align-items: center;
	}
	.rou_inner{
		width:91%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin:28rpx 0;
		border:0rpx solid red;
		height:190rpx
	}
	.round1{
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.round2{
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.name{
		font-size:30rpx;
		color:#212121;
		font-weight:bold;
	}
	.job{
		font-size:26rpx;
		color:#666666;
	}
	.company{
		font-size:26rpx;
		color:#666666;
	}
	.price{
		color:#F90A0A;
		font-size:30rpx;
	}
</style>
