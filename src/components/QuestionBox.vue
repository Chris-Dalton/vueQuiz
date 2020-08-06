<template>
    <div class="question-box-container">
        <b-jumbotron>
            <template v-slot:lead>
                {{ currentQuestion.question }}
            </template>

            <hr class="my-4">

            
            <b-list-group 
            v-for="(answer, index) in answers" 
            :key="index">
                <b-list-group-item 
                v-on:click="selectAnswer(index)"
                :class="[selectedIndex === index ? 'selected' : '']"
                >
                
                    {{answer}}
                </b-list-group-item>
            </b-list-group>
                
            

            <b-button variant="primary" href="#">Submit Button</b-button>
            <b-button variant="success" @click="next" href="#">
                Next Question
            </b-button>

        </b-jumbotron>
    </div>
</template>

<script>
export default {
    props: {
        currentQuestion: Object,
        next: Function
    },
    data() {
        return {
            selectedIndex: null
        }
    },
    methods: {
        selectAnswer (index) {
            this.selectedIndex = index
    
        }
    },
    computed: {
    answers(){
        let answers = [...this.currentQuestion.incorrect_answers]
        answers.push(this.currentQuestion.correct_answer)
        return answers
    }
  },
  mounted() {
      console.log(this.currentQuestion)
    }
}
</script>
<style scoped>
    .list-group{
        margin-bottom: 5px;
    }
    .list-group-item:hover{
        background-color: #eee;
        cursor: pointer;
    }
    .btn {
        margin: 0 5px;
    }
    .selected{
        background-color: cyan;
        }
    .correct{
        background-color: green;
        }
    .incorrect{
        background-color: red;
        }
</style>