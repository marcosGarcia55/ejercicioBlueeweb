<template>
    <h2>Tipo de cuenta: {{cuenta}}</h2>
    <h2>Saldo: {{saldo}}</h2>
    <h2>Cuenta {{estado ? 'Activada' : 'Desactivada'}}</h2>
    <div v-for="(servicio, index) in servicios" :key="index">
        {{index + 1}} - {{servicio}}
    </div>
    <AccionSaldo texto="Aumentar saldo" @accion="aumentar"/>
    <AccionSaldo texto="Disminuir saldo" @accion="disminuir" :desactivar="desactivar"/>
</template>

<script>
import AccionSaldo from './AccionSaldo'

export default {
    //name: 'AccionSaldo',
    components:{
        AccionSaldo       
    },
    data() {
        return {
            cuenta: 'Visa',
            saldo: 1000,
            estado: true,
            servicios: ['Giro', 'Abono', 'Transferencia'],
            desactivar: false
        }
    },
    methods: {
        aumentar(){
            this.saldo = this.saldo + 100;
            this.desactivar = false;
        },
        disminuir(){
            if (this.saldo === 0){
                alert('Saldo agotado');
                this.desactivar= true
                return
            }            
            this.saldo= this.saldo - 100;            
        }
    }
}
</script>

<style>

</style>