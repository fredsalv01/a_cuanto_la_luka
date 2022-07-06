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
        <div class="mobile__table">
            <div class="mobile__table-companies">
                <a href="#" class="currency_active">Compra</a>
                <a href="#" >Venta</a>
            </div>
            <div class="currency">
                <img src="../assets/img/companies/inkamoney.png" alt="inkamoney">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ 3.7180
                    </span>
                    <span class="currency__sell">
                    V: S/ 3.7330
                    </span>
                    <a target="_blank" class="currency__btn" href="https://www.inkamoney.com/">Ir a</a>
                </div>
            </div>
            <div class="currency">
                <img src="../assets/img/companies/rextie.png" alt="rextie">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ 3.8760
                    </span>
                    <span class="currency__sell">
                    V: S/ 3.9070
                    </span>
                    <a target="_blank" class="currency__btn" href="https://www.rextie.com/">Ir a</a>
                </div>
            </div>
            <div class="currency">
                <img src="../assets/img/companies/cambi.png" alt="cambi">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ 3.8780
                    </span>
                    <span class="currency__sell">
                    V: S/ 3.9020
                    </span>
                    <a target="_blank" class="currency__btn" href="https://www.cambi.pe/">Ir a</a>
                </div>
            </div>
            <div class="currency">
                <img src="../assets/img/companies/dollarhouse.png" alt="dollarhouse">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ 3.8750
                    </span>
                    <span class="currency__sell">
                    V: S/ 3.9000
                    </span>
                    <a target="_blank" class="currency__btn" href="https://dollarhouse.pe/">Ir a</a>
                </div>
            </div>
            <div class="currency">
                <img src="../assets/img/companies/roblex.png" alt="roblex">
                <div class="currency__data">
                    <span class="currency__buy">
                    C: S/ 3.8750
                    </span>
                    <span class="currency__sell">
                    V: S/ 3.8950
                    </span>
                    <a target="_blank" class="currency__btn" href="https://roblex.pe/#/">Ir a</a>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { ref } from 'vue'
export default {
    setup() {
        const lastUpdate = ref(new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds())
        const update = () => {
            lastUpdate.value = (new Date().getHours() + ':' + new Date().getMinutes() + ':' + new Date().getSeconds())
        }
        setInterval(update, 300000)
        update()
        return {
            lastUpdate
        }
    }
}
</script>