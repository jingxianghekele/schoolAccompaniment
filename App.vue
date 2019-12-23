<script>
	export default {
		onLaunch: function() {
			console.log('App Launch'),
			uni.onTabBarMidButtonTap(()=>{
				//在此可以直接进行跳转
				// uni.switchTab({
				// 	url:'/pages/mine/mine'
				// })
				// return
				const subNVue = uni.getSubNVueById('release-home')
				subNVue.show('slide-in-bottom')
				//关闭
				uni.$on('close-release', ()=>	subNVue.hide('slide-out-bottom') )
				uni.$on('tapThis', ({index, url})=>{
					console.log(index, url)
					// 在此根据url可以进行跳转页面
					//subNVue.hide('slide-out-bottom') //隐藏
				})
			})
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style scoped>
	/*每个页面公共css */
	.uni-checkbox-input {
		border-radius: 50% !important;
		color: #ffffff !important;
	}

	 .uni-checkbox-input.uni-checkbox-input-checked {
		color: #fff;
		border-color: rgba(255, 195, 0, 1);
		background: rgba(255, 195, 0, 1);
	}

	.uni-checkbox-input.uni-checkbox-input-checked:after {
		font-size: 18px;
	}
</style>
