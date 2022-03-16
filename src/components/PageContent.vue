<template>
    <div  class="container-fluid">
       <div class="row">
            <div class="col-md-6">
              <div v-for="item in todoData" :key="item.id">
                <div class="col-md-11" v-on:click="showAlert(item.id)">
                  <div v-if="!item.completed">
                    <div class="alert alert-success" role="alert">
                      Adı: {{ item.name}}
                      <br>
                      E-mail: {{ item.email}}
                    </div>
                  </div>
                </div>
                <div class="col-md-1">
                  <button class="btn btn-danger" v-on:click="removeTodo(item.id)">Sil</button>
                </div>
              </div>
            </div>
            <div class="col-md-6">
              <div v-for="item in todoData2" :key="item.id">
                <div class="col-md-11" v-on:click="showAlert2(item.id)">
                  
                  <div v-if="!item.completed">
                    <div class="alert alert-danger" role="alert">
                      Adı: {{ item.name}}
                      <br>
                      E-mail: {{ item.email}}
                    </div>
                  </div>
                </div>
                <div class="col-md-1">
                  <button class="btn btn-danger" v-on:click="removeTodo2(item.id)">Sil</button>
                </div>
              </div>
            </div>
            <!-- /.container-fluid -->
          </div>
    </div>
</template>

<script>
export default {
    name:"PageContent"
}
</script>

<style>

</style>