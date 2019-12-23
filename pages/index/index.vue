<template>
	<view class="app">
		<view class="head">
			<view style="width:100%;height:180rpx;background:#FFC300"></view>
			<view class="head_swiper">
				<swiper :autoplay="true" :interval="4000" :circular="true" :indicator-dots="true" :indicator-active-color="color1"
				 :indicator-color="color2" class="swiper">
					<swiper-item v-for="(item,index6) in arr" :key="index6" class="swiper_round">
						<image :src="item.src" class="round_img"></image>
					</swiper-item>
					<!--swiper-->
				</swiper>
			</view>
			<!--head_swiper轮播图部分-->
			<view style="width:100%;display: flex;flex-direction:column; center;align-items: center;">
				<view class="area">
					<view v-for="(item,index1) in arrlist" :key="index1" class="area_round" @click="toPage(item.a)">
						<image :src="item.src" class="round_image"></image>
						<view class="round_title">{{item.title}}</view>
					</view>
				</view>
				<!--area十个专区-->
			</view>
		</view>
		<!--head头部搜索框，轮播图，专区部分-->
		<view class="body">
			<view class="body_inner">
				<view class="news_title">
					<view v-for="(item,index) in array" :key="index" class="title_round" :class="{active:index==isShow}" @click="change(index)">
						<view class="round_name">{{item.name}}</view>
						<view class="huakuai"></view>
					</view>
				</view>
			</view>
			<!--body_title标题选择部分-->
			<view class="news_page">
				<view class="schoolNews" v-show="isShow===0">
					<xinwen></xinwen>
				</view>
				<!--schoolNews校内资讯的页面内容-->
				<view class="hotNews" v-show="isShow===1">
					222
				</view>
				<!--hotNews热点新闻页面内容-->
				<view class="newNews" v-show="isShow===2">
					333
				</view>
				<!--newNews最新消息页面内容-->
			</view>
			<!--news_page新闻资讯内容部分-->
		</view>
		<!--body中间资讯、新闻、消息部分-->
		<view class="bottom">
			<view class="bottom_inner">
				<view class="inner_title">{{title}}</view>
				<view class="shop">
					<view v-for="(item,index5) in shop" :key="index5" class="shop_round">
						<view class="round_box">
							<view class="img_box">
								<image :src="item.src" class="shop_img" mode="widthFix"></image>
							</view>
							<view class="shop_name">{{item.name}}</view>
							<view class="shop_bottom">
								<view class="shop_price">{{item.price}}</view>
								<view class="shop_buy">{{item.buy}}</view>
							</view>
						</view>
						<!--round_box循环里的盒子-->
					</view>
					<!--shop-round商品循环-->
				</view>
				<!--shop商品陈列-->
			</view>
			<!--bottom_inner底部内容-->
		</view>
		<!--bottom底部商品-->
		<!-- <uniPopup ref="popup" type="bottom" custom="true" :maskClick="false" >
		</uniPopup> -->
	</view>
</template>

