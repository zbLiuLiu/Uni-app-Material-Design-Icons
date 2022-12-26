<template>
	<view class="content">
		<view class="icon-container">
			<mdi-icon :icon="icon" :flip="flip.value" :rotate="rotate.value"></mdi-icon>
		</view>
		<text class="title" selectable>{{icon}}</text>
		<view class="options">
			<picker @change="(e)=>flip=flipRange[e.detail.value]" :value="flip.value" :range="flipRange" range-key="name">
				<view class="option-name">翻转模式</view>
				<view class="option-value" :class="{'active':flip.value}">{{flip.name}}</view>
			</picker>
			<picker @change="(e)=>rotate=rotateRange[e.detail.value]" :value="rotate.value" :range="rotateRange" range-key="name">
				<view class="option-name">旋转角度</view>
				<view class="option-value" :class="{'active':rotate.value}">{{rotate.name}}</view>
			</picker>
		</view>
		<view class="code">
			<text selectable>{{code}}</text>
		</view>
		<view class="options">
			<button type="primary" @click="copy(icon)">复制图标名</button>
			<button @click="copy(code)">复制代码</button>
		</view>
	</view>
</template>

<script>
export default {
		data() {
			return {
				icon:null,
				flip:{name:'不反转',value:null},
				flipRange:[{name:'不反转',value:null},{name:'水平反转',value:'horizontal'},{name:'垂直反转',value:'vertical'}],
				rotate:{name:'0°',value:null},
				rotateRange:[{name:'0°',value:null},{name:'45°',value:45},{name:'90°',value:90},{name:'135°',value:135},{name:'180°',value:180},{name:'225°',value:225},{name:'270°',value:270},{name:'315°',value:315}],
			};
		},
		computed:{
			code(){
				var attrs = ''
				if(this.icon) attrs += ` icon="${this.icon}"`;
				if(this.flip.value) attrs += ` flip="${this.flip.value}"`;
				if(this.rotate.value) attrs += ` :rotate="${this.rotate.value}"`;
				return `<mdi-icon${attrs}></mdi-icon>`
			},
			pageTitle(){
				return this.icon+" - Material Design Icons"
			}
		},
		onLoad(options) {
			if(!options.icon) uni.redirectTo({
				url:"/pages/index/index"
			})
			this.icon=options.icon
		},
		methods:{
			copy(text){
				uni.setClipboardData({
					data:text
				})
			}
		},
		watch:{
			pageTitle(){
				uni.setNavigationBarTitle({
					title:this.pageTitle
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.icon-container{
	height: 200rpx;
	width: 200rpx;
	margin-top: 200rpx;
	margin-left: auto;
	margin-right: auto;
	margin-bottom: 50rpx;
	
	font-size: 200rpx;
}
.title {
	font-size: 36rpx;
	color: #8f8f94;
}

.options{
	
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: center;
	flex-wrap: wrap;
	
	margin: 80rpx 0rpx 10rpx;
	
	column-gap: 80rpx;
	
	line-height: 1.8;
	
	
	.option-name{
		font-weight: 700;
		font-size: .8em;
		text-align: start;
	}
	
	.option-value{
		opacity: .4;
		text-align: center;
		display: flex;
		
		&.active{
			opacity: .8;
		}
		
		.input{
			line-height: 1.8;
			height: 1.8em;
			text-align: start;
		}
	}
}

.code{
	background-color: $uni-bg-color-grey;
	border-radius: 10rpx;
	overflow: hidden;
	padding: 20rpx 30rpx;
	font-family: Consolas,Monaco,Andale Mono,Ubuntu Mono,monospace;
	color:$uni-color-paragraph;
	font-size: $uni-font-size-paragraph;
	line-height: 1.4;
	margin: 40rpx auto;
}
</style>
