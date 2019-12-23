<template>
	<view class="app">
		<view class="message">
			<view class="name">
				<img src="/static/img/icon_login_account@2x.png">
				<input type="text" placeholder="请输入姓名" >
			</view>
			<view class="tel">
				<img src="/static/img/icon_register_phone@2x.png">
				<input type="number" placeholder="请输入手机号">
			</view>
		</view><!--姓名、手机号-->
		<view class="details">
			<view class="title">{{title}}</view>
			<view class="desc">
				<image :src="img" class="img"></image>
				<view>
					<view class="area">{{area}}</view>
					<view class="pinpai">{{pinpai}}</view>
				</view>
			</view>
			<view class="three">
				<view class="three_lef">
					租赁数量<span>（单位:件）</span>
				</view>
				<view class="three_rig">
					<view class="jia" @click="add">+</view>
					<view class="num"><input type="text"  class="input" value="1" v-model="number1"></view>
					<view class="jian" @click="cut">-</view>
				</view>
			</view><!--three第三部分选择租赁时长-->
			<view class="four">
				<view class="four_lef">
					租赁时长<span>（单位:时）</span>
				</view>
				<view class="four_rig">
					<view class="jia2" @click="add2">+</view>
					<view class="num2"><input type="text"  class="input2" value="1" v-model="number2"></view>
					<view class="jian2" @click="cut2">-</view>
				</view>
			</view><!--第四部分租赁数量-->
		</view><!--租赁信息-->
		<view class="button">
			<view class="buttons">
				<view class="all">
					合计：<input type="text"  v-model="all" value="9.00">
				</view>
				<button class="but" @click="success()">提交订单</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"number1":1,
				"number2":1,
				"title":'租赁信息',
				"img":'/static/img/popup.png',
				"area":'临沂大学城对面体育馆羽毛球租赁',
				"pinpai":'李宁牌',
				"all":9+'.00'
			}
		},
		onNavigationBarButtonTap() { 
			uni.showModal({
			    title: '',
				content:'确定取消本次租赁吗？',
				confirmColor:'#FFC300',
			    success: function (res) {
			        if (res.confirm) {
			            uni.navigateBack({
			            	url:"./details"
			            })
			        } else if (res.cancel) {
			           
			        }
			    }
			});
		},
		methods:{
			add(){
				this.number1++;
				this.all++;
			},
			cut(){
				this.number1--;
				this.all--;
				if(this.number1 <1){
					this.number1 = 1;
					this.all = 9
				}
				
			},
			add2(){
				this.number2++;
				this.all++;
			},
			cut2(){
				this.number2--;
				this.all--;
				if(this.number2 <1){
					this.number2 = 1;
					this.all = 9
				}
			},
			success(){
				uni.navigateTo({
					url:'zhifuchenggong'
				})
			}
		}
	}
</script>

<style>
	.app{
		display: flex;
		width:750rpx;
		flex-direction: column;
		align-items: center;
		background:#FAFAFA;
		height:100vh;
		position: relative;
	}
	/*姓名、手机号------------------------------------*/
	.message{
		width:94%;
		border:0rpx solid red;
		margin:40rpx 0 34rpx 0;
		background: #FFFFFF;
		border-radius: 20rpx;
	}
	.name{
		display: flex;
		flex-direction: row;
		align-items: center;
		placeholder-color:rgba(230,230,230,1);
		font-size:28rpx;
		border-bottom: 1rpx solid #E1E1E1;
		padding:34rpx 0 26rpx 0;
	}
	.name img,.tel img{
		width:32rpx;
		height:32rpx;
		padding-left:36rpx
	}
	.name input{
		border:0rpx solid red;
		margin-left:10rpx;
	}
	.tel{
		display: flex;
		flex-direction: row;
		align-items: center;
		placeholder-color:rgba(230,230,230,1);
		font-size:28rpx;
		padding:34rpx 0 26rpx 0;
	}
	.tel input{
		margin-left:10rpx;
	}
	/*详细信息----------------------*/
	.details{
		width:94%;
		border:0rpx solid red;
		background:#FFFFFF;
		border-radius: 20rpx;
	}
	.title{
		font-weight:bold;
		font-size:28rpx;
		margin:30rpx 0 30rpx 20rpx;
	}
	.desc{
		display:flex;
		flex-direction: row;
		margin-left:20rpx;
	}
	.img{
		width:100rpx;
		height:100rpx;
		margin-right:20rpx;
	}
	.area{
		font-size:28rpx;
		margin-bottom:18rpx;
	}
	.pinpai{
		font-size:24rpx;
		color:#666666
	}
	
	.three{
		width:94%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		margin-left:20rpx;
		margin-top:28rpx;
		margin-bottom:40rpx;
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
		margin-left:20rpx;
		margin-bottom:32rpx;
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
	/*提交订单------------------------------*/
	.button{
		width:100%;
		position: fixed;
		bottom:0;
		box-shadow:0px 1rpx 8px -4px #ccc;
	}
	.buttons{
		width:100%;
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.all{
		font-size:30rpx;
		color:#666666;
		margin-left:330rpx;
		margin-right:30rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.all input{
		font-size:24rpx;
		color:#F90A0A;
		font-weight:bold;
		width:86rpx;
	}
	.but{
		border-radius: 44rpx;
		font-size:30rpx;
		font-weight:bold;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background: #FFC300;
		margin:20rpx 0;
		padding:0 40rpx;
		height:60rpx;
	}
</style>
