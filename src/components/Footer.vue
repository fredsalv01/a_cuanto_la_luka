<template>
    <div class="footer">
        <div class="footer__content">
            <div class="footer__company-description">
                <img src="/Iconremovebg.png" alt="logo">
                <div class="text">
                    A cuanto la luka es un comparador del tipo de cambio de algunas
                    de las casas de cambio mas importantes del Peru.
                    Lo que te facilita la busqueda de la mejor opcion para ti.
                </div>
            </div>
            <div class="footer__titles" v-for="item in footer" :key="item.title">
                <h3>{{item.title}}</h3>
                <ul v-for="link in item.links" :key="link">
                    <li><a href="#">{{link}}</a></li>
                </ul>
            </div>
        </div>
        <div class="footer__copyright">
            <div class="text">
                <span>Copyright © 2022</span>
                &nbsp;<span>All rights reserved.</span>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    setup() {
    const footer = [
        {
            title:"Datos importantes",
            links:[
                "Politica de privacidad",
                "Terminos y condiciones",
                "Transparencia",
            ]
        },
        {
            title:"Contacto",
            links:[
                "Contacto",
                "Soporte",
                "Acerca de",
            ]
        },
        {
            title:"Redes sociales",
            links:[
                "Facebook",
                "Twitter",
                "Instagram",
            ]
        },
    ];

        return {
            footer
        }
    }    
}
</script>