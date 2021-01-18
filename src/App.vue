<template>
  <div class="container mt-5">
    <div class="flex justify-center">
      <div class="row">
        <div class="col form-inline">
          <b-form-input v-model="newTask" placeholder="Insert New Task" @keyup.enter="add"></b-form-input>
          <b-button class="ml-2" variant="primary" @click="add">Add</b-button>
        </div>
      </div>
      <div></div>

      <div class="row">
        <b-card-group deck class="mt-3 pl-3">
          <div class="col-md-3 px-0">
            <b-card class="mb-3 p-1 alert alert-danger">
              <b-card-header class="pb-1 mt-1 mb-3">
                <h3>Backlog</h3>
              </b-card-header>
              <b-card-body class="p-0 m-0">
                <draggable class="list-group kanban-column" :list="arrBacklog" group="tasks">
                  <div class="list-group-item" v-for="element in arrBacklog" :key="element.name">
                    {{element.name}}
                  </div>
                </draggable>
              </b-card-body>
            </b-card>
          </div>

          <div class="col-md-3 px-0">
            <b-card class="mb-2 p-1 alert alert-primary">
              <b-card-header class="pb-1 mt-1 mb-3">
                <h3>In Progress</h3>
              </b-card-header>
              <b-card-body class="p-0">
                <draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
                  <div class="list-group-item" v-for="element in arrInProgress" :key="element.name">
                    {{element.name}}
                  </div>
                </draggable>
              </b-card-body>
            </b-card>
          </div>

          <div class="col-md-3 px-0">
            <b-card class="mb-2 p-1 alert alert-warning">
              <b-card-header class="pb-1 mt-1 mb-3">
                <h3>Tested</h3>
              </b-card-header>
              <b-card-body class="p-0">
                <draggable class="list-group kanban-column" :list="arrTested" group="tasks">
                  <div class="list-group-item" v-for="element in arrTested" :key="element.name">
                    {{element.name}}
                  </div>
                </draggable>
              </b-card-body>
            </b-card>
          </div>

          <div class="col-md-3 px-0">
            <b-card class="mb-2 p-1 alert alert-success">
              <b-card-header class="pb-1 mt-1 mb-3">
                <h3>Completed</h3>
              </b-card-header>
              <b-card-body class="p-0">
                <draggable class="list-group kanban-column" :list="arrCompleted" group="tasks">
                  <div class="list-group-item" v-for="element in arrCompleted" :key="element.name">
                    {{element.name}}
                  </div>
                </draggable>
              </b-card-body>
            </b-card>
          </div>
        </b-card-group>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: 'App',
  components: {
    draggable
  },
  data() {
    return {
      newTask: "",
      arrBacklog: [
        {name: "Code Welcome Page"},
        {name: "Code Login Page"},
        {name: "Code Product Listing Page"},
        {name: "Style Welcome Page"},
        {name: "Test Website"}
      ],
      arrInProgress: [],
      arrTested: [],
      arrCompleted: []
    }
  },
  methods: {
    add() {
      if(this.newTask) {
        this.arrBacklog.push({name: this.newTask});
        this.newTask = "";
      }
    }
  }
}
</script>

<style>
  .cards {
    padding:.5rem;
  }

  .kanban-column {
    min-height: 600px;
  }
</style>
