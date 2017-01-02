<template>
	<div class="font" v-bind:style="{ fontSize: result.fontSize+'px', fontFamily:result.fontFamily }">
	{{result.text}}
		<input type="text" v-model="result.text" />
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
		name: 'font',
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