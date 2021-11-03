<template>
  <div class="hello">
      <div class="holder">
        <p>These are the things you need to do.</p>
        <form @submit.prevent="addListItem">
            <input type="text" placeholder="Add a thing to do..." v-model="listItem">
        </form>

        <ul>
            <transition-group name="items" class="animations"> 
            <!-- enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown"> -->
                <li v-for="(data, index) in list" :key="index">
                    <span> {{ data.list }} </span>
                    <button type="checkbox" class="checkbox" v-on:click="remove(index); addCompleted(index)"></button>
                    <!-- <i class="fa fa-minus-circle" v-on:click="remove(index)"></i> v-model="checked" --> 
                </li>
            </transition-group>
        </ul>

        <p>These are the things you completed</p>
        <ul>
            <transition-group name="items" class="animations"> 
            <!-- enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown"> -->
                <li v-for="(data, index) in completed" :key="index"> 
                    <span> {{ data.completed }} </span>
                    <!-- <i class="fa fa-minus-circle" v-on:click="remove(index)"></i> v-model="checked" --> 
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
         { "list": "Complete HW"},
        { "list": "Read Book"}
      ],
      completed: [],
    }
  },
  methods: {
      addListItem() {
          this.list.push({list: this.listItem})
          this.listItem = '';
          /* console.log("This checkbox value is: "+this.checked); */
      },
      remove(id) {
          this.list.splice(id,1)
      },
      addCompleted(id) {
          this.completed.push({completed: list[id]})
          this.listItem= '';
      }
      
  }
}
</script>

<style scoped>

/* @import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1"; 
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; */

  .holder {
    background: #fff;
  }
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }
  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }
  .container {
    box-shadow: 0px 0px 40px lightgray;
  }
input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
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