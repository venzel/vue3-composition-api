<template>
    <div>
        <div>Name: {{ user.name }}</div>
        <div>Hobbies: {{ hobbies }}</div>
        <button @click="changeName('Tiago Campos')">Change Name</button>
        <Message @messageEmited="changeMessageEmited" :message="user.name" />
        <div>message emited: {{ msgEmited }}</div>
    </div>
</template>

<script>
import { ref, watch, computed } from 'vue';
import Message from './Message.vue';

export default {
    name: 'Member',
    components: { Message },
    setup() {
        const user = ref({
            name: 'Tiago Rizzo',
            age: 20,
            hobbies: ['Sports', 'Cooking'],
        });

        const msgEmited = ref('');

        watch(
            () => user.value.name,
            (value) => {
                console.log('Name changed to: ' + value);
            }
        );

        const changeName = (name) => {
            user.value.name = name;
        };

        const hobbies = computed(() => user.value.hobbies.join(', '));

        const changeMessageEmited = (dataEmited) => {
            msgEmited.value = dataEmited;
        };

        return {
            user,
            msgEmited,
            hobbies,
            changeName,
            changeMessageEmited,
        };
    },
};
</script>
