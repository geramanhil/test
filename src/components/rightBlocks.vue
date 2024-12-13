<template>
  <div class="container-right">
    <div class="selected">
      <div @click="deleteItem()">
        {{ selectedItem.name }}
      </div>
    </div>

    <div class="list">
      <div  
        v-for="item in list"
        :class="[{ 'select': selectedItem.id == item.id }, 'item']" 
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
        selectedItem: '',
        list: [
          {
              "id": 11,
              "name": "Jacket 1"
          },
          {
              "id": 12,
              "name": "Jacket 2"
          },
          {
              "id": 13,
              "name": "Jacket 3"
          },
          {
              "id": 14,
              "name": "Jacket 4"
          },
          {
              "id": 15,
              "name": "Hoodie 1"
          },
          {
              "id": 16,
              "name": "Hoodie 2"
          },
          {
              "id": 17,
              "name": "Hoodie 3"
          },
          {
              "id": 18,
              "name": "Hoodie 4"
          }
        ]
      }
    },
    methods:{
      selectItem(item){
        if(this.selectedItem.id == item.id) {
          this.deleteItem(item)
          return
        }
        if(!this.selectedItem) this.selectedItem = item
      },
      deleteItem(){
        this.selectedItem = ''
      }
    }
  }
</script>

<style lang="scss">
.container-right {
  width: 50%;

  .selected {
    width: fit-content;
    height: 45px;
    min-width: 35px;
    border: black 1px solid;
    display: flex;
    padding: 0 5px;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  .list {
    display: flex;
    border: black 1px solid;
    padding: 5px;
    column-gap: 5px;
    margin-top: 5px;
    
    .item {
      border: black 1px solid;
      cursor: pointer;

      &.select {
        background-color: aquamarine;
      }
    }
  }
}
</style>