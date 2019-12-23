<template>
	<view class="app">
		<view style="box-shadow: inset 0px 15px 8px -15px #ccc;width:100%;height:19rpx;position: fixed;"></view>
		<view class="shop">
			<view class="name">{{name}}</view>
			<view class="desc">
				<view class="price">￥{{price}}</view>
				<view class="describe">{{describe}}</view>
				<image :src="img1" class="img1" mode="widthFix"></image>
				<image :src="img2" class="img2" mode="widthFix"></image>
			</view>
		</view><!--商品信息-->
		<view class="beizhu">
			<view class="shuoming">备注说明</view>
			<view class="text">{{shuoming}}</view>
		</view><!--备注信息-->
		<view class="area">
			<view class="jiaoyi">交易地址</view>
			<view class="dizhi">{{dizhi}}</view>
		</view><!--交易地址-->
		<!--留言为空，去留言-->
		<view class="null">
			<view class="null_all">全部留言</view>
			<view class="to">
				<img src="/static/img/img_No_message@2x.png" class="null_img">
				<view class="null_null">暂无留言</view>
				<button class="null_to">去留言</button>
			</view><!--to-->
		</view><!--null-->
		
		
		
		
		
		
		<!--有留言的部分-->
		<view class="liuyan">
			<view class="all">全部留言·{{all}}</view>
			<view v-for="(item,index) in array" :key="index" class="words">
				<view class="words_one">
					<view style="display: flex;flex-direction: row;align-items: center;">
						<image :src="item.src" class="userimg"></image>
						<view class="username">{{item.userName}}</view>
					</view>
					<view class="date">{{item.date}}</view>
				</view><!--words_one买家头像名称-->
				<view class="words_two"> {{item.innerText}}</view><!--words-two买家留言内容-->
				<view v-for="(item,index1) in arrlist" :key=index1 class="reply">
					<view class="reply_one">
						<image :src="item.src" class="image"></image>
						<view class="user">{{item.user}}</view>
						<view class="who">主人</view>
					</view><!--主人头像名称-->
					<view class="reply_two">
						回复@{{item.maijia}}:{{item.inner}}
					</view>
				</view><!--reply卖家回复-->
			</view><!--words第一个大循环-->
		</view><!--liuyan全部留言-->
		<view class="footer">
			<view class="footers">
				<view class="foo1">
					<image :src="icon"></image>
					<view>留言</view>
				</view>
				<view class="foo2">
					<button>联系商家</button>
				</view>
			</view>
		</view><!--footer-->
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
				"name":'360 N4 9成新手机',
				"price":'299',
				"describe":'360N4 银色 自用 64G 无锁 手机没有问题 后面 有点氧化周围有点磕碰的痕迹 手机没有换过屏 指纹完 好 电池半天一冲。',
				"img1":'/static/img/phone2.png',
				"img2":'/static/img/phone.png',
				"shuoming":'本手机决对没有任何使用问题，有看好的可以电话联系机 不可失失不再来',
				"dizhi":'北京市朝阳区北三环东路15号38号北京化工大学男生宿 舍1号楼门口',
				"icon":'/static/img/message@2x.png',
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
				"all":'3',
				"array":[
					{"src":'/static/img/user.png',"userName":'不太帅的帅哥',"date":'一天前',"innerText":'可以便宜一点吗？'},
					{"src":'/static/img/user2.png',"userName":'小仙女酵母',"date":'一月前',"innerText":'宝贝还在吗？'},
					{"src":'/static/img/user1.png',"userName":'不太懒的懒羊羊',"date":'三月前',"innerText":'好像要呀，可以让价吗？'}
				],
				"arrlist":[
					{"src":'/static/img/user1.png',"user":'哆啦A梦',"who":'天上的仙女',"maijia":'不太帅的帅哥',"inner":'你想便宜多少，一切好 说你可以电话联系我'},
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
		background: #FAFAFA;
	}
	/*商品的信息----------------------*/
	.shop{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		background: #ffffff;
	}
	.name{
		font-size:36rpx;
		color:rgba(33,33,33,1);
		width:100%;
		border-bottom:1rpx solid #E1E1E1;
		padding:24rpx 0 28rpx 28rpx;
		font-weight:bold;
	}
	.desc{
		width:94%;
	}
	.price{
		font-size:30rpx;
		color:rgba(249,10,10,1);
		margin:10rpx 0 20rpx 0;
		font-weight:boldrpx;
	}
	.describe{
		font-size:30rpx;
		color:rgba(33,33,33,1);
		opacity:1;
		margin-bottom:12rpx
	}
	.img1,.img2{
		width:100%;
	}
	.img2{
		margin-top:-10rpx;
		margin-bottom:20rpx;
	}
	/*备注说明-----------------------------*/
	.beizhu{
		width:100%;
		margin-top:20rpx;
		background: #ffffff;
	}
	.shuoming{
		font-size:30rpx;
		font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
		margin-left:24rpx;
		margin-top:12rpx;
	}
	.text{
		font-size:26rpx;
		font-weight:400;
		color:rgba(33,33,33,1);
		opacity:1;
		margin:2rpx 38rpx 12rpx 58rpx;
	}
	/*交易地址----------------------*/
	.area{
		width:100%;
		background: #ffffff;
		border:0rpx solid  red;
		margin-top:20rpx;
	}
	.jiaoyi{
		font-size:30rpx;
		font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
		margin-left:24rpx;
		margin-top:12rpx;
	}
	.dizhi{
		font-size:26rpx;
		font-weight:400;
		color:rgba(33,33,33,1);
		opacity:1;
		margin:2rpx 38rpx 12rpx 58rpx;
	}
	
	/*暂无留言------------------------------*/
	.null{
		width:100%;
		background: #ffffff;
		padding-bottom:136rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-top:20rpx
	}
	.null_all{
		font-size:30rpx;
		color:rgba(33,33,33,1);
		font-weight:bold;
		opacity:1;
		width:94%;
		margin-top:36rpx;
	}
	.null_img{
		width:514rpx;
		height:312rpx;
		margin-top:10rpx;
	}
	.null_null{
		font-size:18rpx;
		color:#999999;
		margin-top:42rpx;
	}
	.to{
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.to button{
		width:130rpx;
		height:50rpx;
		background:rgba(255,196,2,1);
		opacity:1;
		border-radius:10rpx;
		font-size:24rpx;
		color:#212121;
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-top:16rpx;
	}
	
	
	
	
	/*留言部分--------------------------------*/
	.liuyan{
		width:100%;
		background:#ffffff;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding-bottom:100rpx;
		display: none;
	}
	/*第一个循环---------------*/
	.words{
		display: flex;
		flex-direction: column;
		align-items: center;
		border-bottom:1rpx solid #E1E1E1;
		padding-bottom:12rpx;
		margin-top:20rpx;
		
	}
	.words_one{
		border:0rpx solid red;
		display: flex;
		flex-direction: row;
		align-items: center;
		width:94%;
		justify-content: space-between;
	}
	.all{
		font-size:30rpx;
		font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
		width:94%;
	}
	.username{
		font-size:24rpx;
		font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
		margin-left:20rpx;
	}
	.date{
		font-size:24px;
		color:rgba(102,102,102,1);
		opacity:1;
	}
	.words_two{
		width:94%;
		font-size:24rpx;
		color:rgba(102,102,102,1);
		margin-left:80rpx;
		opacity:1;
	}
	.userimg,.image{
		width:60rpx;
		height: 60rpx;
	}
	.date{
		font-size:24rpx;
		color:rgba(102,102,102,1);
		opacity:1
	}
	
	/*第二个循环------------------------*/
	.reply{
		width:84%;
		margin-top:10rpx;
	}
	.user{
		font-size:24rpx;
		font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
		margin-left:20rpx;
		margin-left:20rpx
	}
	.who{
		border:1px solid rgba(46,188,247,1);
		opacity:1;
		border-radius:10rpx;
		font-size:22rpx;
		color:rgba(88,188,252,1);
		opacity:1;
		text-align: center;
		margin-left:20rpx;
		line-height:30rpx;
		width:54rpx;
	}
	.reply_one{
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.reply_two{
		margin-left:80rpx;
		font-size:24rpx;
	}
	/*底部按钮。留言--------------------------*/
	.footer{
		width:100%;
		position: fixed;
		background: #ffffff;
		bottom:0;
		border:0rpx solid red;
		box-shadow: 0px 1rpx 8px -4px #ccc;
	}
	.footers{
		width:100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.foo1{
		display: flex;
		flex-direction: column;
		margin-left:24rpx;
		justify-content: center;
	}
	.foo1 image{
		width:41rpx;
		height:34rpx;
	}
	.foo1 view{
		font-size:24rpx;
		margin-top:8rpx
	}
	.foo2 button{
		margin:10rpx  24rpx 10rpx 0;
		width:620rpx;
		height:80rpx;
		background:rgba(255,195,0,1);
		opacity:1;
		border-radius:44rpx;
		font-size:30rpx;
		color:rgba(33,33,33,1);
		opacity:1;
		display: flex;
		flex-direction: column;
		justify-content: center;
		font-weight:bold
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
