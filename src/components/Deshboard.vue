<template>
    <div id="massa-table">
        <div>
            <div id="massa-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente:</div>
                <div>Pão:</div>
                <div>Carne:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>
            </div>
        </div>
        <div id="massa-table-rows">
           <div class="massa-table-row" v-for="burger in burgers" :key="burger.id">
               <div class="order-number">{{ burger.id }}</div>
               <div>{{ burger.nome }}</div>
               <div>{{ burger.pao }}</div>
               <div>{{ burger.carne }}</div>
               <div>
                   <ul>
                       <li v-for="(opcional, index) in Opcionais" :key="index">
                           {{ opcional }}
                       </li>
                   </ul>
               </div>
        <div>
           <select name="status" class="status">
           <option value="">Selecionar:</option> 
           <option v-for="s in status" :key="s.id" value="s.tipo" :selected="burger.status == s.tipo">
           {{ s.tipo }}
           </option>   
        </select>
        <button class="delete-btn">Cancelar</button> 
    </div>
    </div>
    </div>
    </div>
</template>

<script>

export default {
    name: "Deshboard",
    data() {
        return {
            burgers: null,
            burger_id: null,
            status: []
        }
    },
    methods: {
        async getPedidos() {

            const req = await fetch("http://localhost:3000/burgers");  

            const data = await req.json(); 

            this.burgers = data;

            console.log(this.burgers);
            // resgatar os status
            this.getStatus();
        },
        async getStatus() {
            const req = await fetch("http://localhost:3000/status");

            const data = await req.json;

            this.status = data;

           // console.log(data);

        }

    },
    mounterd() {
        this.getPedidos();
    }
}
</script>

<style scoped>
#massa-table {
    max-width: 1200px;
    margin: 0 auto;
}
#massa-table-heading,
#massa-table-rows,
.massa-table-row {
   display: flex;
   flex-wrap: wrap; 
}
#massa-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
}
#massa-table-heading div,
.massa-table-row div {
    width: 19%;
}
.massa-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
}
#massa-table-heading .order-id,
.massa-table-row .order-number {
    width: 5%;

}
select {
    padding: 12px 6px;
    margin-right: 12px;
}
.delete-btn {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
}
.delete-btn:hover {
    background-color: transparent;
    color:#222;
}

</style>
