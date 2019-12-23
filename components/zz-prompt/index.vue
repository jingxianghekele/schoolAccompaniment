<template>
  <view class="prompt-box" v-if="visible" @touchmove="true">
    <view class="prompt">
      <view class="prompt-top">
        <text class="prompt-title">{{title}}</text>
        <view class="name">
			<view style="font-weight:bold;font-size:36rpx;">姓名：</view>
			<input v-if="!isMutipleLine" class="prompt-input" :style="inputStyle" type="text" placeholder="张艺兴" v-model="value">
		</view>
		<view class="tel">
			<view style="font-weight:bold;font-size:36rpx;">手机：</view>
			<input v-if="!isMutipleLine" class="prompt-input" :style="inputStyle" type="text" placeholder="15588536790" v-model="value1">
		</view>
      </view>
      <slot></slot>
      <view class="prompt-buttons">
        <view class="prompt-cancle"  @click="close">取消</view>
        <view class="prompt-confirm"  @click="confirm">确定</view>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    props: {
      visible: {
        type: Boolean,
        default: false,
        required: true,
      },
      title: {
        type: String,
        default: '请输入参与信息',
      },
      mainColor: {
        type: String,
        default: '',
      },
      defaultValue: {
        type: String,
        default: '',
      },
      inputStyle: {
        type: String,
        default: '',
      },
      // 是否多行输入的textarea
      isMutipleLine: {
        type: Boolean,
        default: false,
      }
    },
    data() {
      return {
        value: '',
		value1:''
      }
    },
    watch: {
      visible(val) {
        if(val) {
          this.value = this.defaultValue
        }
      }
    },
    mounted() {
      this.value = this.defaultValue === 'true' ? '' : this.defaultValue
    },
    methods: {
      close() {
        this.$emit('update:visible', false)
      },
      confirm() {
        this.$emit('confirm', this.value)
        this.value = ''
		this.value1 = ''
		uni.showToast({
			title: '参与成功',
			success() {
				
			}
		})
      },
    }
  }
</script>

<style scoped>
  view,
  button,
  input {
    box-sizing: border-box;
  }

  .prompt-box {
    position: fixed;
    left: 0;
    top: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, .2);
    transition: opacity .2s linear;
  }

  .prompt {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 600upx;
    min-height: 300upx;
    background: white;
    border-radius: 20upx;
    overflow: hidden;
  }

  .prompt-top {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .prompt-title {
    margin: 40upx 0 40upx 40upx;
    color: #212121;
	font-weight:bold;
  }

  .prompt-input {
	margin-top:25upx;
    width: 70%;
    min-height: 72upx;
    border-radius: 8upx;
    font-size: 28upx;
    text-align: left;
	border:0upx solid red;
  }

  .prompt-buttons {
    display: flex;
    width: 100%;
  }
  
  .prompt-buttons button:after {
    border-radius: 0;
  }

  /* button {
    width: 50%;
    background: white;
    border-radius: 0;
	line-height:80upx;
	font-size: 36upx;
	margin:34upx 0
  }
 */
  .prompt-cancle {
    background: white;
	border:0;
	width: 50%;
	background: white;
	border-radius: 0;
	line-height:80upx;
	font-size: 36upx;
	margin:34upx 0;
	border-right:1upx solid #E1E1E1;
	text-align: center;
  }

  .prompt-confirm {
    color: yellow;
	width: 50%;
	background: white;
	border-radius: 0;
	line-height:80upx;
	font-size: 36upx;
	margin:34upx 0;
	text-align: center;
  }
  
  .name{
	  display: flex;
	  flex-direction: row;
	  border:0upx solid red;
	  line-height:118upx;
	  border-bottom: 1upx solid #E1E1E1;
	  justify-content: center;
  }
  .tel{
	  display: flex;
	  flex-direction: row;
	  border:0upx solid red;
	  line-height:118upx;
	  border-bottom: 1upx solid #E1E1E1;
	   justify-content: center;
  }
</style>
