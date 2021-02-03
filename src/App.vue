<template>
  <div id="app">
    <h1>{{ titulo }}</h1>
    <div class="form" >
      <div>
        <div class="form-group">
          <label>Título</label>
          <input class="form-control" type="text" v-model="nota.titulo">
        </div>
        <div class="form-group">
          <label>Texto</label>
          <textarea class="form-control" v-model="nota.texto"></textarea>
        </div>
      </div>
    </div>
    <button class="btn btn-primary" @click="agregarNota">Enviar</button>
    <div class="col-sm-12">
      <div class="col-sm-4 nota" v-for="(nota, index) in notas">
        <div class="card">
          <div class="card-block">
            <div class="card-title">
              {{nota.titulo}}
            </div>
            <div class="car-subtitle mb-2 text-muted">
              {{nota.fecha}}
            </div>
            <p class="card-text">
              {{nota.texto}}
            </p>
          </div>
          <button class="close bg-danger blank" @click="eliminarNota(index)" >&times;</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      titulo: 'Gestión de notas',
      nota:{
        titulo:'',
        texto:''
      },
      notas:[
        {
          titulo:'Ir al cine',
          texto:'Examinar las películas de estreno',
          fecha: new Date(Date.now()).toLocaleDateString()
        }
      ]
     
    }
  },
  methods:{
    agregarNota:function(){
      let{texto, titulo} = this.nota;
      this.notas.push({
        texto, 
        titulo,
        fecha: new Date(Date.now()).toLocaleDateString()
      });

      this.nota.titulo='';
      this.nota.texto='';
    },
    eliminarNota:function(index){
      this.notas.splice(index,1);
    }
  }
}
</script>

<style>
.blank{color: white}
*{
  padding: 5px;
}
.form{
  text-align: left;
}
.card{
  text-align: left;
  border: 1px solid #2c3e50;
  border-radius: 4px;
  padding: 8px;
}
nota{

  padding: 5px;
}
</style>
