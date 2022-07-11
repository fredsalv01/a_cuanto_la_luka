<template>
    <div class="mobile__container">
        <div class="mobile__info-banner">
            <p>
                Datos actualizados a las {{ lastUpdate }}
            </p>
            <span>
                (El precio se actualiza cada 5 minutos)
            </span>
        </div>
        <div class="mobile__search">
            <input class="mobile__search-input" type="text" placeholder="Buscar..." v-model="search">
        </div>
        <div class="mobile__table">
            <div class="mobile__table-companies">
                <a href="#" class="currency_option currency_active">Compra</a>
                <a href="#" class="currency_option">Venta</a>
            </div>
            
            <div class="currency" v-for="company in filteredCompanies" :key="company.name">
                <img :src="`./companies/${company.logo}`" :alt="company.name">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ {{company.buy}}
                    </span>
                    <span class="currency__sell">
                    V: S/ {{company.sell}}
                    </span>
                    <a target="_blank" class="currency__btn" :href="company.url">Ir a</a>
                </div>
            </div>
            
        </div>
    </div>
</template>
<script>
import { computed, reactive, ref } from 'vue'
import data from '../data/dataExchanges.json'

export default {
    setup() {
        const lastUpdate = ref(new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds())
        const update = () => {
            lastUpdate.value = (new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds())
        }
        setInterval(update, 300000)
        update()

        const companies = reactive(data)
        const search = ref("");
        const filteredCompanies = computed(() => {
            return companies.filter(company => {
                return company.name.toLowerCase().includes(search.value.toLowerCase())
            })
        })

        return {
            lastUpdate,
            companies,
            search,
            filteredCompanies
        }
    }
}
</script>