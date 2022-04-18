<template>
	<div class="todo-wrapper">
		<form @submit.prevent class="todo-form">
			<input
				v-model="task"
				type="text"
				placeholder="Напиши задачу"
			/>
			<button @click="addTask(task)">
				Добавить
			</button>
		</form>
		<div class="task-item" v-for="(task, index) in tasks" :key="task.id">

			<div :class="{ checked: tasks[index].checked }">
				{{ task.text }}
			</div>

			<div class="task-item__control">
				<checkbox :test="tasks[index]" class=checkbox>
				</checkbox>
				<button
					@click="deleteTask(index)"
					class="task-item__delete"
				>
				</button>
			</div>
		</div>
	</div>
</template>

<script>
import Checkbox from '@/components/Checkbox'

export default {
	components: { Checkbox },
	data() {
		return {		
			task: '',
			tasks: [
				{
					text: "Посмотреть мой гитхаб",
					checked: false
				},
				{
					text: "Написать еще одну задачу",
					checked: false
				}
			],
		}
	},
	methods: {
		addTask(task) {
			if(task === '')
				return;
			this.tasks.push(
				{
					text: task,
					checked: false
				}
			);
			this.task='';
		},
		deleteTask(index) {
			this.tasks.splice(index, 1);
		}
	}
}
</script>

<style scoped lang="scss">
	.todo-wrapper {
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: stretch;
	}
	.todo-form {
		display: flex;
		justify-content: space-between;
		input {
			flex: 1 0 0;
		}
		margin-bottom: 15px;
	}
	.task-item {
		display: flex;
		justify-content: space-between;
		text-align: center;
		padding: 10px 5px;
		border: solid 1px #f7cb15;
		border-radius: 5px;
		margin-bottom: 5px;
		.checked {
			text-decoration: line-through;
		}
	}
	.task-item__control {
		display: flex;
		.checkbox {
			right: 50px;
			top: -16px;
		}
	}
	.task-item__delete {
		background-image: url('/src/assets/trash-solid.svg');
		background-repeat: no-repeat;
		background-position: center;
		background-size: contain;
		border: none;
		 background-color: transparent;
	}
</style>