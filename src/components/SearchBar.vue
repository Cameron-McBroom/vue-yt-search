<template>
    <div class="input-group mb-3">
        <div class="input-group-prepend">
            <span class="input-group-text" id="inputGroup-sizing-default">Search Youtube</span>
        </div>
        <input type="text" class="form-control" @input="onInput"/>
    </div>
</template>


<script>
import debounce from 'lodash/debounce' 
export default {
    name: 'SearchBar',
    methods: {
        onInput: debounce(function (e) {
            // Send the data to the parent to share with other components
            this.$emit('newSearch', e.target.value)
        }, 1000)
    }
};
</script>


<style scoped>

    div.input-group {
        margin-top: 20px;
    } 

</style>
