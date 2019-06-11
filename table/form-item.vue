<template>
	<td>
		<slot :row = 'row' :index = 'index'>{{ getVal() }}</slot>
	</td>
</template>

<script>
	export default{
		props: {
			prop: {
				
			},
			name: {
				
			}
		},
		data() {
			return {
				len: 0,
				index: 0,
				row: {}
			}
		},
		computed:{
			
		},
		methods:{
			getVal() {
				let list = this.$parent.list
				let index = this.getIndex()
				let rate = this.len / list.length
				//console.log()
				//console.log(this.prop)
				this.index = parseInt(index/rate)
				this.row = list[this.index]
				return this.row[this.prop]
			},
			getIndex() {
				let index = 0
				let uid = this._uid
				//console.log(this._uid)
				let childs = this.$parent.$children
				this.len = childs.length
				for (let i = 0; i < childs.length; ++i) {
					if (childs[i]._uid == uid) {
						console.log(i)
						return i
						break;
					}
				}
			}
		},
		mounted() {
			//console.log(this.$parent)
		}
	}
</script>

<style>
</style>
