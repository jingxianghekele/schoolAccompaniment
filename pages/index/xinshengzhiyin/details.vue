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
	import uniPopup from "../../../components/uni-popup/uni-popup.vue"
	export default {
		components: {
			uniPopup
		},
		data() {
			return {
				'title': '清华大学',
				'txt1': '清华大学（Tsinghua University）是中华人民共和国教育部直属的高等院校，“211工程”、“985工程”、“世界一流大学和一流学科”，为亚洲大学、环太平洋大学等联盟成员，被誉为“红色工程师的摇篮”，是中国最著名的大学之一。',
				'txt2': '其前身是清华学堂，始建于1911年，因北京西北郊清华园而得名。1912年，更名为清华学校。1928年，更名为国立清华大学。1938年，迁至昆明，易名国立西南联合大学。1946年，迁回清华园复校。1949年后，更名“清华大学”。',
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
		height: 100%;
		position: relative;
	}

	.text {
		width: 90%;
		margin-top: 20rpx
	}

	.title {
		font-weight: bold;
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

	.inner {
		margin: 20rpx 0;
	}

	.inner view {
		font-size: 34rpx;
		color: #212121;
		letter-spacing: 60;
		line-height: 48rpx;
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
