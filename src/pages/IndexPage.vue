<template>
  <q-page class="flex flex-center">
    <q-card class="my-card" style="width: 600px">
      <q-card-section>
        <div class="text-h4">TO-DO List</div>
      </q-card-section>
      <q-card-section>
        <div class="row justify-center">
          <div class="col-12">
            <q-input v-model="todoTask" label="Input Task">
              <template v-slot:after>
                <q-btn round dense flat icon="send" @click="addItem" />
              </template>
            </q-input>
          </div>
        </div>
      </q-card-section>
      <q-card-section v-if="todoList.length > 0">
        <div
          class="row justify-center"
          v-for="(item, index) in todoList"
          :key="index"
        >
          <div class="col-8 q-py-md">
            {{ item.value }}
          </div>
          <div class="col-auto q-py-md">
            <q-btn round dense flat icon="done" @click="deleteTodo(index)" />
          </div>
        </div>
      </q-card-section>
      <q-card-section v-else>
        <div class="row justify-center">
          <div class="col-12">
            <div class="text-h6">No items in the list</div>
          </div>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const todoList = ref([
      { value: "create an app" },
      { value: "Build an app" },
    ]);
    const todoTask = ref("");

    //methods
    const addItem = () => {
      todoList.value.push({ value: todoTask.value });
    };
    const deleteTodo = (index) => {
      todoList.value.splice(index, 1);
    };
    return {
      todoList,
      todoTask,
      addItem,
      deleteTodo,
    };
  },
};
</script>
