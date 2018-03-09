<template>
	<div id="app">
		<appNavigation :menu="menu" />
		<div id="app-content">
			<span :class="{ 'icon-loading': loading }">
				<h1>Users</h1>
				<button @click="addItem">+</button>
				<div>{{users}}</div>
			</span>
		</div>
	</div>
</template>

<script>
import appNavigation from '../components/appNavigation'

export default {
	name: 'Users',
	components: {
		appNavigation
	},
	created: function () {
		this.$store.dispatch('getUsers');
	},
	data: function () {
		return {
			menu: {
				items: [
					{text: 'Test', href:'#test', children:[{text: 'Test1', href:'#test1'}]}
				]
			}
		}
	},
	computed: {
		users() {
			return this.$store.getters.getUsers
		},
		loading() {
			return Object.keys(this.users).length === 0;
		}
	},
	methods: {
		addItem: function() {
			this.menu.items.push({
				text: 'Test'+parseInt(Math.random()*10), href:''
			});
		}
	},
}
</script>

<style lang="scss">
</style>
