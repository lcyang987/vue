<template>
	<div class="hello">
		<h1>{{ msg }}</h1>
		<h2>Essential Links</h2>
		<ul>
			<li>
				<a href="https://vuejs.org" target="_blank">Core Docs</a>
			</li>
			<li>
				<a href="https://forum.vuejs.org" target="_blank">Forum</a>
			</li>
			<li>
				<a href="https://gitter.im/vuejs/vue" target="_blank">Gitter Chat</a>
			</li>
			<li>
				<a href="https://twitter.com/vuejs" target="_blank">Twitter</a>
			</li>
			<br>
			<li>
				<a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a>
			</li>
		</ul>
		<h2>Ecosystem</h2>
		<ul>
			<li>
				<a href="http://router.vuejs.org/" target="_blank">vue-router</a>
			</li>
			<li>
				<a href="http://vuex.vuejs.org/" target="_blank">vuex</a>
			</li>
			<li>
				<a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a>
			</li>
			<li>
				<a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'hello',
		data() {
			return {
				list: [{
					name: "模块1",
					background: "none",
					height: 200,
					modules: [{
						x: 100,
						y: 100,
						width: 200,
						height: 200,
						zIndex: 0,
						url: false,
						background: "none",
						type: "font",
						angle: 0,
						attr: { //字体需要双击模块可以修改字
							fontSize: "20",
							fontFamily: "微软雅黑",
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
						background: "none",
						url: false,
						angle: 0,
						type: "img", //图片模块更多的是裁剪操作  裁剪 水平翻转/垂直翻转 图片替换/图片交换 并且要裁剪里的裁剪选择器要和原本图片一样大 即等比例裁剪
						attr: {
							src: "xxx.png"
						}

					}, {
						x: 100,
						y: 100,
						width: 200,
						height: 200,
						zIndex: 0,
						background: "none",
						url: false,
						angle: 0,
						type: "table", //表格模块需要新增删除行列 然后双击可以修改某一块字 单击修改他的属性 
						attr: {
							data: {//这块你们看下 有更好的双向绑定设计
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
								td:[{	text: "值1",
									fontSize: "20",
									fontFamily: "微软雅黑",
									textCenter: "auto",
									color: "#fff"},{	text: "值2",
									fontSize: "20",
									fontFamily: "微软雅黑",
									textCenter: "auto",
									color: "#fff"}]
							}
						}

					},{
						x: 100,
						y: 100,
						width: 200,
						height: 200,
						zIndex: 0,
						background: "none",
						url: false,
						angle: 0,
						type: "select", //选择框就是生成
						attr: {
							style:"",//有多个风格可以选择
							values:["aaa","bbb","ccc"],
							select:"aaa"
						}

					}]
				}]
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h1,
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
</style>