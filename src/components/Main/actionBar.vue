<template>
	<div >
		<a v-on:click="up">向上</a>
		<a >向下</a>
		<a >插入到前面</a>
		<a > 插入到后面</a>
		<a > 删除</a>
		<a > 编辑属性</a>
		<div>
			高度 <input type="text" v-model="result.height" />
			背景颜色  <input type="color" v-model="result.background" />
			名称 <input type="text" v-model="result.name" />
		</div>
		
	</div>
</template>

<script>
	export default {
		name: 'actionBar',
		props: ["result","index"],
		data() {
			return {
			}
		},
		methods:{
			up(){
				this.$emit('actionBar',{index:this.index});
			}
		}
	}
</script>