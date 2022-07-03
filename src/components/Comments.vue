
    <template style="position: relative; left: 10px; top: 100px;">
        <div>
    </div>
    <div class="comments">
        <ul class="list-group">
            <li v-for="(comment, index) in comments" class="list-group-item d-flex justify-content-between align-items-center">
                <span>{{ comment.name }}</span>
                <span>{{ comment.comment }}</span>
                <span class="badge bg-primary rounded-pill"> {{ comment.votes }}</span>   
                <button @click="voteComment(comment)" type="button" class="btn btn-default" aria-label="Left Align">
                    <span class="glyphicon glyphicon-circle-arrow-upt" aria-hidden="true">Vote</span>
                </button>
            </li>
        </ul>
    </div>

    <div class="newVotter">
        <input v-model="comment.name" placeholder="Name" class="campos">
        <input v-model="comment.comment" placeholder="Comment" class="campos">
        <button class="btn btn-secondary" @click="addComment()">Add</button>
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
    color: rgb(0,0,0);
    font-size: 16px;
    font-family: "Lucida Console", "Courier New", monospace;
    cursor: pointer;
    background: rgb(95, 62, 255);
    align: center;
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

.campos{
    border-radius: 10px;
    box-shadow: 1px 1px;
}
</style>

<script>
export default {
    data() {
        return {
            comments: [],
            comment: {
                name: ' ',
                comment: ' ',
                votes: ' 0 ',
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
                name: ' ',
                comment: ' ',
                votes: ' 0 ',
            }
        },
        voteComment(comment) {
            comment.votes++;
        }
    },
}
</script>
