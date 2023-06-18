<template>
  <main class="main">
    <section>
      <h1 class="title">Simple To-Do</h1>
      <div class="box-input">
        <label for="title" class="label-input">
          <span>
            <i class="fa-solid fa-pen fa-sm"></i>
            Título
          </span>
        </label>
        <FormTask @saveTask="saveTask" />
      </div>
    </section>
    <section class="section-main">
      <CardTask v-for="(task, index) in tasks" :key="index" :title="task.title" />
    </section>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CardTask from './components/CardTask.vue';
import ITask from './interfaces/ITask';
import FormTask from './components/Form.vue';

export default defineComponent({
  name: 'App',
  data() {
    return {
      tasks: [] as ITask[]
    }
  },
  components: {
    CardTask,
    FormTask
  },
  methods: {
    saveTask(title: string) {
      this.tasks.push({
        title
      })
    }
  }
});
</script>

<style>
  .main {
    display: flex;
    flex-direction: column;
    padding-top: 3rem;
    align-items: center;
    height: 100vh;
    background-color: "#f4f4f4";
    overflow-y: hidden;
    font-style: darkBlue;
  }
  .section-main {
    width: 40rem;
    max-width: 50rem;
  }
  .title {
    font-size: 2rem;
    text-align: center;
  }
  .box-input {
    display: flex;
    flex-direction: column;
    gap: .3rem;
  }
  .label-input {
    font-size: 1.5rem;
  }
</style>
