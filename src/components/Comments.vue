<script>
export default {
    data() {
        return {
            comments: [],
            comment: {
                name: '',
                comment: '',
                votes: 0,
            }
        }
    },
    methods: {
        addComment() {
            this.comments.push(this.comment);
            this.cleanPreviousComments()
        },
        cleanPreviousComments(){
            this.comment = {
                name: '',
                comment: '',
                votes: 0,
            }
        },
        voteComment(comment) {
            comment.votes++;
        }
    },
}
</script>
<template>
    <div>
    </div>
    <div class="comments">
        <ul>
            <li v-for="(comment, index) in comments">
                <span>{{ comment.name }}</span>
                <span>{{ comment.comment }}</span>
                <span>{{ comment.votes }}</span>
                <button @click="voteComment(comment)">vote</button>
            </li>
        </ul>
    </div>

    <div class="newVotter">
        <input v-model="comment.name" placeholder="Name">
        <input v-model="comment.comment" placeholder="Comment">
        <button @click="addComment()">Add</button>
    </div>
</template>

<style>
.wrapper {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;
}

li {
    list-style: none;
}

button {
    border: none;
    color: #000;
    font-size: 1rem;
    cursor: pointer;
}

input {
    border: none;
    border-bottom: 1px solid #000;
    padding: 0.5rem;
    width: 100%;
}

#newVotter {
    margin-top: 2rem;
}
</style>


