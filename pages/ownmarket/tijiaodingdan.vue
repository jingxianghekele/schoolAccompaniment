<template>
	<view class="app">
		<view style="box-shadow: inset 0px 15px 8px -15px #ccc;width:100%;height:19rpx;position: fixed;"></view>
		<view class="top">
			<view class="null">
				<view>暂无地址，去手动添加地址</view>
				<view> > </view>
			</view>
			
			<view v-if="0">
				<view class="top_one">
					<view style="display: flex;flex-direction: row;width:44%;align-items: center;border:0rpx solid red">
						<view class="name">{{name}}</view>
						<view class="tel">{{tel}}</view>
					</view>
					<view class="reset">
						<img src="/static/img/reset.png">修改
					</view>
				</view><!--top_one买家信息-->
				<view class="top_two">
					<view class="moren">默认</view>
					<view class="area">{{area}}</view>
				</view><!--地址信息-->
			</view>
		</view><!--top-->
		<view class="shop">
			<view class="shops">
				<view class="image">
					<image :src="src"></image>
				</view>
				<view class="shoped">
					<view class="shop_name">{{shop_name}}</view>
					<view class="shop_details">
						<view class="guige">规格：{{guige}}</view>
						<view class="price">￥{{price}}</view>
					</view>
				</view><!--商品信息-->
			</view><!--shops-->
			<view class="shops_bottom">
				<view class="number">
					<view class="numbers">购买数量：</view>
					<view class="three_rig">
						<view class="jia" @click="add">+</view>
						<view class="num"><input type="text"  class="input" value="1" v-model="number1"></view>
						<view class="jian" @click="cut">-</view>
					</view>
				</view>
				<view class="peisong">配送费：<span>{{peisong}}</span></view>
				<view class="all">商品总额：<span>￥{{zonge}}</span></view>
			</view>
		</view><!--商品信息-->
		<view class="liuyan">
			<view class="input">
				留言:<input type="text" placeholder="给卖家留言">
			</view>
		</view><!--留言-->
		<view class="bottom">
			<view class="bottoms">
				<view class="radio"><checkbox style="transform:scale(0.8)"></checkbox>线下付款</view>
				<view class="heji">合计:<span>￥{{jiage}}</span></view>
				<button class="button" @click="to()">提交订单</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				"number1":'1',
				"name":'海绵宝',
				"tel":'13356748976',
				"area":'安徽省-合肥市-庐阳区 某某某街道阜阳北 路与北城大道交口创智天地',
				"src":'/static/img/youhui2.png',
				"shop_name":'坚果大礼包坚果大礼包坚果大礼包坚果大礼包 坚果大礼包',
				"guige":'全部套装【68块】',
				"price":'128',
				"peisong":'8.00',
				"zonge":'256',
				"jiage":'9.00'
				
			}
		},
		methods:{
			add(){
				this.number1++;
			},
			cut(){
				this.number1--;
				if(this.number1 <1){
					this.number1 = 1
				}
			},
			to(){
				uni.navigateTo({
					url:'zhifuchenggong'
				})
			}
		}
	}
