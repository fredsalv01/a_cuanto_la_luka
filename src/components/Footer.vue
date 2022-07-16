<template>
    <div class="footer">
        <div class="footer__wrapper">
            <div class="branding">
            <div class="logo">
                <a href="/a_cuanto_la_luka/">
                    <img src="/Iconremovebg.png" alt="A cuanto la Luka">
                </a>
            </div>
            <div class="text">
                A cuanto la luka es un comparador del tipo de cambio de algunas
                Casas de Cambio Online que se encuentran en la web en tiempo real.
                Ademas de proveer noticias acerca del tipo de cambio en el Peru.
            </div>
        </div>
        <div class="headings" v-for="(heading, index) in headings" :key="index">
            <h3>
                {{ heading.link }}
            </h3>
            <ul class="links">
                <li v-for="(li, index) in heading.list" :key="index">
                    {{ li }}
                </li>
            </ul>
        </div>
        </div>
        <footer>
            <div class="copyright">
                <p>&copy; 2022 A cuanto la luka</p>
            </div>
        </footer>
    </div>
</template>
<script>
import { computed, reactive, ref } from "vue";
export default {
    setup() {
        const headings = ref([
            {
                link: "Datos importantes", 
                list: [
                    'Politicas de privacidad',
                    'Terminos y condiciones',
                ]
            },
            {
                link: "Contactanos",
                list: [
                    'fredalbert37@outlook.com',
                    'cel: +51 980 048 040',
                ]
            }
        ])

        return {
            headings
        }
    }
}
</script>
<style lang="">
    
</style>