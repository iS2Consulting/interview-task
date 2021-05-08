<template>
	<div>
		<InputBar 
			v-model="newTodoText"
			placeholder="New todo"
			@keydown.enter="addTodo"
		/>
		<button_add @click="addTodo">ADD</button_add>
		<ul v-if="todos.length">
			<ListItem
				v-for="todo in todos"
				v-if="!todo.done"
				:key="todo.id"
				:todo="todo"
				@remove="isDone"
			/>
		</ul>
		<p v-else>
			Nothing left in the list. Add a new todo in the input above.
		</p>
		<ul v-if="todos.length">
			<ListItem
				v-for="todo in todos"
				v-if="todo.done"
				:key="todo.id"
				:todo="todo"
				@remove="isNotDone"
			/>
		</ul>
		<p v-else>
			Nothing done so far, don't be lazzy!
		</p>
	</div>
</template>

<script>
import InputBar from './InputBar.vue'
import ListItem from './ListItem.vue'

let nextTodoId = 1

export default {
	components: {
		InputBar, ListItem
	},
  data () {
    return {
			newTodoText: '',
      todos: [
				{
					id: nextTodoId,
					text: 'Sell InSign licenses',
					done: false,
					nextTodoId: nextTodoId++
				},
				{
					id: nextTodoId,
					text: 'Practice consulting in front of the mirror',
					done: false,
					nextTodoId: nextTodoId++
				}
			]
    }
  },
	methods: {
		addTodo () {
			const trimmedText = this.newTodoText.trim()
			if (trimmedText) {
				this.todos.push({
					id: nextTodoId++,
					text: trimmedText,
					done: false
				})
				this.newTodoText = ''
			}
		},

		isDone (Todo) {
			Todo.done = true
		},

		isNotDone (Todo) {
			Todo.done = false
		}

	}
}

</script>

<style>
	button_add {
    background-color: #1dcaff;
    border: 1px solid  #1dcaff;
    positioning: absolute;
bottom: 0px;

}
			
			</style>