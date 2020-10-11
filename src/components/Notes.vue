<template>
<div class="hello">
    <div class="container">
        <h3>{{msg}}</h3>
        <div class="form">
            <div class="form-group">
                <div class="form-gorup">
                    <label>Note Title</label>
                    <input class="form-control" type="text" v-model="note.title">
                </div>
            </div>
            <div class="form-gorup">
                <label>Note text</label>
                <textarea class="form-control" name="name" rows="8" cols="80" v-model="note.text"></textarea>
            </div>
            <button class="btn btn-primary" @click="addNote">Add Note</button>
        </div>
    </div>

    <div class="col-md-8 offset-md-2">
        <div class="row">
            <NotesItem class="col-md-4 " v-for="(note, index) in notes" :key="index" :note="note" @deleteNote="removeNote">
            </NotesItem>
        </div>
    </div>
</div>
</template>

<script>
import NotesItem from './NotesItem.vue'
export default {
    name: 'Notes',
    components: {
        NotesItem
    },
    data: function () {
        return {
            note: {
                text: '',
                title: ''

            },
            notes: [{
                title: 'Note 1',
                text: 'Text of note 1',
                date: new Date(Date.now()).toLocaleString()
            }]
        }
    },
    methods: {
        addNote() {
            let {
                title,
                text
            } = this.note

            this.notes.push({
                title,
                text,
                date: new Date(Date.now()).toLocaleString()
            })
        },
        removeNote(index) {
            this.notes.splice(index, 1)
        }

    },
    props: {
        msg: String
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
