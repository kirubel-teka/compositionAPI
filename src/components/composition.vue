<template>
    <div class="com_num">
        <p>{{ num }}</p>
        <button type="button" @click.prevent="increment">Click Me</button>
        <p>{{ name }}</p>
    </div>
</template>

<script>
import { ref, reactive, toRefs } from 'vue';

export default {
    name: 'composition',
    setup() {
        let num = ref(0);

        function increment() {
            num.value++;
        }
        
        const user = reactive({
            name: 'John',
            age: 20,
        });

         setTimeout(() =>{
            user.name = 'Chris';
         }, 3000);

        return {
            num,
            increment,
            ...toRefs(user),
        }
    }
}
</script>

<style>
.com_num {
    position: fixed;
}
</style>