<template>
	<div class="main" id="main">
		<ul class="preview">
			<li v-for="(t ,i) in list"  v-on:click="viewPanto(i)">
				<div >
		<a v-on:click="moduleUp(i)">向上</a>
		<a  v-on:click="moduleDown(i)">向下</a>
		<!--<a >插入到前面</a>
		<a > 插入到后面</a>
		<a > 删除</a>
		<a >添加组件</a>-->
		<a > 编辑属性</a>
		<div>
			高度 <input type="text" v-model="t.height" />
			背景颜色  <input type="color" v-model="t.background" />
			名称 <input type="text" v-model="t.name" />
		</div>
		
	</div>
				<div v-bind:style="{ height: t.height+'px', background:t.background }" class="c-module">
					
					<template v-for="tt in t.modules">
						<module  v-bind:result="tt"></module>
					</template>
				</div>
			</li>
		</ul>
		<ul id="J_view">
			<li v-for="t  in list">
				<div v-bind:style="{ height: t.height+'px', background:t.background }" class="c-module">
					{{t.name}}

					<template v-for="tt in t.modules">
						<module v-on:myChild="toFatherSay" v-bind:result="tt"></module>
					</template>

				</div>
			</li>
		</ul>
		<div id="info">
			<li v-for="t  in list">
				<template v-for="tt in t.modules">
					<moduleInfo v-bind:result="tt"></moduleInfo>
				</template>
		</div>
	</div>
	</div>
</template>

<script>import module from './Main/module/module'
import moduleInfo from './Main/module/Info'
import actionBar from './Main/actionBar'
import $ from 'jquery'
export default {
	name: 'cmain',
	components: {
		module,
		moduleInfo,
		actionBar
	},
	methods: {
		toFatherSay: function(massage) { // mychlid事件触发调用的方法
			this.list.forEach(function(t, i) {
				t.modules.forEach(function(tt, ii) {
					tt.current = false;
				})
			})
		},
		moduleUp: function(i) {
			if(i == 0) {
				console.log("第一个无法再往上");
			} else {
				var _tem = this.list[i - 1];
				var _tem1 = this.list[i];
				this.list.splice(i, 1, _tem)
				this.list.splice(i - 1, 1, _tem1)
			}

		},
		moduleDown: function(i) {
			console.log(i)
			if(i == this.list.length) {
				console.log("最后一个无法向下");
			} else {
				var _tem = this.list[i +1];
				var _tem1 = this.list[i];
				this.list.splice(i, 1, _tem)
				this.list.splice(i + 1, 1, _tem1)
			}

		},
		
		viewPanto: function(index) {

			let scroll = 0;
			for(var i = 0; i < index; i++) {
				scroll += this.list[i].height
			}
			console.log(scroll)
			this.scroll = scroll;
		}

	},
	watch: {
		scroll(newValue) {
			$("#J_view").stop().animate({
				scrollTop: newValue + 'px'
			}, 800);
		}
	},
	data() {
		return {
			scroll: 0,
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
						text: "我叫林彬彬",
						textCenter: "auto",
						color: "#fff",
						other: {
							bold: false, //加粗
							italic: false, //斜体
							lineThrough: false,
							underline: false //下划线
						}
					},
					current: false
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
					},
					current: false
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
					},
					current: false
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
					},
					current: false
				}]
			}, {
				name: "模块2",
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
						text: "我叫林彬彬",
						textCenter: "auto",
						color: "#fff",
						other: {
							bold: false, //加粗
							italic: false, //斜体
							lineThrough: false,
							underline: false //下划线
						}
					},
					current: false
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
					},
					current: false
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
					},
					current: false
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
					},
					current: false
				}]
			}, {
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
						text: "我叫林彬彬",
						textCenter: "auto",
						color: "#fff",
						other: {
							bold: false, //加粗
							italic: false, //斜体
							lineThrough: false,
							underline: false //下划线
						}
					},
					current: false
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
					},
					current: false
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
					},
					current: false
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
					},
					current: false
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
}

.main ul {
	height: 900px;
	overflow-y: scroll;
	overflow-x: hidden;
	width: 600px;
	float: left;
}

.preview .c-module {
	/*  position: absolute;*/
	transform: scale(0.3);
}</style>