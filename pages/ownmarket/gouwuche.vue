<template>
	<view class="app">
		<view class="yellow"></view>
		<view class="gouwuche">
			<view class="none" v-if="0">
				<img src="/static/img/shopping-none@2x.png">
				<view>购物车里空空如也，快去逛逛吧~</view>
			</view>

			<view class="shops">
				<checkbox-group class="group">
					<label class="groups" v-for="item in checkboxItems" :key="item.name">
						<view class="kuang">
							<checkbox :value="item.name" :checked="item.checked" color="#FFCC33" ></checkbox>
						</view>
						<view class="shops">
							<image :src="item.src"></image>
							<view class="shopdetails">
								<view class="shopname">{{item.shopname}}</view>
								<view class="color">
									<select name="choose">
										<option>{{item.color1}}</option>
										<option>{{item.color2}}</option>
										<option>{{item.color3}}</option>
									</select>
								</view>
								<!--color选择色号-->
								<view class="details">
									<view class="price">￥{{item.price}}</view>
									<view class="three_rig">
										<view class="jia" @click="add">+</view>
										<view class="num"><input type="text" class="input" value="1" v-model="number1"></view>
										<view class="jian" @click="cut">-</view>
									</view>
								</view>
							</view>
							<!--shops-->
						</view>
						<!--kuang选择框-->
					</label>
					<!--label-->
				</checkbox-group>
			</view>
			<!--shops购物车物品-->
			<view class="bottom">
				<view class="bottoms">
					<view class="radio" @click="checked_all()"><checkbox color="#FFCC33" ></checkbox>全选</view>
					<view class="heji">合计:<span>￥{{jiage}}</span></view>
					<button class="button" @click="to()">结算</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				"number1":'1',
				"jiage":'0',
				"checkboxItems": [{
						"src": '/static/img/youhui2.png',
						"shopname": '瓷肌女性气垫CC霜，她会告诉你女人 是水做的',
						"color1": '象牙白',
						"color2": '自然白',
						"color3": '浅肤色',
						"price": '29.9'
					},
					{
						"src": '/static/img/youhui2.png',
						"shopname": '瓷肌女性气垫CC霜，她会告诉你女人 是水做的',
						"color1": '一盒装',
						"color2": '两盒装',
						"color3": '浅肤色',
						"price": '29.9'
					},
					{
						"src": '/static/img/youhui2.png',
						"shopname": '瓷肌女性气垫CC霜，她会告诉你女人 是水做的',
						"color1": '象牙白',
						"color2": '自然白',
						"color3": '浅肤色',
						"price": '29.9'
					}
				]
			}
		},
		methods: {
			add(){
				this.number1++;
			},
			cut(){
				this.number1--;
				if(this.number1 <1){
					this.number1 = 1
				}
			},
			checked_all(){
				
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
		justify-content: center;
		height: 100vh;
		background:#FAFAFA;
		position:relative;
	}

	.yellow {
		height: 112rpx;
		width: 100%;
		background:#FFC300;
		position: absolute;
		top:0;
	}

	/*购物车物品-------------------------*/
	.gouwuche {
		width: 94%;
		position: absolute;
		top: 0;
		background: #ffffff;
		border-radius: 20rpx;
		border:0rpx solid red;
		padding-bottom:40rpx;
	}

	/*商品列表------------------------*/
	.shops {
		width: 100%;
		background: #ffffff;
		border-radius: 20rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
		margin-right:22rpx;
		margin-top:40rpx;
	}
	.kuang{
		margin-left:20rpx
	}
	.groups {
		border: 0rpx solid red;
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.shops image {
		width: 180rpx;
		height: 180rpx;
		margin-left: 20rpx;
	}

	.shopname {
		font-size: 24rpx;
		font-weight: 400;
		color: rgba(33, 33, 33, 1);
		opacity: 1;
	}

	.shopdetails {
		display: flex;
		flex-direction: column;
		margin-left: 20rpx;
	}

	.color select {
		width: 120rpx;
		height: 50rpx;
		background: #F6F4F0;
		font-size: 24rpx;
		color: #8D8C8A;
		border-radius: 6rpx;
		margin: 18rpx 0;
	}
	.details{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.price {
		font-size: 24rpx;
		color: #FF0606;
		font-weight: 600;
	}




	.three_rig{/*加减---------------*/
		width:160rpx;
		height:36rpx;
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
	/*没有物品*/
	.none {
		margin-top: 300rpx;
		margin-bottom: 630rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.none img {
		width: 486rpx;
		height: 296rpx;
		margin-bottom: 80rpx;
	} 

	.none view {
		font-size: 26rpx;
		color: #B8B4B4;
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
		margin-left:262rpx;
		margin-right:16rpx;
	}
	.heji span{
		font-size:24rpx;
		color:#F90A0A;
		font-weight:600
	}
	.button{
		width:200rpx;
		height:80rpx;
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
