<template>
	<text :class="classes" aria-hidden>
	</text>
</template>

<script>
	import './MaterialDesign-Webfont/scss/materialdesignicons.scss'
	export default {
		name:"mdi-icon",
		props:{
			icon:{
				type:String,
				required:true
			},
			rotate:{
				type:[String,Number],
				validator(value){
					switch (parseInt(value)){
						case 45 :
						case 90 :
						case 135 :
						case 180 :
						case 225 :
						case 270 :
						case 315 :
							return true
						default:
							return false
					}
				}
			},
			flip:{
				type:String,
				validator(value){
					switch (value+""){
						case 'horizontal' :
						case 'vertical' :
							return true
						default:
							return false
					}
				}
			}
		},
		computed:{
			classes(){
				var classes = ['mdi-icon','mdi','mdi-'+this.icon];
				if(this.rotate) classes.push('mdi-rotate-'+this.rotate);
				else if(this.flip) classes.push('mdi-flip-'+this.flip.slice(0,1));
				return classes
			}
		}
	}
</script>

<style lang="scss" scoped>
	.mdi-icon{
		display: inline-flex;
		width: 1em;
		height: 1em;
		justify-content: center;
		align-items: center;
	}
</style>
