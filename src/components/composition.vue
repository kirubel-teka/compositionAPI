<template>
    <div class="com_num">
        <p>{{ num }}</p>
        <button type="button" @click.prevent="increment">Click Me</button>
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    name: 'composition',
    setup() {
        let num = ref(0);

        function increment() {
            num.value++;
        }

        return {
            num,
            increment,
        }
    }
}
</script>

<style>
.com_num {
    position: fixed;
}
</style>