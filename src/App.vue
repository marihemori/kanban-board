<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <b-form-input
          v-model="newTask"
          placeholder="Enter task"
          @keyup.enter="add"
        ></b-form-input>
        <b-button class="ml-2" variant="primary" @click="add">Add</b-button>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>Backlog</h3>
          <draggable class="list-group kanban-column" :list="arrBacklog" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrBacklog"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>In Progress</h3>
          <draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrInProgress"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>Tested</h3>
          <draggable class="list-group kanban-column" :list="arrTested" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrTested"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
          <draggable class="list-group kanban-column" :list="arrDone" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrDone"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: "App",
  components: {
    draggable,
  },
  data() {
    return {
      newTask: "",
      arrBacklog: [
        { name: "Study" },
        { name: "Going to the market" },
        { name: "Clean the house" }
      ],
      arrInProgress: [],
      arrTested: [],
      arrDone: [],
    };
  },
  methods: {
    add() {
      if (this.newTask) {
        this.arrBacklog.push({ name: this.newTask });
        this.newTask = "";
      }
    },
  },
};
</script>

<style>
.kanban-column {
  min-height: 300px;
}
</style>
