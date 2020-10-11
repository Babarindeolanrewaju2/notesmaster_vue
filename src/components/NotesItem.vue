<template>
<div>
    <div class="card">
        <button class="close" @click="remove_Note(index)">&times;</button>
        <div class="card-block">
            <h4 class="card-title">{{note.title}}</h4>
            <h6 class="card-subtitle mb-2 text-muted">{{note.date}}</h6>
            <p class="card-text">{{note.text}}</p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'NotesItem',
    props: ["note"],
    methods: {
        remove_Note(item) {
            this.$emit('deleteNote', item)
        }
    }
}
</script>
