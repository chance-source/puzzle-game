<template>
    <div>
        <h3>Records</h3>
        <!-- Update times -->
        <button class="update-button" @click="getRecords">Update</button>
        <!-- User times to be displayed -->
        <div v-for="(r, index) of records" :key="index">
            {{ index + 1 }} - {{ r.elapsedTime }} 
        </div>
    </div>    
</template>

<script>

export default {
    name: "Records-component",
    data(){
        return {
            // empy array for storing times logged by user
            records: [],
        }
    },
    created(){
        // once the component is created 
        // all previous times set by the user will be displayed automatically
        this.getRecords();

    },
    methods: {
        // method to obtain fastest time from local storage
        // returns an empty array if "records" isnt found
        getRecords(){
            const records = JSON.parse(localStorage.getItem('records')) || [];
            // reactive property set to localstoarge or default
            this.records = records;
        }

    }
}

</script>

<style scoped>
button.update-button {
    margin-bottom: 20px;
    border-radius: 25px;
    background-color: darkslategrey;
    border: none;
}
</style>