<template>
    <div class="row">
        <div class="col-md-3">
            <div class="btn-group">
                <button type="button" class="btn btn-secondary">Ordered By: {{ direction === 'desc' ? 'Descending' : 'Ascending' }}</button>
                <button type="button" class="btn btn-secondary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    <span class="sr-only">Toggle Dropdown</span>
                </button>
                <div class="dropdown-menu">
                    <h6 class="dropdown-header">Sorting Options</h6>
                    <a class="dropdown-item" href="#" v-on:click="changeDirection('asc')">Ascending</a>
                    <a class="dropdown-item" href="#" v-on:click="changeDirection('desc')">Descending</a>
                </div>
            </div>
        </div>
        <div class="col-md-9">
            <div class="form-group">
                <input type="text" class="form-control" id="search-field" v-model="query" v-on:keyup.enter="submit" placeholder="Search a Product">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'filter-component',
    data () {
        return {
            query: '',
            direction: 'asc',
        }
    },
    methods: {
        changeDirection: function(i) {
            this.direction = i
        },
        submit: function() {
            if(this.query.length === 0) {
                return
            }

            this.$emit('query', this.query)
            this.$emit('direction', this.direction)
        }
    },
}
</script>
