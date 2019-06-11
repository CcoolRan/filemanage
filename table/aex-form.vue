<template>
	<div>
		<div class="tab-t">
			<table cellpadding="0" cellspacing="0">
				<colgroup>
					<col style="width: 80px;"></col>
					<col style="width: 200px;"></col>
				</colgroup>
				<tr>
					<td v-for="item in tList">{{ item }}</td>
				</tr>
			</table>
			<input type="hidden" :value = 'getTList'>
		</div>
		<div class="tab-con">
			<table cellpadding="0" cellspacing="0">
				<colgroup>
					<col style="width: 80px;"></col>
					<col style="width: 200px;"></col>
				</colgroup>
				<!-- <thead>
					<tr>
						<td v-for="item in tList">{{ item }}</td>
					</tr>
				</thead> -->
				<tr v-for="item in list">
					<slot></slot>
				</tr>
			</table>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			list: {
				
			}
		},
		data() {
			return {
				a: 123,
				tList: []
			}
		},
		computed:{
			getTList() {
				this.$nextTick(()=>{
					let childs = this.$children
					let cLen = childs.length
					let len = this.list.length
					let rowLen = cLen / len
					for (let i = 0; i< rowLen; ++i) {
						this.tList.push(childs[i].name)
					}
				})
				return true
			}
		},
		methods:{
			
		},
		mounted() {
			console.log(this.$children[0])
		}
	}
</script>

<style>

	.tab-con table,.tab-t table{
		width: 100%;
	}
	.tab-con table td,.tab-t table td{
		border: thin solid #ccc;
		padding: 10px 0;
		box-sizing: border-box;
	}
</style>
