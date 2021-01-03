<template>
    <div>
        <div class="list-group">
            <template v-for="chat in chatList">
                <ChatListItem
                    :chat="chat"
                    @click="itemClick"
                    v-bind:key="chat.id"
                />
            </template>
        </div>
    </div>
</template>
<script>
import ChatListItem from './ChatListItem';

export default {
    props: ['chatList'],
    methods: {
    },
    components: {
        ChatListItem
    }
}
</script>