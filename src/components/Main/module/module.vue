<template>
	<div class="module"  v-bind:style="{ height: result.height+'px', background:result.background ,width:result.width+'px',zIndex:result.zIndex,left:result.x+'px',top:result.y+'px'}" v-on:click="toFather(result)"  >
		<div v-if="result.type==='font'"><font v-bind:result="result.attr"></font></div>
	</div>
</template>

<script>
import font from './font/font'
	export default {
		name: 'module',
		props: ["result"],
components: {
		font
	},
	methods: {
		greet: function(event) {
			console.log(event);
			event.current = true;
			this.$emit('hideAll')
		},
			toFather: function(result) {// 按钮点击触
	          this.$emit('myChild',this.massage)// 使用$emit来向父组件传播
	          result.current = true;
	      }
		  },
		data() {
			return {
			}
		}
	}
</script>
<style scoped>
.module{ position: absolute;}
</style>