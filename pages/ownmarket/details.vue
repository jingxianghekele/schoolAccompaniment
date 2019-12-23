<template>
	<view class="app">
		<view class="head">
			<image :src="src" class="bg"></image>
			<view class="price">￥{{price}}</view>
			<view class="name">
				<view class="title">
					{{title}}
				</view>
				<view class="share1" @click="open()">
					<img src="/static/img/commodity_share@2x(1).png">分享
				</view>
			</view>
		</view><!--head头部-->
		<view class="peisong">
			<view>配送费：<span>￥{{much}}</span></view>
		</view><!--配送费-->
		
		<!--留言为空-->
		<view class="liuyan">
			<view class="one">
				<view>宝贝评价（{{number}}）</view>
				<view>查看全部 ></view>
			</view>
			<view class="two">
				<img src="/static/img/message_none.png" >
				<view>该商品暂无评价，快去购买评价吧</view>
			</view>
		</view><!--留言-->
		
		
		<!--有留言内容-->
		<view class="leave">
			<view class="top">
				<view>宝贝评价（{{numbers}}）</view>
				<view @click="jump()">查看全部 ></view>
			</view><!--top-->
			<view class="mid">
				<view class="mid_user">
					<view style="display: flex;flex-direction: row;align-items: center;">
						<image :src="user" class="userimg"></image>
						<view class="username">{{username}}</view>
						<view v-for="(item,index) in array" :key="index" class="star">
							<image :src="item.src"></image>
						</view>
					</view>
					<view class="times">{{times}}</view>
				</view><!--mid_user-->
				<view class="mid_inner">
					<view class="innertxt">{{innertxt}}</view>
					<view style="display: flex;flex-direction: row;margin-top:30rpx;margin-bottom:32rpx;">
						<view v-for="(item,index1) in arrlist" :key="index1" class="inner_pingjia">
							<image :src="item.inner"></image>
						</view>
					</view>
				</view><!--mid_inner-->
			</view><!--mid用户评论部分-->
		</view><!--留言-->
		
		<view class="details">
			<view class="det_name">宝贝详情</view>
			<view class="det_img">
				<image :src="details" mode="widthFix"></image>
			</view>
		</view><!--details-->
		<view class="bottom">
			<view class="bottoms">
				<view class="left">
					<img src="/static/img/shopping_icon_car_big@2x.png" alt="">加入购物车
				</view>
				<view class="right">
					<button>联系商家</button><button @click="openPopup()">立即购买</button>
				</view>
			</view>
		</view><!--bottom-->
		
		<uniPopup ref="popup" type="bottom" custom="true" :maskClick="false" >
			<view class="popup">
				<view class="one1">
					<view class="ones1">
						<view class="one1_left">
							<image :src="goods"></image>
							<view class="lefts">
								<view>￥{{price}}</view>
								<view>库存{{muchs}}件</view>
							</view>
						</view>
						<view class="one1_right">
							<img src="/static/img/publish-button-cancel@2x.png" @click="closePopup()">
						</view>
					</view>
				</view><!--第一个部分one价格、库存-->
				<view class="two1">
					<view class="choose">请选择规格</view>
					<view class="pinpais">
						<view v-for="(item,index) in arrAy" :key="index" :class="{active:active == index}" @click="selected(index)" class="pinpaiss">
							{{item.pinpai}}
						</view>
					</view>
				</view><!--two第二个部分 品牌-->
				<view class="three">
					<view class="three_lef">
						请选择数量<span>（单位:件）</span>
					</view>
					<view class="three_rig">
						<view class="jia" @click="add">+</view>
						<view class="num"><input type="text"  class="input" value="1" v-model="number1"></view>
						<view class="jian" @click="cut">-</view>
					</view>
				</view><!--three第三部分选择租赁时长-->
				<view class="sure" @click="success()">
					<view>确定</view>
				</view><!--sure确定按钮-->
			</view><!--popup弹出框内容-->
		</uniPopup><!--弹出框-->
		
		<uniPopup ref="popup1" type="bottom" custom="true">
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
	export default{
		components: {
			uniPopup
		},
		data(){
			return{
				"number1":1,
				"number2":1,
				"goods":'/static/img/popup.png',
				"muchs":'222',
				active:'',
				"src":'/static/img/bg.png',
				"price":'29.90',
				"title":'纳美小苏打牙膏留兰香型180g去牙渍口臭减轻 牙龈疼痛',
				"much":'10.00',
				"number":'0',
				"details":'/static/img/details.png',
				"user":'/static/img/user.png',
				"numbers":'2290',
				"username":'海绵宝宝喝水',
				"times":'一天前',
				"innertxt":'一直都在用工小苏打牙膏，这次买了一箱，好用再来！',
				"arrAy":[
					{'pinpai':'美白'},
					{'pinpai':'护龈'},
				],
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
				"array":[
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'},
					{"src":'/static/img/appraise_start_pressed@2x.png'}
				],
				"arrlist":[
					{"inner":'/static/img/biye1.png'},
					{"inner":'/static/img/biye3.png'},
				]
			}
		},
		onNavigationBarButtonTap() {
			this.$refs.popup1.open()
		},
		methods: {
			jump(){
				uni.navigateTo({
					url:'all_pingjia'
				})
			},
			open() {
				this.$refs.popup1.open()
			},
			openPopup() {
				this.$refs.popup.open()
			},
			closePopup() {
				this.$refs.popup.close()
			},
			selected(index){
				this.active = index
			},
			success(){
				this.$refs.popup.close();
				uni.navigateTo({
					url:'tijiaodingdan'
				})		
			},
			add(){
				this.number1++;
			},
			cut(){ 
				this.number1--;
				if(this.number1 <1){
					this.number1 = 1
				}
			},
			add2(){
				this.number2++;
			},
			cut2(){
				this.number2--;
				if(this.number2 <1){
					this.number2 = 1
				}
			}
		}
	}