</script>
<style>
	.app{
		width: 750rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 100%;
		position: relative;
		background: #F9F9F9;
	}
	/*卖家信息部分---------------------*/
	.top{
		display: flex;
		flex-direction: column;
		align-items: center;
		width:100%;
		background: #ffffff;
		padding-bottom:26rpx;
	}
	.null{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding:70rpx 0;
		width:94%;
		align-items: center;
	}
	.null :first-child{
		font-size:28rpx;
		font-weight:400;
		color:rgba(45,45,45,1);
		opacity:1;
		margin-left:24rpx;
	}
	.null :last-child{
		margin-right:26rpx;
		color:#666666;
	}
	
	
	.top_one{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		margin-top:26rpx;
		width:94%;
		/* display: none; */
	}
	.name{
		font-size:28rpx;
		font-weight:600;
		color:rgba(51,51,51,1);
		opacity:1;
	}
	.tel{
		font-size:26rpx;
		color:rgba(51,51,51,1);
		opacity:1;
		margin-left:52rpx;
	}
	.reset img{
		width:30rpx;
		height:30rpx;
		margin-right:16rpx;
	}
	.reset{
		font-size:24rpx;
		font-weight:400;
		color:rgba(102,102,102,1);
		opacity:1;
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	/*买家地址-------------------*/
	.top_two{
		display: flex;
		flex-direction: row;
		margin-top:18rpx;
		align-items: center;
		width:94%;
		/* display: none; */
	}
	.moren{
		width:80rpx;
		height:40rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		border:2rpx solid rgba(253,65,65,1);
		opacity:1;
		border-radius:20px;
		font-size:24rpx;
		color:#FD4141;
		margin-right:56rpx;
	}
	.area{
		font-size:26rpx;
		font-weight:400;
		color:rgba(102,102,102,1);
		opacity:1;
		width:64%;
		text-align: justify;
	}
	/*商品信息部分----------------------------*/
	.shop{
		width:100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		background: #ffffff;
		margin-top:10rpx;
	}
	.shops{
		margin-top:28rpx;
		width:94%;
		display: flex;
		flex-direction: row;
		background: #FAFAFA;
		border-radius: 20rpx;
	}
	.shoped{
		display: flex;
		flex-direction: column;
		border:0rpx solid green;
		margin:48rpx 22rpx;
	}
	.image image{
		width:120rpx;
		height:120rpx;
		margin:48rpx 22rpx;
	}
	.shop_details{
		display: flex;
		flex-direction: row;
		border:0rpx solid red;
		align-items: center;
		justify-content: space-between;
	}
	.guige{
		font-size:24rpx;
		line-height:22px;
		color:rgba(153,153,153,1);
		opacity:1;
	}
	.shop_name{
		font-size:26rpx;
		font-weight:400;
		color:rgba(0,0,0,1);
		opacity:1;
	}
	.price{
		font-size:26rpx;
		color:#FE4545;
		font-weight:600;
	}
	/*商品数量、配送费、商品总额---------------*/
	.shops_bottom{
		width:94%;
		display: flex;
		flex-direction: column;
		align-items: center;
		border:0rpx solid red;
		margin-bottom:22rpx;
	}
	.numbers,.peisong,.all{
		font-size:26rpx;
		font-weight:400;
		color:rgba(33,33,33,1);
		opacity:1;
	}
	.peisong,.all{
		width:100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border:0rpx solid red;
		margin-top:22rpx;
	}
	.number{
		width:100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border:0rpx solid red;
		margin-top:22rpx;
	}
	.peisong span{
		fpnt-weight:26rpx
	}
	.all span{
		color:#FE4646;
		font-size:28rpx;
		font-weight:600;
	}
	.three_rig{/*加减---------------*/
		width:160rpx;
		height:40rpx;
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
	/*留言部分-------------------*/
	.liuyan{
		box-shadow:0px 1rpx 8px -4px #ccc;
		width:100%;
		margin-top:10rpx;
		background:#ffffff;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background: #ffffff;
		padding-bottom:376rpx;
	}
	.input{
		width:94%;
		color:#333333;
		font-size:23rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		border-bottom:1rpx solid #F2F2F2;
		padding:20rpx 0; 
	}
	.input input{
		font-size:23rpx;
		padding-left:40rpx;
		border:0rpx solid red;
		width:85%;
	}
	/*底部部分-----------------------*/
	.bottom{
		width:100%;
		position: fixed;
		bottom:0;
	}
	.bottoms{
		width:100%;
		display: flex;
		flex-direction: row;
		align-items: center;
		background: #ffffff;
		box-shadow:0px 1rpx 8px -4px #ccc;
	}
	.radio{
		font-size:28rpx;
		color:#707070;
		padding-left:20rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.heji{
		font-size:30rpx;
		color:#666666;
		margin-left:134rpx;
		margin-right:30rpx;
	}
	.heji span{
		font-size:24rpx;
		color:#F90A0A;
		font-weight:600
	}
	.button{
		width:200rpx;
		height:60rpx;
		background:linear-gradient(90deg,rgba(247,202,56,1) 0%,rgba(255,195,0,1) 100%);
		opacity:1;
		border-radius:44rpx;
		font-size:30rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin:20rpx 0;
	}
</style>