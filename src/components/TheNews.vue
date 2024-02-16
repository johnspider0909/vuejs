<script>
const API_URL = `https://newsapi.org/v2/everything?q=apple&from=2024-01-17&to=2024-01-17&sortBy=popularity&apiKey=c64b7bda3f6a4855ba2baf6d5258452b`

export default {
    name: "TheNews",
    data: () => ({
        branches: ['main', 'v2-compat'],
        currentBranch: 'main',
        commits: null
    }),
    
    created(){
        // fetch on init
        this.fetchData()
    },

    watch: {
        currentBranch: 'fetchData'
    },

    methods: {
        async fetchData(){
            const url = `${API_URL}${this.currentBranch}`
            this.commits = await (await fetch(url)).json()
        },
        truncate(v) {
            const newline = v.indexOf('\n')
            return newline > 0 ? v.slice(0, newline): v
        },
        formatDate(v){
            return v.replace(/T|Z/g, '')
        }
    }
}
</script>

<template>
    <h1>Latest Tesla News</h1>

    <template v-for = "branch in branches">
            <input type="radio"
        :id="branch"
        :value="branch"
        name="branch"
        v-model="currentBranch">
        <label :for="branch">{{ branch }}</label>
  <p>vuejs/vue@{{ currentBranch }}</p>

            <ul>
                <li v-for="{ status } in commits">
                    <span> {{status}}</span>
                    
                </li>
            </ul>
            

    </template>

</template>