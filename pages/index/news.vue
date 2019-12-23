<template>
	<view class="app">
		<view style="box-shadow: inset 0px 15px 8px -15px #ccc;width:100%;height:19rpx;position: fixed;"></view>
		<view class="text">
			<view class="title">
				<view>{{title}}</view>
			</view>
			<!--title文章标题-->
			<view class="inner">
				<view>{{txt1}}</view>
				<view>{{txt2}}</view>
				<view>{{txt3}}</view>
			</view>
			<!--inner文章内容-->
			<view>
				<image class="img" :src="src"></image>
				<!--img文章插图-->
			</view>
		</view>
		<!--text-->

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
	import uniPopup from "../../components/uni-popup/uni-popup.vue"
	export default {
		components: {
			uniPopup
		},
		data() {
			return {
				'title': '刚毕业的大学生想创业没有启动资金怎么办？',
				'txt1': '近几年的大学生就业压力越来越大，有部分毕业两年内的大学生有好点子想创业，但是苦于资金不足无法创业。今天我来给你支招,解决你的资金困难.',
				'txt2': '首先，有个前提条件就是毕业两年之内的毕业生，也是其中正规渠道贷款，具体方法，我后续文章再写',
				'txt3': '第二，办理地点是在当地就业局，你可以实地去咨询，每个地方贷款政策不一样，这个贷款是贴息贷款还有无息贷款一般最高可以贷10万,我们可以考虑这样来创业。',
				'src': '/static/img/sch5.png',
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
				]
			}
		},
		onNavigationBarButtonTap() {
			this.$refs.popup1.open()
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
		height: 100vh;
		position: relative;
	}

	.text {
		width: 90%;
		margin-top: 20rpx
	}

	.title {
		font-size: 44rpx;
		color: #212121;
		border: 0rpx solid red;
		position: relative;
	}

	.title img {
		position: absolute;
		top: 70rpx;
		left: 620rpx;
		width: 46rpx;
		height: 46rpx;
		border: 0rpx solid red
	}

	.inner view {
		font-size: 34rpx;
		color: #212121;
		letter-spacing: 60;
		line-height: 48rpx;
		margin: 30rpx 0
	}

	.img {
		width: 100%;
		height: 402rpx
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
