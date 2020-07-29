<template>
    <div class="question-box-container">
        <b-jumbotron>
            <template v-slot:lead>
                {{currentQuestion.question}}
            </template>

            <hr class="my-4">

            <p v-for="(answer, index) in answers" :key="index">
                
                {{ answer }}
            </p>

            <b-button variant="primary" href="#">Submit Button</b-button>
            <b-button @click="next" href="#">
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
    }
}
</script>