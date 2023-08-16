<template>
  <div>
    <span
      @click="deleteTask"
      class="bi bi-trash-fill ms-3"
    ></span>

    <span v-if="loading" class="spinner-border spinner-border-sm"></span>
  </div>
</template>

<script>
import { ref } from "vue";
import { useStore } from "vuex";

export default {
  props: ["id"],

  setup(props) {
    const store = useStore();
    const loading = ref(false);

    async function deleteTask() {
      loading.value = true;
      await store.dispatch("task/deleteTask", props.id);
      loading.value = false;
    }

    return {
      deleteTask,
      loading,
    };
  },
};
</script>

<style>
</style>