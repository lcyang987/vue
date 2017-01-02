<template>
	<div class="main" id="main">
		<ul>
			 <li v-for="t  in list" >
			 	<div  v-bind:style="{ height: t.height+'px', background:t.background }"  class="c-module"> 
			 		{{t.name}}
			 		
			 		<template  v-for="tt in t.modules" >
			 			<module  v-bind:result="tt" ></module>
			 		</template>
			 		
			 		
			 	</div>
 		 </li>
		</ul>
		<div id="info">
		<li v-for="t  in list" >
		<template  v-for="tt in t.modules" >
			 			<moduleInfo  v-bind:result="tt" ></moduleInfo>
			 		</template>
			 		</div>
		</div>
	</div>
</template>

<script>
import module from './Main/module/module'
import moduleInfo from './Main/module/Info'
export default {
	name: 'cmain',
	components: {
		module,
		moduleInfo
	},
	data() {
		return {
			list: [{
				name: "模块1",
				background: "#ff0",
				height: 400,
				modules: [{
					x: 50,
					y: 100,
					width: 200,
					height: 200,
					zIndex: 1,
					url: false,
					background: "#000",
					type: "font",
					angle: 0,
					attr: { //字体需要双击模块可以修改字
						fontSize: "20",
						fontFamily: "微软雅黑",
						text:"我叫林彬彬",
						textCenter: "auto",
						color: "#fff",
						other: {
							bold: false, //加粗
							italic: false, //斜体
							lineThrough: false,
							underline: false //下划线
						}
					}
				}, {
					x: 100,
					y: 100,
					width: 200,
					height: 200,
					zIndex: 0,
					background: "#eee",
					url: false,
					angle: 0,
					type: "img", //图片模块更多的是裁剪操作  裁剪 水平翻转/垂直翻转 图片替换/图片交换 并且要裁剪里的裁剪选择器要和原本图片一样大 即等比例裁剪
					attr: {
						src: "xxx.png"
					}
				}, {
					x: 300,
					y: 100,
					width: 100,
					height: 200,
					zIndex: 0,
					background: "#ddd",
					url: false,
					angle: 0,
					type: "table", //表格模块需要新增删除行列 然后双击可以修改某一块字 单击修改他的属性 
					attr: {
						data: { //这块你们看下 有更好的双向绑定设计
							th: [{
								text: "列名1",
								fontSize: "20",
								fontFamily: "微软雅黑",
								textCenter: "auto",
								color: "#fff",
							}, {
								text: "列名1",
								fontSize: "20",
								fontFamily: "微软雅黑",
								textCenter: "auto",
								color: "#fff",
							}],
							td: [{
								text: "值1",
								fontSize: "20",
								fontFamily: "微软雅黑",
								textCenter: "auto",
								color: "#fff"
							}, {
								text: "值2",
								fontSize: "20",
								fontFamily: "微软雅黑",
								textCenter: "auto",
								color: "#fff"
							}]
						}
					}
				}, {
					x: 100,
					y: 100,
					width: 200,
					height: 200,
					zIndex: 0,
					background: "#000",
					url: false,
					angle: 0,
					type: "select", //选择框就是生成
					attr: {
						style: "", //有多个风格可以选择
						values: ["aaa", "bbb", "ccc"],
						select: "aaa"
					}
				}]
			}]
		}
	}
}</script>
<style scoped>h1,
h2 {
	font-weight: normal;
}

ul {
	list-style-type: none;
	padding: 0;
}

li {
	display: inline-block;
	margin: 0 10px;
}

a {
	color: #42b983;
}

.c-module {
	width: 600px;
	position: relative;
	overflow: hidden
}</style>