<template>
	<section>
		<input v-model="new_todo" @keyup.enter="add_todo" placeholder="輸入待辦事項" />
		<button class="btn-add" @click="add_todo">新增</button>
		<ul>
			<li 
				v-for="(list, index) in todo_list" 
				:key="`list-${index}`"
			>
				{{ list }}
				<button class="btn-delete" @click="delete_todo(index)">
					刪除
				</button>
			</li>
		</ul>
	</section>
</template>

<script setup>
import { ref, reactive } from "vue";

const new_todo = ref("");
const todo_list = reactive([]);

const add_todo = () => {
	if (new_todo.value.trim() !== "") {
		todo_list.push(new_todo.value.trim());
		new_todo.value = "";
	}
};

const delete_todo = (index) => {
	todo_list.splice(index, 1);
};
</script>

<style scoped>
.btn-add {
	margin-left: 20px;
}

.btn-delete {
	margin-left: 20px;
}

ul {
	display: grid;
	gap: 20px;
}
</style>
