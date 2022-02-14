<script>

export default{
    data(){
        return{
            games:[]
        }
    },

    methods:{
        async mounted(){
            const $re= await axios.get('api/Mostrar')
            this.games=$re.data
        },
        async eliminar(id){
            const $re= await axios.delete('api/Eliminar/'+id)
            this.mounted()
        }
        },
    created(){
        this.mounted()
    }
}
</script>



<template>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <div class="container">
    <h1>Lista de juegos</h1>
    <a href="crear" class="btn btn-primary">Crear</a>
<table class="table table-dark table-striped mt-4">
    <thead>
        <tr>
            <th scope="col">ID</th>
            <th scope="col">Nombre</th>
            <th scope="col">Categoria</th>
            <th scope="col">Precio</th>
            <th scope="col">Acciones</th>
        </tr>
    </thead>
    <tbody>
            <tr v-for='game in games' :key='game.id'>
                <td>{{ game.id }}</td>
                <td>{{ game.nombre }}</td>
                <td>{{ game.categoria }}</td>
                <td>{{ game.precio }}</td>
                <td>
                    <a href="/editar" class="btn btn-info">Editar</a>
                    <button type="submit" @click='this.eliminar(game.id)' class="btn btn-danger">Eliminar</button>
                </td>
            </tr>
    </tbody>
</table>
    
</div>
</template>