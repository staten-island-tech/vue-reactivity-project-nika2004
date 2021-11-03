<template>
  <div class="hello">
      <div class="holder">
        <p>TO DO LIST</p>
        <form @submit.prevent="addListItem">
            <input type="text" placeholder="Add things to do..." v-model="listItem">
        </form>
        <ul>
            <transition-group name="items" class="animations"> 
                <li v-for="(data, index) in list" :key="index">
                    <span> {{ data.list }} </span>
                    <button type="checkbox" class="checkbox" v-on:click="remove(index); addCompleted(index)"></button>
                </li>
            </transition-group>
        </ul>

        <br>

        <p>COMPLETED ITEMS</p>
        <ul>
            <transition-group name="items" class="animations"> 
                <li v-for="(data, index) in completed" :key="index"> 
                    <span> {{ data.completed }} </span>
                </li>
            </transition-group>
        </ul>

      </div>
  </div>
</template>
 
<script>
export default {
  name: 'List',
  data() {
    return {
      listItem: '',
      list: [
        // { "list": "Complete HW"},
        // { "list": "Read Book"},
      ],
      completed: [],
    }
  },
  methods: {
      addListItem() {
          this.list.push({list: this.listItem})
          this.listItem = '';
      },
      remove(id) {
           this.removedItem = this.list[id] 
           this.list.splice(id,1)
      },
      addCompleted() {
          this.completed.push({completed: this.removedItem["list"]})
      }
      
  }
}
</script>

<style scoped>

ul {
    margin: 0;
    margin-top: 5px;
    padding: 0;
    list-style-type: none;
}
  
ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: black;
}

p {
    margin-bottom: 5px;
    font-size: 18px;
    text-align:center;
    padding: 10px;
    color:white;
    background-color: blue;
    width: fit-content;

}

br {
    padding: 20px;
}

input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: navy;
    color: white;
}

.checkbox {
   float: left;
   cursor:pointer;
   padding: 5px;
   margin: 6px;
   margin-left: 3px;
   margin-right: 10px;
}

.animations {
   animation-duration: 1s;
   animation-name: slidein;
}

</style>