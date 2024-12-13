<template>
  <div class="container-left">
    <div class="selected">
      <div 
        class="item" 
        v-for="item in selected" 
        :key="item.id"
        @click="deleteItem(item)"
      >
        {{ item.name }}
      </div>

      <div class="info">
        {{ `selected ${selected.length}/${list.length}` }}
      </div>
    </div>

    <div class="list">
      <div  
        v-for="item in list"
        :class="[{ 'select': selected.indexOf(item) != -1 }, 'item']" 
        :key="item.id"
        @click="selectItem(item)"
      >
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        selected: [],
        list: [
          {
              "id": 1,
              "name": "Shoes 1"
          },
          {
              "id": 2,
              "name": "Shoes 2"
          },
          {
              "id": 3,
              "name": "Shoes 3"
          },
          {
              "id": 4,
              "name": "Shoes 4"
          },
          {
              "id": 5,
              "name": "T-shirt 1"
          },
          {
              "id": 6,
              "name": "T-shirt 2"
          },
          {
              "id": 7,
              "name": "T-shirt 3"
          },
          {
              "id": 8,
              "name": "T-shirt 4"
          }
        ]
      }
    },
    methods:{
      selectItem(item){
        if(this.selected.indexOf(item) != -1) {
          this.deleteItem(item)
          return
        }
        if(this.selected.length < 6 && this.selected.indexOf(item) == -1) this.selected.push(item)
      },
      deleteItem(item){
        this.selected = this.selected.filter(x => x != item)
      }
    }
  }
</script>

<style lang="scss">
.container-left {
  width: 50%;

  .selected {
    position: relative;
    height: 35px;

    .info {
      position: absolute;
      left: 0;
      bottom: 0;
    }
  }

  .selected, .list {
    display: flex;
    border: black 1px solid;
    padding: 5px;
    column-gap: 5px;
    

    .item {
      border: black 1px solid;
      height: fit-content;
      cursor: pointer;

      &.select {
        background-color: aquamarine;
      }
    }
  }

  .list {
    margin-top: 5px;
  }
}
</style>