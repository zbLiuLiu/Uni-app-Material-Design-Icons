<template>
	<view class="content">
		<view class="head">
			<image class="logo" src="/static/logo.png"></image>
			<view class="options">
				<picker @change="(e)=>flip=flipRange[e.detail.value]" :value="flip.value" :range="flipRange" range-key="name">
					<view class="option-name">翻转模式</view>
					<view class="option-value" :class="{'active':flip.value}">{{flip.name}}</view>
				</picker>
				<picker @change="(e)=>rotate=rotateRange[e.detail.value]" :value="rotate.value" :range="rotateRange" range-key="name">
					<view class="option-name">旋转角度</view>
					<view class="option-value" :class="{'active':rotate.value}">{{rotate.name}}</view>
				</picker>
				<view>
					<view class="option-name">分页</view>
					<view class="option-value active">
						<uni-pagination title="标题文字" :show-icon="true" :total="filteredIcons.length" v-model="page" :pageSize="pageSize"></uni-pagination>
					</view>
				</view>
				<view>
					<view class="option-name">搜索</view>
					<view class="option-value" :class="{'active':search}">
						<input class="input" confirm-type="search" placeholder="输入关键词以搜索" v-model="search" />
						<label><switch :checked="regexp" @change="(e)=>regexp=e.detail.value" type="checkbox"/>使用正则表达式</label>
					</view>
				</view>
			</view>
		</view>
		<view class="icon-area">
			<button v-for="(item,index) in pagedIcons" :key="index" class="icon-button" @click="iconClick(item.name)">
				<mdi-icon :icon="item.name" :flip="flip.value" :rotate="rotate.value"></mdi-icon>
				<text class="info">{{item.name}}</text>
			</button>
		</view>
	</view>
</template>

<script>
	import icons from "./icons"
	export default {
		data() {
			return {
				flip:{name:'不反转',value:null},
				flipRange:[{name:'不反转',value:null},{name:'水平反转',value:'horizontal'},{name:'垂直反转',value:'vertical'}],
				rotate:{name:'0°',value:null},
				rotateRange:[{name:'0°',value:null},{name:'45°',value:45},{name:'90°',value:90},{name:'135°',value:135},{name:'180°',value:180},{name:'225°',value:225},{name:'270°',value:270},{name:'315°',value:315}],
				icons:[...icons,{ "name": "blank", "hex": "f68c" }],
				search:"",
				regexp:false,
				page:1,
				pageSize:200
			}
		},
		computed:{
			filteredIcons(){
				if(this.regexp){
					try{
						const regexp = new RegExp(this.search,"g")
						return this.icons.filter(value=>regexp.test(value.name))
					}catch(e){
						//TODO handle the exception
						return this.icons
					}
					
				}else{
					return this.icons.filter(value=>value.name.includes(this.search))
				}
				
			},
			pagedIcons(){
				return this.filteredIcons.slice((this.page-1)*this.pageSize,this.page*this.pageSize)
			}
		},
		methods:{
			iconClick(name){
				uni.navigateTo({
					url:"/pages/icon/icon?icon="+encodeURIComponent(name)
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {		
		.head{
			width: 100%;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			background-color: $uni-bg-color;
			margin-top: 180rpx;
			position: sticky;
			top: var(--window-top);
			z-index: 1;

			.logo {
				height: 200rpx;
				width: 200rpx;
				margin-top: 20rpx;
				margin-left: auto;
				margin-right: auto;
				margin-bottom: 50rpx;
			}
			
			.options{
				
				display: flex;
				flex-direction: row;
				align-items: center;
				justify-content: center;
				flex-wrap: wrap;
				
				margin: 10rpx 0rpx;
				
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
		}
		.icon-area {
			width: 100%;
			display: grid;
			grid-template-columns: repeat(auto-fill,120rpx);
			padding: 40rpx 0rpx 40rpx;
			grid-gap: 20rpx;
			justify-content: space-between;
			
			.icon-button{
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: flex-start;
				padding: 20rpx 10rpx;
				margin: 0rpx;
				gap:10rpx;
				.info{
					opacity: .6;
					font-size: .5em;
					line-height: 1;
				}
			}
			
		}
	}


</style>
