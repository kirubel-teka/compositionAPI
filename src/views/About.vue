<template>
    <div class="about">
      <h1>{{ $route.params.member }}</h1>
      <p>{{ store.counter }}</p>
      <p>{{ store.doubleCount }}</p>
      <button type="button" @click.prevent="increment">Press me!</button>
    </div>
  </template>
<script>
import { useRoute, useRouter } from 'vue-router';
import { useCounterStore } from '@/stores/counter';

export default {
    setup() {
        const route = useRoute();
        const router = useRouter();

        console.log(route.params.member);

        router.push({
            hash: '#test',
        })

        return { store };
    }
}

</script>
  