<template>
	<view class="content" 
	:style="{backgroundImage: 'url('+imageURL+')',
	height:windowHeight,
	width:windowWidth,
	backgroundSize:backgroundsize}">
		<!-- 表单 -->
		<form class="myform" @submit="formSubmit" @reset="formReset">
			<!-- 头像 -->
			<view class="head_icon">
				<image src="../../static/logo.png" mode="scaleToFill" style="width: 136rpx; height: 136rpx;"></image>
			</view>
			<!-- 输入框 -->
			<view class="logo_input">
				<!-- 用户名输入框 -->
				<view class="logo_input_user">
					<picker @change="bindPickerChange" :value="index" :range="array" range-key="name">
						<view>{{array[index].name}}</view>
					</picker>
					<view class="logo_input_div" >|</view>
					<input class="logo_input_user_text" type="number" placeholder="请 输 入 手 机 号 码 登 录" />
				</view>
				<!-- 密码输入框 -->
				<view class="logo_input_pass">
					<image src="../../static/logo/drawable-hdpi/icon_password_3login.png" mode="scaleToFill"  style="width: 30rpx; height: 37rpx;"></image>
					<view class="logo_input_div" >|</view>
					<input class="logo_input_pass_text" type="text" password="true" placeholder="请 输 入 密 码" />
				</view>
			</view>
			<!-- 输入框下的两个操作 -->
			<view class="logo_note">
				<!-- 跳转短信登录 -->
				<view class="logo_note_right">
					<image src="../../static/logo/drawable-hdpi/icon_dx_dl.png" mode="scaleToFill" style="width: 35rpx; height: 30rpx;"></image>
					短&nbsp;信&nbsp;验&nbsp;证
				</view>
				<!-- 跳转找回密码界面 -->
				<view class="logo_note_left">
					忘&nbsp;记&nbsp;密&nbsp;码 ?
				</view>
			</view>
			<!-- 底部两个按钮 -->
			<view class="logo_submit">
				<!-- 实现密码的记忆 -->
				<view class="logo_submit_remember">
					<image src="../../static/logo/drawable-hdpi/icon_jzmm_dl.png" mode="scaleToFill" style="width: 30rpx; height: 30rpx;"></image>
					&nbsp;记住密码<checkbox value="cb" checked="true"  />选中
				</view>
				<!-- 表单数据提交按钮和跳转注册界面按钮 -->
				<view class="logo_submit_button">
					<button class="logo_button_submit" form-type="submit">登&nbsp;录</button>
					<button class="logo_button_register" >注&nbsp;册</button>
				</view>
			</view>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imageURL : '/static/logo/drawable-hdpi/bg_dl.png',
				windowHeight : '',
				windowWidth : '',
				backgroundsize : '',
				index : 0,
				array: [{name:'+86'},{name: '+96'}, {name:'+00'}, {name:'+01'}]
			}
		},
		onReady(){
			uni.getSystemInfo({
				success: res =>  {
					this.windowHeight=res.windowHeight+'px';
					this.windowWidth=res.windowWidth+'px';
					this.backgroundsize=res.windowWidth+'px '+res.windowHeight+'px';
				}
			})
		},
		methods: {
			formSubmit(){
				uni.switchTab({
				    url: '/pages/index/index'
				});
			},
			bindPickerChange: function(e) {
				this.index = e.target.value
			}
		}
	}
</script>

<style>
	.myform,.head_icon,.logo_input,.logo_input_user,.logo_input_pass,.logo_input_div,.logo_note,.logo_note_right,.logo_submit_remember,.logo_submit_button{
		display: -webkit-flex;
		display: flex;
	}
	.myform{
		justify-content: center ;
		flex-wrap: wrap;
	}
	.head_icon{
		height: 414rpx;
		width: 576rpx;
		justify-content:  center ;
		align-items: center;
	}
	.logo_input{
		width: 576rpx;
		height: 180rpx;
		flex-direction:  column ;
		justify-content:  space-between ;
	}
	.logo_input_user,.logo_input_pass{
		color:#f8f8f8 ;
		background-color: #515151;
		height: 80rpx;
		border-radius: 6px;  
		align-items: center;
	}
	.logo_input_user{
		padding-left: 10rpx;
		width: 566rpx;
	}
	.logo_input_pass{
		padding-left: 32rpx;
		width: 544rpx;
	}
	.logo_input_div{
		flex-direction: row-reverse ;
		width: 40rpx;
	}
	.logo_input_user_text,.logo_input_pass_text{
		padding-left: 40rpx;
	}
	.logo_note{
		flex-direction:  row ;
		justify-content:  space-between ;
		align-items: center;
		width: 576rpx;
		height: 80rpx;
		color: #f8f8f8;
	}
	.logo_note_right{
		width: 170rpx;
		flex-direction:  row ;
		justify-content:  space-between ;
		align-items: center;
		font-size: 25rpx;
	}
	.logo_note_left{
		font-size: 25rpx;
	}
	.logo_submit{
		width: 576rpx;
		height: 660rpx;
		color: #f8f8f8;
	}
	.logo_submit_remember{
		padding-left: 30rpx;
		padding-bottom: 20rpx;
		width: 160rpx;
		flex-direction:  row ;
		justify-content:  space-between ;
		align-items: center;
		font-size: 25rpx;
	}
	.logo_submit_button{
		width: 576rpx;
		height: 190rpx;
		flex-direction:  column ;
		justify-content:  space-between ;
	}
	.logo_button_submit,.logo_button_register{
		color: #f8f8f8;
		width: 576rpx;
		height: 80rpx;
		border-radius: 6px; 
	}
	.logo_button_submit{
		background-color: #8b5322;
	}
	.logo_button_register{
		background-color: #6a6a6a;
	}
</style>
