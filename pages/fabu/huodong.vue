<template>
	<view class="app">
		<view style="box-shadow: inset 0px 15px 8px -15px #ccc;width:100%;height:19rpx;position: fixed;"></view>
		<view class="inner">
			<view class="title">
				<view>标题：</view><input type="text" placeholder="篮球友谊赛" class="a">
			</view>
			<view class="describe">
				<view>描述：</view><textarea value="" placeholder="来一场热血沸腾的篮球比赛吧" />
			</view>
			<view class="type">
				<view>分类：</view> 
				<view>
					<picker mode="selector">
						<view></view>
					</picker>
				</view>
			</view>
			<view class="begin">
				<view>活动时间：</view>
				<view>
					<picker mode="selector">
						<view></view>
					</picker>
				</view>
			</view>
			<view class="area">
				<view>活动地点：</view><input value="" placeholder="请输入地址" />
			</view>
			<view class="number">
				<view>活动人数：</view><input type="number" placeholder="请输入人数">
			</view>
			<view class="end">
				<view>截止时间：</view>
				<view>
					<picker mode="selector">
						<view></view>
					</picker>
				</view>
			</view>
			<view class="tel">
				<view>请输入手机号：</view><input type="text" placeholder="请输入手机号">
			</view>
			<view class="wechat">
				<view>请输入微信号：</view><input type="text" placeholder="请输入微信号">
			</view>
			<view class="QQ">
				<view>请输入QQ号：</view><input type="text" placeholder="请输入QQ号">
			</view>
			<view class="image">
				<view>添加照片<span> (最多9张)</span></view>
				<view class="addImg">
					<img src="/static/img/publish_img_add@2x.png" alt="">
				</view>
			</view>
			<view class="button">
				<button>发布</button>
			</view>
		</view><!--inner-->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				array: ['运动', '手机', '数码', '美妆','文具'],
			}
		},
		onNavigationBarButtonTap() {
			uni.showModal({
			    title: '',
				content:'确定取消本次发布吗？',
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
			bindPickerChange: function(e) {
			    this.index = e.target.value
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
		position: relative;
	}
	.inner{
		width:94%;
		height:100%;
		border:0rpx solid red;
	}
	.title,.describe,.price,.type,.area,.tel,.wechat,.QQ,.other,.begin,.end,.number{
		display: flex;flex-direction: row;
		border-bottom:1rpx solid #E1E1E1;
		
	}
	.title view,.describe view,.price view,.type view,.area view,.tel view,.wechat view,.QQ view,.other view,.begin view,.end view,.number view{
		font-size:32rpx;font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
	}
	.image{
		font-size:32rpx;
		font-weight:bold;
		color:rgba(33,33,33,1);
		opacity:1;
		border-bottom:1rpx solid #E1E1E1;
		padding-top:20rpx;
		height:318rpx;
	}
	.addImg{
		width:160rpx;
		height:160rpx;
		margin-top:36rpx;
		margin-left:60rpx;
	}
	.addImg img{
		width:160rpx;
		height:160rpx;
	}
	.title,.begin,.type,.area,.tel,.wechat,.QQ,.end,.number{
		line-height:104rpx;
		display: flex;flex-direction: row;align-items: center;
	}
	.title input,.area input,.tel input,.wechat input,.QQ input,.number input{
		padding-left:22rpx;
		border:0rpx solid red;
		width:60%;
		color:#666;
		font-size:28rpx;
	}
	.image span{
		color:#666;
		font-size:28rpx;
		font-weight:normal
	}
	.describe,.other{
		height:240rpx;
		padding-top:20rpx;
		border:0rpx solid red;
		border-bottom:1rpx solid #E1E1E1
	}
	.describe textarea,.other textarea{
		padding-left:22rpx;
		border:0rpx solid red;
		height:200rpx;
		padding-top:5rpx;
		color:#666;
		font-size:28rpx;
		width:80%
	}
	.button{
		margin:98rpx 0 236rpx 0;
	}
	.button button{
		width:648rpx;
		height:80rpx;
		background:rgba(255,195,0,1);
		opacity:1;
		border-radius:40px;
		font-size:28rpx;
		color: #212121;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		font-weight:bold;
	}
</style>
