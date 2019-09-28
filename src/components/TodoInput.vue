<template>
	<div>
		<input type="text" v-model="inputText" v-on:keyup.enter="addTodo">
		<button v-on:click="addTodo">add</button>
		<h1>TodoInput</h1>
	</div>
</template>

<script>

	export default {
		data: function () {
			return {
				inputText: ''
			}
		},
		methods:{
			addTodo: function () {
				if( this.inputText.trim() === '')
					return;
				this.$emit('addItem', this.inputText);
				this.clearInput();
			},
			clearInput: function () {
				// console.log(this);
				this.inputText = '';
			}
		}
	}

</script>