<script>
	import uniPopup from '../../components/uni-popup/uni-popup.vue'
	import xinwen from '../../components/index/xiaoneixinwen/jiaowuxinwen.vue'
	export default {
		components: {
			xinwen,uniPopup
		},
		data() {
			return {
				scrollTop: 0,
				old: {
					scrollTop: 0
				},
				isShow: 0,
				color1: '#F4C145',
				color2: '#FCA23D',
				sch1Name: '大学里存在的“阴暗交易”,触目惊心,本该单纯的……',
				sch2Name: '十年大赛促百余个大学生创业项目落地事先产值超亿元',
				sch2Text: '为贯彻落实国家、省、市创新创业部署、有效推进……',
				title: '推荐商品',
				"arr": [{
						'src': '/static/img/index_bannder@2x.png'
					},
					{
						'src': '/static/img/index_bannder@2x.png'
					},
					{
						'src': '/static/img/index_bannder@2x.png'
					},
					{
						'src': '/static/img/index_bannder@2x.png'
					}
				],
				"arrlist": [{
						'src': '/static/img/index_icon_rent@2x.png',
						'title': '免租专区',
						'a': '/pages/index/rent/index'
					},
					{
						'src': '/static/img/index_icon_part_time@2x.png',
						'title': '兼职招聘',
						'a': '/pages/index/part-time/index'
					},
					{
						'src': '/static/img/index_icon_resell@2x.png',
						'title': '毕业指引',
						'a': '/pages/index/biyezhiyin/index'
					},
					{
						'src': '/static/img/index_icon_favourable@2x.png',
						'title': '周边服务',
						'a': '/pages/index/zhoubianfuwu/index'
					},
					{
						'src': '/static/img/index_icon_shooping@2x.png',
						'title': '自营商店'
					},
					{
						'src': '/static/img/index_icon_kaoyan@2x.png',
						'title': '考研/升学',
						'a': '/pages/index/kaoyanshengxue/index'
					},
					{
						'src': '/static/img/index_icon_activity@2x.png',
						'title': '活动专区',
						'a': '/pages/index/huodongzhuanqu/index'
					},
					{
						'src': '/static/img/index_icon_news@2x.png',
						'title': '校内新闻',
						'a': '/pages/index/xiaoneixinwen/index'
					},
					{
						'src': '/static/img/index_icon_school@2x.png',
						'title': '新生指引',
						'a': '/pages/index/xinshengzhiyin/index'
					},
					{
						'src': '/static/img/index_icon_more@2x.png',
						'title': '更多分类'
					},
				],
				"array": [{
						'name': '校内资讯'
					},
					{
						'name': '热点新闻'
					},
					{
						'name': '最新消息'
					}
				],
				"arrList": [{
						'src': '/static/img/sch1-1.png'
					},
					{
						'src': '/static/img/sch1-2.png'
					},
					{
						'src': '/static/img/sch1-1.png'
					}
				],
				"shop": [{
						'src': '/static/img/shop1.png',
						'name': '电动牙刷充电式学生党女生男全自动牙刷',
						'price': '￥119.0',
						'buy': '立即购买'
					},
					{
						'src': '/static/img/shop2.png',
						'name': '纯棉毛巾家用男女洗澡洗脸实惠',
						'price': '￥19.00',
						'buy': '立即购买'
					},
					{
						'src': '/static/img/shop3.png',
						'name': '正品纳爱斯牙膏鲜浓果味120g防蛀护龈',
						'price': '￥19.00',
						'buy': '立即购买'
					},
					{
						'src': '/static/img/shop4.png',
						'name': '福百年本色竹浆卫生纸卷纸批发',
						'price': '￥119.0',
						'buy': '立即购买'
					}
				]
			}
		},
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url: 'search'
			})
		},
		methods: {
			search() {
				uni.navigateTo({
					url: 'search'
				})
			},
			change(index) {
				if (this.isShow != index) {
					this.isShow = index;
				}
			},
			toPage(a) {
				uni.navigateTo({
					url: a
				})
			}
		}
	}
</script>

