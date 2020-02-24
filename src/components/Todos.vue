<template>
  <div>
    <h3>Todos</h3>
    <div class="todos">
      <div class="todo" v-for="todo in allTodos" :key="todo.id">
				{{ todo.title }}
				<i class="fas fa-trash" @click="deleteTodo(todo)"></i>
			</div>
		</div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo"])
	},
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}

.todo {
  border: 1px solid white;
  background: lightblue;
  border-radius: 5px;
  padding: 1rem;
  text-align: center;
  position: relative;
  cursor: pointer;
}

i {
	position: absolute;
	bottom: 10px;
	right: 10px;
	cursor: pointer;
}
</style>