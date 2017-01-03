<template>
	<div class="moduleInfo"  v-on:click="showThis(result)" v-show="result.current">
	<input type="text" v-model="result.width" />
		<input type="text" v-model="result.height" />
		<input type="text" v-model="result.background" />
		<input type="text" v-model="result.zIndex" />
		<input type="text" v-model="result.x" />
		<input type="text" v-model="result.y" />
		<div v-if="result.type==='font'"><fontInfo v-bind:result="result.attr"></fontInfo></div>
	</div>
</template>

<script>
import fontInfo from './font/fontInfo'
	export default {
		name: 'moduleInfo',
		components: {
		fontInfo
	},
		props: ["result"],
		methods:{
		  	 showThis: function (result) {
		  	 	console.log(result)
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