<style lang="scss">
	.app {
		display: flex;
		flex-direction: column;
		width: 750rpx;
		background-color: #FAFAFA;
		height: 100%;
	}

	.head {
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		background-size: 50%;
		border: 0rpx solid red;
		position: relative;
	}

	/*轮播图------------------------------*/
	.head_swiper {
		position: absolute;
		top: 0;
		width: 94%;
		border-radius: 20rpx;
		border: 0rpx solid black;
		display: flex;
		justify-content: center;
		height: 260rpx;
	}

	.swiper {
		width: 100%;
		border-radius: 20rpx;
		overflow: hidden;
		transform: translateY(0);
	}

	.swiper_round {
		border-radius: 20rpx;
		overflow: hidden;
		transform: translateY(0);
	}

	.round_img {
		width: 100%;
		height: 260rpx;
		border-radius: 20rpx;
		border: 0rpx solid red;
	}

	/*四个专区部分----------------------*/
	.area {
		width: 94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border: 0rpx solid red;
		flex-wrap: wrap;
		margin-top: 100rpx;
	}

	.area_round {
		width: 18%;
		border: 0rpx solid black;
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-bottom: 28rpx
	}

	.round_image {
		width: 88rpx;
		height: 88rpx;

	}

	,
	.round_title {
		font-size: 24rpx;
		color: #333333
	}

	/*资讯、新闻、消息--------------------------------*/
	.body {
		width: 100%
	}

	.border_inner {
		width: 100%;
		border: 1rpx solid red
	}

	.news_title {
		margin-left: 24rpx;
		height: 82rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		font-size: 26rpx;
		border-top: 1rpx solid #E1E1E1;
		border-bottom: 1rpx solid #E1E1E1;
	}

	.title_round {
		border: 0rpx solid red;
		margin-right: 80rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.huakuai {
		width: 80rpx;
		height: 6rpx;
	}

	.active {
		font-size: 30rpx;
		font-weight: bold;

		.huakuai {
			background: #FFC300;
			border-radius: 20rpx;
		}
	}

	/*资讯内容----------------------------*/
	.news_page {
		border: 0rpx solid red;
	}

	/*校内资讯---------------------------*/
	.schoolNews {
		width: 100%;
		border: 0rpx solid #007AFF;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	/*校内资讯第一篇*/
	.sch1 {
		width: 94%;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 40rpx 0;
		border-bottom: 1rpx solid #E1E1E1
	}

	.sch1Name {
		font-weight: bold;
		width: 100%;
		font-size: 28rpx;
		color: #212121;
		margin-bottom: 8rpx;
	}

	.sch1_img {
		width: 100%;
		display: flex;
		flex-direction: row;
		border: 0rpx solid #3F536E;
		justify-content: space-between;
		border: 0rpx solid #008000
	}

	.img_img {
		width: 220rpx;
		height: 140rpx;
		border: 0rpx solid red
	}

	/*校内资讯第二篇*/
	.sch2 {
		width: 94%;
		display: flex;
		flex-direction: column;
		padding: 40rpx 0;
		border-bottom: 1rpx solid #E1E1E1
	}

	.sch2Name {
		font-weight: bold;
		width: 100%;
		font-size: 28rpx;
		color: #212121;
		margin-bottom: 8rpx
	}

	.sch2Text {
		width: 100%;
		font-size: 24rpx;
		color: #A5A5A5
	}

	/*第三四五篇文章*/
	.sch345 {
		border: 0rpx solid red;
		width: 94%
	}

	.sch345_round {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border: 0rpx solid blue;
		padding: 40rpx 0;
		border-bottom: 1rpx solid #E1E1E1
	}

	.sch345_name {
		font-weight: bold;
		font-size: 28rpx;
		color: #212121;
		margin-bottom: 8rpx;
		width: 432rpx;
	}

	.sch345_text {
		font-size: 24rpx;
		color: #A5A5A5;
		width: 432rpx;
	}

	.sch345_img {
		width: 220rpx;
		height: 140rpx;
	}

	/*底部商品---------------------------------------------*/
	.bottom {
		width: 100%;
		border: 0rpx solid red;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.bottom_inner {
		width: 94%;
	}

	.inner_title {
		margin: 30rpx 0;
		color: #FFC300;
		font-size: 30rpx;
		border-left: 4rpx solid #FFC300;
		padding-left: 14rpx
	}

	.shop {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		border: 0rpx solid red;
	}

	.shop_round {
		width: 336rpx;
		background-color: #FFF;
		margin-bottom: 30rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		border-radius: 20rpx;
		;
		border: 0rpx solid black
	}

	.round_box {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.img_box {
		width: 100%;
		height: 300rpx;
		border: 0rpx solid pink;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.shop_img {
		width: 236rpx;
		height: auto;
		border: 0rpx solid green
	}

	.shop_name {
		width: 312rpx;
		font-size: 26rpx;
		color: #666666;
		margin-top: 8rpx;
		border: 0rpx solid red
	}

	.shop_price {
		width: 110rpx;
		color: #F90A0A;
		font-size: 24rpx;
		line-height: 40rpx;
		border: 0rpx solid red;
		text-align: center;
	}

	.shop_buy {
		line-height: 40rpx;
		color: #F90A0A;
		font-size: 24rpx;
		border: 1rpx solid red;
		border-radius: 20rpx;
		padding: 0 22rpx;
		text-align: center;
	}

	.shop_bottom {
		width: 310rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin-top: 8rpx;
		margin-bottom: 24rpx;
	}
</style>
