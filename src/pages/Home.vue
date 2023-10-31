<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input
        v-model="newTask"
        @keyup.enter="addTask"
        class="col"
        square
        filled
        dense
        bg-color="white"
        placeholder="Inserir tarefa"
      >
        <template v-slot:append>
          <q-btn @click="addTask" round dense color="primary" label="Adicionar" />
        </template>
      </q-input>
    </div>
    <q-list class="bg-white" separator bordered>
      <q-item
        v-for="(task, index) in tasks"
        :key="task.title"
        @click="task.done = !task.done"
        :class="{'done bg-blue-1': task.done}"
        clickable
        v-ripple
      >
        <q-item-section avatar>
          <q-checkbox v-model="task.done" class="no-pointer-events" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label :class="{'done-task': task.done}">{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn
            @click.stop="deleteTask(index)"
            flat
            round
            dense
            color="red"
            icon="delete"
          />
        </q-item-section>
      </q-item>
    </q-list>
    <div v-if="!tasks.length" class="no-tasks absolute-center">
      <q-icon size="50px" :color="primary" name="error" />
      <div class="text-h5 text-primary text-center">Nenhuma tarefa adicionada</div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HomePage',
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    deleteTask(index) {
      this.$q
        .dialog({
          title: 'Confirmar',
          message: 'Deseja deletar?',
          cancel: true,
          persistent: true,
        })
        .onOk(() => {
          this.tasks.splice(index, 1);
          this.$q.notify('Tarefa eliminada');
        });
    },
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({
          title: this.newTask,
          done: false,
        });
        this.newTask = '';
        this.$q.notify('Tarefa adicionada');
      } else {
        this.$q.notify('A tarefa não pode estar em branco', 'negative');
      }
    },
  },
});
</script>

<style lang="scss">
.done-task {
  text-decoration: line-through;
  color: #bbb;
}

.no-tasks {
  opacity: 0.5;
}
</style>
