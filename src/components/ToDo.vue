<template>
  <v-app>
    <v-subheader><h1>Todo app</h1></v-subheader>
    <v-card>
      <v-input label="Enter task">
        <input type="text" v-on:keyup.13="enter_task" v-model="new_task"><br/>
        <h1>{{ new_task}}</h1>
      </v-input>
    </v-card>
    <h1>The tasks are:</h1>
      <ol>
        <li v-for="(task, index) in task_list">
          <h2 v-on:click="remove_task(index)">{{ task }}</h2>
        </li>
      </ol>
    <v-card>
      <h1>The completed tasks are:</h1>
      <ol>
        <li v-for="task in completed_list">
          <h2>{{ task }}</h2>
        </li>
      </ol>
    </v-card>
  </v-app>

</template>

<script>
    export default {
        name: "ToDo",

        data () {
          return {
            new_task: '',
            task_list: [],
            completed_list: []
          };
        },

        methods: {
          enter_task: function() {

            if (this.new_task.trim().length>0) {
              this.task_list.push(this.new_task);
              this.new_task="";
            }
          },

          remove_task: function(index) {
            this.completed_list.push(this.task_list[index]);
            this.task_list.splice(index, 1);
          }
        }
    }
</script>
