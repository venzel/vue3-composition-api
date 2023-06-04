<template>
    <hr />
    <div>message: {{ getMessage }}</div>
    <hr />
    <button @click="sendMessage">Emit Message</button>
</template>

<script>
import { computed } from 'vue';

export default {
    name: 'Message',
    props: {
        message: {
            type: String,
            required: false,
            default: 'Default message',
        },
    },
    emits: ['messageEmited'],
    setup(props, { emit }) {
        const getMessage = computed(() => props.message + ' ok');

        const sendMessage = () => {
            emit('messageEmited', props.message + ' emited');
        };

        return {
            getMessage,
            sendMessage,
        };
    },
};
</script>
