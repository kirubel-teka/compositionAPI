<template>
    <div class="com_num">
        <p>{{ num }}</p>
        <p>{{ double }}</p>
        <button type="button" @click.prevent="increment">Click Me</button>
        <p>{{ name }}</p>
        <p>
            <input type="text" v-model="phrase">
        </p>
        <p>{{ reversedPhrase }}</p>

        <app-alert :user="user"/>
    </div>
</template>

<script>
import { ref, reactive, toRefs, watchEffect, computed } from 'vue';
import AppAlert from "@/components/Alert.vue"

export default {
    name: 'composition',
    components: {
        AppAlert,
    },
    setup() {
        let num = ref(0);

        function increment() {
            num.value++;
        }

        const double = computed(() => {
            return num.value * 2;
        })
        
        const user = reactive({
            name: 'John',
            age: 20,
        });

         setTimeout(() =>{
            user.name = 'Chris';
         }, 3000);

         const phrase = ref("");
         const reversedPhrase = ref("");


        watchEffect(() => {
            reversedPhrase.value = phrase.value.split("").reverse().join("");
        })

        


        return {
            num,
            increment,
            ...toRefs(user),
            phrase,
            reversedPhrase, 
            double,
            user,
        }
    }
}
</script>

<style>
.com_num {
    position: fixed;
}
</style>