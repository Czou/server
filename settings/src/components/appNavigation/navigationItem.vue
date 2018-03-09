<template>
	<li :class="item.classes">

		<!-- Main link -->
		<a :href="(item.href) ? item.href : '#'">{{item.text}}</a>

		<!-- Popover, counter and button(s) -->
		<div v-if="item.utils" class="app-navigation-entry-utils">
			<ul>
				<li v-if="Number.isInteger(item.utils.counter)" class="app-navigation-entry-utils-counter">{{item.utils.counter}}</li>
				<li v-if="item.utils.menu" class="app-navigation-entry-utils-menu-button">
					<button></button>
				</li>
			</ul>
		</div>

		<!-- If the item has children, inject the component with proper data -->
		<ul v-if="item.children">
			<navigationItem v-for="(item, key) in item.children" :item="item" :key="key" />
		</ul>
	</li>
</template>

<script>
export default {
	name: 'navigationItem',
	props: ['item', 'key'],
	computed: {
	}
}
</script>
