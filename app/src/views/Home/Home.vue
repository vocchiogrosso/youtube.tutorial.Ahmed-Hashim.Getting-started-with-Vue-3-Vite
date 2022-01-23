<template>
  <div>
    <h1 class="mb-6 font-extrabold text-3xl">Home</h1>
    <p class="mb-6">Stored Name: {{ name }}</p>

    <input v-model="newName" class="p-2 mr-4 border rounded border-gray-600" type="text"/>
    <button @click="saveName" class="p-2 text-white bg-indigo-600 rounded ">Submit</button>
  </div>
</template>

<script setup>
  import { computed, ref } from 'vue';
  import { useStore } from 'vuex';
  import { useRouter } from 'vue-router';
  
  const router = useRouter();
  const store = useStore();

  const name = computed(()=>{
    return store.state.user.name
  });
  const newName = ref('');
  function saveName(){
    store.dispatch('saveName', newName.value);
    newName.value="";
    router.push('/about');
  }
</script>
