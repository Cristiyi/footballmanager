<template>
    <div>
        <complex-table></complex-table>
    </div>
</template>

<script type="text/javascript">
    import complexTable from '@/views/table/complex-table'
    import axios from 'axios'
    export default {

        components: {
            complexTable
        },

        data() {
            return {
                league: []
            }
        },

        methods: {

            getLeague() {
                axios.get('/api/admin/league/get_all').then(this.getLeagueSucc)
            },
            getLeagueSucc(res) {
                console.log(res.data)
                let result = res.data
                if(result.status == 1&&result.data) {
                    this.league = result.data;
                }
            }

        },

        mounted() {
            this.getLeague();
            console.log(this.league)
        }

    }

</script>
