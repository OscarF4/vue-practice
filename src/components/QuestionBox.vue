<template>
    <div>
        <b-jumbotron class="py-4">
            <template #lead>
            Some question here?
            </template>

            <hr class="my-4">

            <p>
            {{ questions }}
            </p>

            <b-button variant="primary">Submit</b-button>
            <b-button variant="success">Next</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
export default {
    props: {
        questions: Array
    }
}
</script>