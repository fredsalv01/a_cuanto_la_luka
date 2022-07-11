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
                <label :class="btn_buy">Compra
                    <input type="checkbox" v-model="currency__buy">
                </label>
                <label :class="btn_sell">Venta
                    <input type="checkbox" v-model="currency__sell">
                </label>
            </div>
            <div class="currency" v-if="filteredCompanies.length > 0" v-for="company in filteredCompanies" :key="company.name">
                <img :src="`./companies/${company.logo}`" :alt="company.name">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ {{(company.buy).toFixed(4)}}
                    </span>
                    <span class="currency__sell">
                    V: S/ {{(company.sell).toFixed(4)}}
                    </span>
                    <a target="_blank" class="currency__btn" :href="company.url">Ir a</a>
                </div>
            </div>

            <div class="currency" v-if="filteredCompanies.length == 0">
                <p>No hay resultados</p>
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

        const currency__sell = ref(false);
        const currency__buy = ref(false);
        const btn_sell = reactive(["btn_sell"]);
        const btn_buy = reactive(["btn_buy"]);

        const filteredCompanies = computed(() => {
            if(search.value){
                return companies.filter(company => {
                    return company.name.toLowerCase().includes(search.value.toLowerCase())
                })
            }
            if(currency__sell.value){
                const buy = document.getElementsByClassName("btn_buy");
                buy.cheked = false;
                // currency__buy.value = false;
                return companies.sort((a, b) => {
                    return b.sell > a.sell ? 1 : -1
                })
            }
            if(currency__buy.value){
                const sell = document.getElementsByClassName("btn_sell");
                sell.cheked = false;
                // currency__sell.value = false;
                return companies.sort((a, b) => {
                    return b.buy < a.buy ? 1 : -1
            })
            }else{
                return companies
            }
        })

        

        

        return {
            lastUpdate,
            companies,
            search,
            filteredCompanies,
            currency__buy,
            currency__sell,
            btn_buy,
            btn_sell,
        }
    }
}
</script>