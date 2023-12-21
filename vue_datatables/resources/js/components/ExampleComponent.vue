<template>
    <div class="card">
        <div class="card-header">
            Listar Usuarios
        </div>
        <div class="class card-body">
            <div class="table-responsive">
                <table class="table table-hover table-bordered" id="sampleTable">
                    <thead>
                        <tr>
                            <th>id</th>
                            <th>Nombre</th>
                            <th>email</th>
                            <th>Fecha Creado</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="user in usuarios">
                            <td>{{ user.id }}</td>
                            <td>{{ user.name }}</td>
                            <td>{{ user.email }}</td>
                            <td>{{ user.created_at }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
//data table en la actual versión necesita jquery
import $ from 'jquery';
import datatable from 'datatables.net-bs5';
import 'datatables.net-bs5/css/dataTables.bootstrap5.min.css'; // Estilos base de DataTables para Bootstrap 5
export default {
    mounted() {
        this.getUser()
    },
    data() {
        return {
            usuarios: []
        }
    },
    methods: {
        tabla() {
            this.$nextTick(() => {
                $('#sampleTable').DataTable();
            });
        },
        getUser() {
            axios.get('listar_usuarios').then(res => {
                this.usuarios = res.data
                this.tabla()
            });
        }
    }
}
</script>
