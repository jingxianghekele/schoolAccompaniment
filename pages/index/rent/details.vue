<template>
	<view class="app">
		<view class="top_nav">
			<img src="/static/img/nav.png" style="width:100%;height:100%">
		</view><!--top_nav自定义导航栏-->
		<view class="body">
			<view class="top">
				<view class="top1">
					<view class="title">{{title}}</view>
					<view class="area">
						<img src="/static/img/commodity_address.png" class="area_img">
						{{area}}
					</view>
				</view><!--top1地址栏-->
				<view class="top2">
					<view class="zujin">
						<view>{{zujin}}</view>
						<view>租金</view>
					</view>
					<view class="yajin">
						<view>{{yajin}}</view>
						<view>押金</view>
					</view>
					<view class="number">
						<view>{{number}}</view>
						<view>数量</view>
					</view>
				</view><!--top2租金、押金、数量-->
			</view><!--top地址、租金、押金、数量-->
			<view class="bottom">
				<view class="desc">
					<view class="desc_tit">描述</view>
					<view class="desc_txt">{{txt}}</view>
				</view><!--desc描述-->
				<view class="zulindesc">
					<view class="zulindesc_tit">租赁说明</view>
					<view class="zulindesc_txt">{{zulin_txt}}</view>
				</view><!--zulindesc租赁描述-->
				<view class="diyawu">
					<view class="diya">租赁抵押物</view>
					<view class="zulindesc_diya">{{diya}}</view>
				</view><!--desc描述-->
			</view><!--bottom描述、租赁说明-->
		</view><!--body-->
		<view class="call">
			<view class="calls">
				<view class="but">
					<button class="but_img">
						联系商家
					</button>
					<button class="liji" @click="openPopup()">立即租赁</button>
				</view><!--but立即租赁-->
			</view><!--calls-->
		</view><!--call致电-->
		<uniPopup ref="popup" type="bottom" custom="true" :maskClick="false" >
			<view class="popup">
				<view class="one">
					<view class="ones">
						<view class="one_left">
							<image :src="goods"></image>
							<view class="lefts">
								<view>{{price}}</view>
								<view>库存{{much}}件</view>
							</view>
						</view>
						<view class="one_right">
							<img src="/static/img/publish-button-cancel@2x.png" @click="closePopup()">
						</view>
					</view>
				</view><!--第一个部分one价格、库存-->
				<view class="two">
					<view class="choose">请选择品牌</view>
					<view class="pinpai">
						<view v-for="(item,index) in arr" :key="index" :class="{active:active == index}" @click="selected(index)" class="pinpais">
							{{item.pinpai}}
						</view>
					</view>
				</view><!--two第二个部分 品牌-->
				<view class="three">
					<view class="three_lef">
						请选择租赁时长<span>（单位:时）</span>
					</view>
					<view class="three_rig">
						<view class="jia" @click="add">+</view>
						<view class="num"><input type="text"  class="input" value="1" v-model="number1"></view>
						<view class="jian" @click="cut">-</view>
					</view>
				</view><!--three第三部分选择租赁时长-->
				<view class="four">
					<view class="four_lef">
						请选择租赁数量<span>（单位:件）</span>
					</view>
					<view class="four_rig">
						<view class="jia2" @click="add2">+</view>
						<view class="num2"><input type="text"  class="input2" value="1" v-model="number2"></view>
						<view class="jian2" @click="cut2">-</view>
					</view>
				</view><!--第四部分租赁数量-->
				<view class="sure" @click="success()">
					<view>确定</view>
				</view><!--sure确定按钮-->
			</view><!--popup弹出框内容-->
		</uniPopup><!--弹出框-->
		<uniPopup ref="popup1" type="bottom" custom="true" >
			<view class="share">
				<view style="margin-top:40rpx">分享到</view>
				<view class="where">
					<view v-for="(item,index) in array" :key="index" class="cho">
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
	export default{
		data(){
			return{
				isShow:0,
				"number1":1,
				"number2":1,
				"title":'临沂大学城体育馆羽毛球低价租赁',
				"area":'临沂大学对面体育馆中心',
				"zujin":'2/时',
				"yajin":'15/次',
				"number":'一副球拍加一个球',
				"txt":'临沂大学城体育馆羽毛球均是九成新以上的羽毛 球拍。让你一次性打到爽的羽毛球拍满足你的运动欲望。',
				"zulin_txt":'自下单起凭订单到店领取使用，到店内需要缴纳 所需押金，货物退还事退还押金，如若物品损坏 需要缴纳一定的赔偿金。',
				"goods":'/static/img/popup.png',
				"price":'￥2/时',
				"much":'222',
				active:'',
				"diya":'押金、学生证、其他',
				"arr":[
					{'pinpai':'李宁'},
					{'pinpai':'乔丹'},
					{'pinpai':'安踏'}
				],
				"array": [{
						"src": '/static/img/login_icon_wechat@2x.png',
						'where': '微信'
					},
					{
						"src": '/static/img/login_icon_qq@2x.png',
						'where': 'QQ'
					},
					{
						"src": '/static/img/login_icon_wechatquan@2x.png',
						'where': '朋友圈'
					}
				]
			}
		},
		onNavigationBarButtonTap() {
			this.$refs.popup1.open()
		},
		components:{
			uniPopup
		},
		methods:{
			return1(){
				uni.navigateBack({
					delta:1
				})
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
		position: relative;
		height: 100%;
	}
	/*导航栏--------------------------------------*/
	.top_nav{
		width:100%;
		height:500rpx;
		position: relative;
		top:0
	}
	.nav{
		width:94%;
		height:60rpx;
		display: flex;
		flex-direction: row;
		margin:58rpx 26rpx 0 26rpx;
		justify-content: space-between;
		align-items: center;
		position: absolute;
		border:0rpx solid red;
		top:0;
	}
	.back{
		width:48rpx;
		height:48rpx;
	}
	.rig_share{
		width:48rpx;
		height:48rpx;
	}
	/*底部白色部分------------------------------------------*/
	.body{
		width:100%;
		border:0rpx solid red;
		position: absolute;
		top:400rpx;
		background-color:#FAFAFA;
		border-radius: 20rpx 20rpx 0 0;
		border:0rpx solid red;
	}
	/*地点------------------------------*/
	.top{
		height:278rpx;
		width:100%;
		border:0rpx solid red;
		border-radius:20rpx 20rpx 0 0;
		background: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
		
	}
	.top1{
		width:94%;
		border:0rpx solid yellow;
		margin-top:14rpx;
	}
	.title{
		color:#212121;
		font-size:30rpx;
		font-weight:bold;
		margin-bottom:14rpx;
	}
	.area{
		font-size:26rpx;
		color:#212121;
		margin-bottom:14rpx;
		border:0rpx solid red;
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.area_img{
		width:28rpx;
		height:32rpx;
		margin-right:12rpx
	}
	.top2{
		display: flex;
		flex-direction: row;
		width:94%;
		border-top:1rpx solid #E1E1E1;
		border-bottom:1rpx solid #E1E1E1;
		height:118rpx;
		font-size:30rpx;
	}
	.zujin,.yajin{
		border-right:1rpx solid #E1E1E1;
	}
	.zujin,.yajin,.number{
		height:74rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin:22rpx 0;
	}
	.zujin :first-child,.yajin :first-child,.number :first-child{
		color:red;
		font-weight:bold;
		margin-bottom:2rpx
	}
	.zujin{
		width:180rpx;
		display: flex;
	}
	.yajin{
		width:206rpx;
	}
	.number{
		width:316rpx;
	}
	/*描述、租赁说明------------------------*/
	.bottom{
		margin-top:20rpx;
		background: #ffffff;
		border:0rpx solid green;
		display:flex;
		flex-direction: column;
		align-items: center;
	}
	.desc,.zulindesc,.diyawu{
		display: flex;
		flex-direction: column;
		align-items:center ;
	}
	.desc{
		width:94%;
		border:0rpx solid red;
		margin-top:26rpx;
	}
	.zulindesc{
		width:94%;
		border:0rpx solid red;
		margin-top:26rpx;
	}
	.diyawu{
		width:94%;
		border:0rpx solid red;
		margin-top:26rpx;
		margin-bottom:172rpx;
	}
	.desc_tit,.zulindesc_tit,.diya{
		font-size:30rpx;
		color:#212121;
		font-weight:bold;
		width:100%;
		border:0rpx solid red
	}
	.desc_txt,.zulindesc_txt,.zulindesc_diya{
		margin-top:14rpx;
		font-size:30rpx;
		color:#212121;
		width:92%;
		line-height:42rpx;
	}
	/*联系商家、立即租赁*/
	.call{
		width:100%;
		border:0rpx solid red;
		height:98rpx;
		position: fixed;
		bottom:0;
		box-shadow:0px 1rpx 8px -4px #ccc;
	}
	.but{
		display: flex;
		height:98rpx;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		border: 0rpx solid red;
		width:93%;
		margin-left:4%
	}
	.but button{
		border:rpx solid green;
		width:350rpx;
		height:80rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 0rpx solid red;
	}
	.but_img{
		background: #FEC406;
		border-radius:50rpx 0px 0px 50rpx;
	}
	.liji{
		background: #FFA024;
		border-radius:0rpx 50px 50px 0rpx;
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
	.one{
		border-bottom:1rpx solid #E1E1E1;
		width:100%;
		display: flex;
		justify-content: center;
	}
	.ones{
		margin:40rpx 0;
		width:94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.one_left{
		display: flex;
		flex-direction: row;
		width:238rpx;
		border:0rpx solid green;
		justify-content: space-between;
	}
	.one_left image{
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
	.one_right img{
		width:32rpx;
		height:32rpx;
	}
	/*品牌-------------------------------------*/
	.two{
		width:94%;
		border-bottom:1rpx solid #E1E1E1;
		padding:36rpx 0;
	}
	.choose{
		font-size:30rpx;
		margin-bottom:14rpx;
	}
	.pinpai{
		display: flex;
		flex-direction: row;
		font-size:24rpx;
		color:#D6D1D1;
	}
	.pinpais{
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
		padding:18rpx 0;
		border-bottom:1rpx solid #D6D1D1;
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
	/*第四部分租赁数量--------------------------*/
	.four{
		width:94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding:18rpx 0;
	}
	.four_lef{
		font-size:30rpx;
	}
	.four_lef span{
		font-size:24rpx;
		color:#D6D1D1;
	}
	.four_rig{
		width:160rpx;
		height:40rpx;
		margin-right:30rpx;
		display: flex;
		flex-direction: row;
	}
	.jia2{
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
	.jian2{
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
	.num2{
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
	}
	/*分享到--------------------------*/
	.share{
		width:100%;
		height:256rpx;
		background: #ffffff;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.where{
		width:65%;
		margin-top:22rpx;
		border:0rpx solid red;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.picture{
		width:72rpx;
		height:72rpx;
	}
	.tool{
		font-size:26rpx;
	}
	.cho{
		display: flex;
		flex-direction: column;
		align-items: center;
	}
</style>
