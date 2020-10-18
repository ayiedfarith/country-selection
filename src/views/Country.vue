<template>
<div>
    <b-row class="d-flex justify-content-center">
        <b-col cols="3">
            <b-form-select v-model="selectedCountry" :options="countries" value-field="alpha3Code" text-field="name">
            </b-form-select>
        </b-col>
    </b-row>

    <b-row class="mt-5 d-flex justify-content-center">
        {{ selectedCountry }}
    </b-row>

    <b-row class="mt-5 d-flex justify-content-center" v-if="selectedCountry === 'MYS'">
        Hidup Malaysia!
    </b-row>
</div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            countries: [],
            selectedCountry: '',
        }
    },

    created() {
        this.loadAllCountries()

    },

    methods: {
        loadAllCountries() {
            axios.get('https://restcountries.eu/rest/v2/all')
                .then(respond => {

                    this.countries = respond.data
                })
                .catch(err => {
                    console.log(err)
                })

        }
    },

}
</script>

<style lang="stylus" scoped>

</style>
