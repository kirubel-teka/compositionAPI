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
        <button type="button" ref="btn">Button</button>
    </div>
</template>

<script>
import { ref, reactive, toRefs, onMounted } from 'vue';
import AppAlert from "@/components/Alert.vue";
import { useNumber } from "@/hooks/number";
import { usePhrase } from "@/hooks/phrase";

export default {
    name: 'composition',
    components: {
        AppAlert,
    },
    setup() {
        const btn = ref(null);

        onMounted(() => {
            btn.value.addEventListener("click", () => {
                console.log("Button clicked");
            })
        })

       
        
        const user = reactive({
            name: 'John',
            age: 20,
        });

         setTimeout(() =>{
            user.name = 'Chris';
         }, 3000);


        
        const { num, increment, double  } = useNumber();
        const { phrase, reversedPhrase } = usePhrase();


        return {
            num,
            increment,
            ...toRefs(user),
            phrase,
            reversedPhrase, 
            double,
            user,
            btn,
        }
    }
}
</script>

<style>
.com_num {
    position: fixed;
}
</style>