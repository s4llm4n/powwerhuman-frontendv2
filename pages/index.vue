<template>
    <section class="py-[200px] flex flex-col items-center justify-center px-4">
        <div class="text-[32px] font-semibold text-dark mb-4">Select Companies</div>
        <form class="w-full card">
            <div class="form-group">
                <label for="" class="text-grey">Companies</label>
                <select v-if="companies.data"
                    v-model="selectedCompany" 
                    name="companies" 
                    id="" 
                    class="apperance-none input-field form-icon-chevron_down"
                >
                    <option :value="company.id" v-for="company in companies.data.result.data">
                        {{ company.name }}
                    </option>
                </select>
            </div>
            <a href="/companies/1" class="w-full btn btn-primary mt-[14px]">
                Continue
            </a>
        </form>
    </section>
</template>

<script>
    export default {
    middleware: 'auth',
    data() {
        return {
            companies: [],
            selectedCompany: '',
        }
    },
    async fetch() {
        this.companies = await this.$axios.get('/company')
    }
}
</script>