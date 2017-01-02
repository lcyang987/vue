<template>
	<div class="module"  v-bind:style="{ height: result.height+'px', background:result.background ,width:result.width+'px',zIndex:result.zIndex,left:result.x+'px',top:result.y+'px'}" v-on:click="greet">
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
		methods:{
		  	 greet: function (event) {
		  	 	
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