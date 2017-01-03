<template>
	<div  >
		<input type="text" v-model="result.fontSize" />
		<input type="text" v-model="result.fontFamily" />
		<input type="text" v-model="result.text" />
		<input type="text" v-model="result.textCenter" />
		<input type="text" v-model="result.color" />
		<input type="text" v-model="result.other.bold" />
	</div>
</template>

<script>
	export default {
		name: 'fontInfo',
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
</style>