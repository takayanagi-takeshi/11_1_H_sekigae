<template>
<div>
  <div class="aa">
    <div class="form-group">
        <div class="input-group">
            <input type="text" v-model="newItem" class="form-control">
            <span class="input-group-btn"><button class="btn btn-primary" @keydown.enter="onKeyDown()" @click="addItem()">登録</button></span>
            <!-- <input @name.enter="addItem()"> -->
            <span class="input-group-btn"><button class="btn btn-primary1" @click="shuffles()">シャッフルスタート！！</button></span>
        </div>
        <ul class="submit_group">
          <li class="list_group" v-for="todo in todos" :key="todo">{{todo}}</li>
        </ul>
    </div>

    <div id="zaseki">
      <ul id="zaseki_name">
        <li class="index_name" v-for="(name,index) in names" :key="name.id">
          <div class="name">{{index + 1}}:</div>
          <div class="name">{{name}}</div>
        </li>
      </ul>
    </div>
  </div>
</div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'Zaseki',
  data() {
    return {
      // newItem: '',
      // todos: [],
      names: [
      
      ],
      shuffle_names: [],

    }
  },
    mounted: function() {
      // this.shuffle_names = this.shuffle(this.names)
  },
    methods: {
      addItem: function(){
        this.names.push(this.newItem);
        this.newItem = '';
      },
      shuffles() {
        this.shuffle_names = this.shuffle(this.names)
        this.shuffle_names.splice()
      },
      onKeyDown: function() {
        this.names.push(this.newItem);
        this.newItem = '';
    },
    shuffle: function(array) {
      for (let i = array.length - 1; i > 0; i--) {
        let r = Math.floor(Math.random() * (i + 1))
        let tmp = array[i]
        array[i] = array[r]
        array[r] = tmp
      }
      return array
    }
  }
}
</script>

<style>
/* .aa {
  display: flex;
} */

.index_name {
  list-style: none;
  font-size: 30px;
  border: solid 1px;
  display: flex;
  padding-left: 10px;
  padding-right: 10px;
  width: 40%;
  margin-left :250px ;
}

.name {
  padding-left: 20px;
  padding-right: 10px;
}

.btn-primary1 {
  position: absolute;
  padding:  10px;             /* 余白指定 */
  left:  15px;                /* 左からの位置指定 */
  top: 100px;
}
</style>
