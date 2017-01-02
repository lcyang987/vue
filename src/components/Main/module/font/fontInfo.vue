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
//	{ //字体需要双击模块可以修改字
//						fontSize: "20",
//						fontFamily: "微软雅黑",
//						text:"我叫林彬彬",
//						textCenter: "auto",
//						color: "#fff",
//						other: {
//							bold: false, //加粗
//							italic: false, //斜体
//							lineThrough: false,
//							underline: false //下划线
//						}
//					}

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