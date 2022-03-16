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
    name:"PageContent",
    data: function() {
        return {
            todoData: [],
            todoData2: [],
        };
    },
    methods: {
            showAlert(id) {
                var item = this.todoData.find(x => x.id == id);
                item.completed = !item.completed;
            },
            showAlert2(id) {
                var item = this.todoData2.find(x => x.id == id);
                item.completed = !item.completed;
            },
            removeTodo(id) {
                var add = this.todoData.find(x => x.id == id);
                this.todoData2.unshift(add);
                var filtered = this.todoData.filter(x => x.id != id);
                //this.todoData2.push(todoData.pop(id));
                this.todoData = filtered;
                console.log(this.todoData);

            },
            removeTodo2(id) {
                var add2 = this.todoData2.find(x => x.id == id);
                this.todoData.push(add2);
                var filtered2 = this.todoData2.filter(x => x.id != id);
                //this.todoData.push(todoData2.pop(id));
                this.todoData2 = filtered2;
                console.log(this.todoData2);
            }
        },
        created() {
            fetch("https://jsonplaceholder.typicode.com/comments")
                .then((res) => {
                    return res.json()
                })
                .then((jsonResponse) => {
                    this.todoData = jsonResponse;
                    console.log(jsonResponse);
                })
        }
}
</script>

<style>

</style>