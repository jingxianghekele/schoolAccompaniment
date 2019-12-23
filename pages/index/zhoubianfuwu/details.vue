<template>
	<view class="app">
		<view class="head">
			<view class="img">
				<image :src="src"></image>
			</view>
			<view class="name">{{name}}</view>
		</view>
		<!--head图片、名称-->
		<view class="shangjia">
			<view class="top">商家信息</view>
			<view class="details">
				<view class="tit">{{tit}}</view>
				<view class="area">{{area}}</view>
				<view class="lianxi">联系方式：</view>
				<view class="tel">
					<view>手机：<span>{{phone}}</span></view>
					<view>微信：<span>{{wechat}}</span></view>
					<view>Q Q：<span>{{QQ}}</span></view>
				</view>
			</view>
			<!--详细信息-->
		</view>
		<!--商家信息-->
		<view class="desc">
			<view class="message">详细信息</view>
			<view class="text">{{text}}</view>
		</view>
		<!--详细描述-->
		<uniPopup ref="popup" type="bottom" custom="true">
			<view class="share">
				<view style="margin-top:40rpx">分享到</view>
				<view class="where">
					<view v-for="(item,index) in arr" :key="index" class="cho">
						<image :src="item.src" class="picture"></image>
						<view class="tool">{{item.where}}</view>
					</view>
				</view>
			</view>
		</uniPopup>
	</view>
</template>

<script>
	import uniPopup from "../../../components/uni-popup/uni-popup.vue"
	export default {
		components: {
			uniPopup
		},
		data() {
			return {
				"tit": '香格里拉理发店',
				"area": '北京市朝阳区北三环东路15号38号北京化工大学男生宿 舍1号楼门口',
				"phone": '13344765889',
				"wechat": '13344765889',
				"QQ": '447893456',
				"name": '香格里拉理发店限时请购288套餐！！！！',
				"src": '/static/img/youhui1.png',
				"arr": [{
						"src": '/static/img/login_icon_wechat@2x.png',
						'where': '微信'
					},
					{
						"src": '/static/img/login_icon_qq@2x.png',
						'where': 'QQ'
					},
					{
						"src": '/static/img/login_icon_space@2x.png',
						'where': '朋友圈'
					},
					{
						"src": '/static/img/login_icon_wechatquan@2x.png',
						'where': '空间'
					}
				],
				"text": '我们是从长沙出发直飞大理的，一出机场大厅就看到 婷婷在挥手迎接我们的到来，专车直奔大理古城。 我们大理古城的客栈办好入住，第一站就去了双廊和 崇圣寺，近距离的观看了崇圣寺三塔，之后就在大理 古城游玩，尽情感受古城生活气息。 我们是从长沙出发直飞大理的，一出机场大厅就看到 婷婷在挥手迎接我们的到来，专车直奔大理古城。 我们大理古城的客栈办好入住，第一站就去了双廊和 崇圣寺，近距离的观看了崇圣寺三塔，之后就在大理 古城游玩，尽情感受古城生活气息。 我们是从长沙出发直飞大理的，一出机场大厅就看到 婷婷在挥手迎接我们的到来，专车直奔大理古城。 我们大理古城的客栈办好入住，第一站就去了双廊和 崇圣寺，近距离的观看了崇圣寺三塔，之后就在大理 古城游玩，尽情感受古城生活气息。 我们是从长沙出发直飞大理的，一出机场大厅就看到 婷婷在挥手迎接我们的到来，专车直奔大理古城。 我们大理古城的客栈办好入住，第一站就去了双廊和 崇圣寺，近距离的观看了崇圣寺三塔，之后就在大理 古城游玩，尽情感受古城生活气息.'
			}
		},
		onNavigationBarButtonTap() {
			this.$refs.popup.open()
		},
		methods: {
			closePopup() {
				this.$refs.popup.close()
			}
		}
	}
</script>

<style>
	.app {
		width: 750rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.head {
		width: 100%;
		display: flex;
		flex-direction: column;
		border: 0rpx solid red
	}

	/*图片、名字那一块------------------------------*/
	.img image {
		width: 100%;
		height: 350rpx;
	}

	.name {
		font-size: 32rpx;
		font-weight: bold;
		margin: 40rpx 0 40rpx 24rpx;
	}

	/*商家信息---------------------------------------*/
	.shangjia {
		width: 100%;
		display: flex;
		flex-direction: column;
	}

	.top {
		font-size: 30rpx;
		color: #2D2D2D;
		background: #FAFAFA;
		padding-left: 34rpx;
		line-height: 80rpx;
		font-weight: bold;
	}

	.details {
		width: 100%;
		display: flex;
		flex-direction: column;
	}

	.tit {
		font-size: 26rpx;
		color: #2D2D2D;
		margin-left: 34rpx;
		margin-top: 40rpx;
		font-weight: bold;
	}

	.area {
		font-size: 26rpx;
		color: #B8B4B4;
		margin: 20rpx 20rpx 20rpx 34rpx;
	}

	.lianxi {
		font-size: 26rpx;
		color: #2D2D2D;
		font-weight: bold;
		margin-left: 34rpx;
	}

	.tel {
		display: flex;
		flex-direction: column;
		margin-left: 108rpx;
	}

	.tel view {
		font-size: 26rpx;
		color: #2D2D2D;
		margin-top: 12rpx
	}

	.tel view span {
		font-size: 26rpx;
		color: #B8B4B4;
		text-align: center;
	}

	/*详细描述------------------------------------*/
	.desc {
		width: 100%;
		display: flex;
		flex-direction: column;
	}

	.message {
		font-size: 30rpx;
		color: #2D2D2D;
		background: #FAFAFA;
		padding-left: 34rpx;
		line-height: 80rpx;
		font-weight: bold;
		margin-top: 28rpx;
	}

	.text {
		font-size: 30rpx;
		width: 94%;
		margin: 30rpx auto
	}

	/*分享到-------------------------------*/
	.share {
		width: 100%;
		height: 256rpx;
		background: #ffffff;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.where {
		width: 85%;
		margin-top: 22rpx;
		border: 0rpx solid red;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}

	.picture {
		width: 72rpx;
		height: 72rpx;
	}

	.tool {
		font-size: 26rpx;
	}

	.cho {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>
