<template>
  <div class="row ">
    <div class="col-12 my-auto">
      <div class="card text-light bg-danger mx-auto" style="width: 30rem;min-height:20rem;">
        <div class="card-body pt-4">
          <h1 class="card-title text-center">Todo List </h1>
          <h5 class="card-subtitle text-center mb-2 text-light">Get things done</h5>
          <hr>

            <!-- Items --> 
          <ul v-if="items.length" class="list-group list-group-flush pt-4">
            <li  v-for="(item,index) in items" :key="index"
            class="list-group-item pt-3" :class="{'done' : item.done}">
              <div class="d-flex bd-highlight">

                <div class="flex-grow-1 bd-highlight">
                  <span class="label" > {{item.title}} </span>
                </div>
                

                <button class="btn bd-highlight" type="button" @click="changeItemStatus(index)">
                    <i aria-hidden="true" class="material-icons">{{item.done ? 'check_box' :
                     'check_box_outline_blank'}}</i>
                </button>

              <button class="btn bd-highlight" type="button"
                  aria-label="Delete" title="Delete" @click="deleteItem(index)">
                  <i aria-hidden="true" class="material-icons">delete</i>
              </button>
              </div>            
            </li>
        </ul>

          <h5 class="text-center pt-2" v-else>Your todo list is empty.</h5>
            <!--Add Items --> 
     
        <form class="text-center" @submit.prevent="addItem">
              <div class="mb-3 pt-5 ">
                <h4 class="form-label">Add to do</h4>
                <input type="text" class="form-control" aria-describedby="emailHelp" v-model="newTitle">
 
              </div>

              <button type="submit" class="btn btn-dark ">Add Item</button>
            </form>
     
            


        </div>
      </div>
    </div>
  </div>
</template>

<script>
 
export default {
  
  name: 'ToDo',
  data() {
    return {
      newTitle: '',
      items: [],
    }
  },
  methods: {
    addItem(){
      if(this.newTitle === ''){
        return;
      }
      this.items.push({
        title: this.newTitle,
        done: false,
      })
      this.newTitle = ''
    },
    deleteItem(index){
      this.items.splice(index,1)
    },
    changeItemStatus(index){
      const item = this.items[index]
      item.done = !item.done
    }
  },
}
</script>


<style scoped>
.row{
  height: 100vh;
}
.card{
  -webkit-box-shadow: 11px 10px 11px 11px rgba(0,0,0,0.22); 
  box-shadow: 11px 10px 11px 11px rgba(0,0,0,0.22);
}
li{
  background-color: transparent;
  color: white;
}
button:hover{
  color:black;
  background-color: transparent;
}
.done .label {
  opacity: .6;
}
.done .label:before {
  content: '';
  position: absolute;
  top: 50%;
  left: -.5rem;
  display: block;
  width: 0%;
  height: 1px;
  background: #FFF;
  animation: strikeitem .3s ease-out 0s forwards;
}
.label {
        position: relative;
        transition: opacity .2s linear;
    }
@keyframes strikeitem {
        to {
            width: calc(100% + 1rem);
        }
    }

</style>
