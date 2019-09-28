<template>
	<div>
<!--		<button v-on:click="fetchTodoItems">get all</button>-->
		<ul>
			<li v-for="(todoItem, index) in items" v-bind:key="index">
				{{ todoItem }}
				<button v-on:click="removeTodoItem(todoItem, index)">remove</button>
			</li>
		</ul>
	</div>
</template>

<script>

	export default {
		props: [ 'items' ],
		methods: {
			removeTodoItem: function (todoItem, index) {
				this.$emit("removeItem", todoItem, index);
			}
		}
	}
</script>