</script>

<style>
	.app{
		width:750rpx;
		display: flex;
		flex-direction: column;
		background: #FAFAFA;
		position: relative;
	}
	.head{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		background: #ffffff;
		border:0rpx solid red
	}
	.bg{
		width:100%;
		height:674rpx;
	}
	.price{
		color:#FF0606;
		font-size:26rpx;
		font-weight:bold;
		width:94%;
		margin-top:30rpx;
	}
	.name{
		margin-left:24rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border:0rpx solid red;
		margin-top:30rpx;
		margin-bottom:30rpx
	}
	.title{
		font-size: 26rpx;
		width:75%;
		font-weight:600;
	}
	.share1{
		font-size:26rpx;
		color:#666666;
		width:19%;
		background:rgba(233,234,235,1);
		opacity:0.43;
		border-radius:25rpx 0rpx 0rpx 25rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		height:50rpx;
		margin-top:12rpx
	}
	.share1 img{
		width:30rpx;
		height:30rpx;
	}
	/*配送费------------------------*/
	.peisong{
		width:100%;
		margin:20rpx 0;
		background: #ffffff;
	}
	.peisong view{
		font-size:28rpx;
		font-weight:600;
		margin:24rpx 0 24rpx 24rpx 
	}
	.peisong view span{
		color:#C5C4C4;
		font-weight:normal
	}
	/*留言内容------------------------*/
	.leave{
		width:100%;
		display: flex;
		flex-direction: column;
		background: #ffffff;
		align-items: center;
		border:0rpx solid red
	}
	.top{
		width:94%;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		margin-top:12rpx;
	}
	.top :first-child{
		font-size:26rpx;
		color:#666666
	}
	.top :last-child{
		font-size:24rpx ;
		color:#FF0606;
	}
	.mid{
		display: flex;
		flex-direction: column;
		width:94%;
		justify-content: center;
		align-items: center;
		margin-top:30rpx;
	}
	.mid_user{
		width:100%;
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
	
	
	/*留言为空--------------------------*/
	.liuyan{
		width:100%;
		display: flex;
		flex-direction: column;
		background: #ffffff;
		align-items: center;
		display: none;
	}
	.one{
		width:94%;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		margin-top:12rpx;
	}
	.one :first-child{
		font-size:26rpx;
		color:#666666
	}
	.one :last-child{
		font-size:24rpx ;
		color:#FF0606;
	}
	.two{
		margin-top:22rpx;
		display: flex;
		flex-direction: column;
	}
	.two img{
		width:468rpx;
		height:254rpx;
	}
	.two :last-child{
		font-size:24rpx;
		font-weight:400;
		color:rgba(184,180,180,1);
		opacity:1;
		margin:32rpx 0 54rpx 0
	}
	/*宝贝详情------------------------*/
	.details{
		width:100%;
		padding-bottom:80rpx;
	}
	.det_name{
		font-weight:600;
		font-size:30rpx;
		color:rgba(33,33,33,1);
		opacity:1;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin:20rpx 0;
	}
	.det_img{
		background: #ffffff;
	}
	.det_img image{
		width:100%;
		margin-top:20rpx;
	}
	
	/*底部按钮、加入购物车*/
	.bottom{
		width:100%;
		position: fixed;
		bottom:0;
		background: #ffffff;
	}
	.bottoms{
		display: flex;
		flex-direction: row;
	}
	.left{
		display: flex;
		flex-direction: column;
		align-items: center;
		font-size:20rpx;
		margin-left:50rpx;
		border:0rpx solid red;
		justify-content: space-between;
	}
	.left img{
		width:40rpx;
		height:40rpx;
		margin:12rpx 0 18rpx 0;
	}
	.left{
		margin-bottom:8rpx;
	}
	.right{
		display:flex ;
		flex-direction: row;
		margin-left:54rpx
	}
	.right button{
		width:260rpx;
		line-height:80rpx;
		margin:10rpx 0;
		font-size:30rpx
	}
	.right :first-child{
		border-radius:50rpx 0rpx 0rpx 50rpx;
		background: #FEC406;
	}
	.right :last-child{
		border-radius:0rpx 50rpx 50rpx 0rpx;
		background: #FFA024;
		color:#ffffff;
	}
	/*弹出框部分--------------------------------------*/
	.popup{
		width:100%;
		height:604rpx;
		border:0rpx solid red;
		background:#fff;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	/*价格、库存--------------------------------------------*/
	.one1{
		border-bottom:1rpx solid #E1E1E1;
		width:100%;
		display: flex;
		justify-content: center;
	}
	.ones1{
		margin:40rpx 0;
		width:94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.one1_left{
		display: flex;
		flex-direction: row;
		width:234rpx;
		border:0rpx solid green;
		justify-content: space-between;
		border:0rpx solid red;
	}
	.one1_left image{
		width:100rpx;
		height:100rpx;
		border-radius: 10rpx;
	}
	.lefts :first-child{
		font-size:26rpx;
		color:#F90A0A;
		margin-bottom:14rpx
	}
	.lefts :last-child{
		font-size:24rpx;
		color:#666;
	}
	.one1_right img{
		width:32rpx;
		height:32rpx;
	}
	/*品牌-------------------------------------*/
	.two1{
		width:94%;
		border-bottom:1rpx solid #E1E1E1;
		padding:36rpx 0;
	}
	.choose{
		font-size:30rpx;
		margin-bottom:14rpx;
	}
	.pinpais{
		display: flex;
		flex-direction: row;
		font-size:24rpx;
		color:#D6D1D1;
		border:0rpx solid red;
	}
	.pinpaiss{
		border-radius: 10rpx;
		width:110rpx;
		line-height:40rpx;
		border:1rpx solid #D6D1D1;
		text-align: center;
		margin-right:30rpx;
	}
	/*动态样式绑定*/
	.active{
		border:1rpx solid #FFC300;
		background:#FFC300;
		color:#212121;
	}
	/*第三部分租赁时长---------------------------------*/
	.three{
		width:94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding:18rpx 0;
		border:0rpx solid red
	}
	.three_lef{
		font-size:30rpx;
	}
	.three_lef span{
		font-size:24rpx;
		color:#D6D1D1;
	}
	.three_rig{/*加减---------------*/
		width:160rpx;
		height:40rpx;
		margin-right:30rpx;
		display: flex;
		flex-direction: row;
	}
	.jia{
		border:1rpx solid #B0B0B0;
		width:50rpx;
		height:40rpx;
		text-align: center;
		border-radius:6px 0px 0px 6px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		color:#B0B0B0;
	}
	.jian{
		border:1rpx solid #B0B0B0;
		width:50rpx;
		height: 40rpx;
		text-align: center;
		border-radius:0px 6px 6px 0px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		color:#B0B0B0;
	}
	.num{
		width:60rpx;
		text-align: center;
		height: 40rpx;
		border-top:1rpx solid #B0B0B0;
		border-bottom:1rpx solid #B0B0B0;
		font-size:24rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	/*确定按钮---------------------*/
	.sure{
		width:92%;
		line-height:80rpx;
		text-align: center;
		background:#FFC300;
		color:#212121;
		border-radius:40rpx;
		margin-top:64rpx
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
