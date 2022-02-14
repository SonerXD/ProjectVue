<template>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <div class="container">
    <h2>Agrega Juego</h2>


    <div class="mb-3">
        <label for="" class="form-label">Nombre</label>
        <input v-model="game.nombre" type="text" id="nombre" name="nombre" class="form-control" tabindex="1">
    </div>
    <div class="mb-3">
        <label for="" class="form-label">Categoria</label>
        <input v-model="game.categoria" type="text" id="categoria" name="categoria" class="form-control" tabindex="2">
    </div>
    <div class="mb-3">
        <label for="" class="form-label">Precio</label>
        <input v-model="game.precio" type="number" id="precio" name="precio" step="any" class="form-control" tabindex="3">
    </div>

    <a href="/juegos" class="btn btn-danger" tabindex="4">Cancelar</a>
    <a href="/juegos" @click="this.crear()" class="btn btn-primary" tabindex="5">Guardar</a>



</div>
</template>

<script>

export default {
    data(){
        return{
            game:{
                nombre:'',
                categoria:'',
                precio:0
            }
        }
    },
    methods: {
        async crear(){
            const $re= await axios.post('api/Crear', this.game) 
            
        },
        
    },
    created(){
        console.log("Hola xd")
    }
}
</script>
