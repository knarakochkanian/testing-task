<script>
export default {
  data() {
    return {
      data: [
        { name: "foo1", value: "bar1" },
        { name: "foo2", value: "bar2" },
        { name: "foo3", value: "bar3" },
        { name: "foo4", value: "bar4" },
        { name: "foo5", value: "bar5" }

      ],
      selectedItem: null
    };
  },
  methods: {
    selectItem(index) {
      this.selectedItem = this.data[index];
    },
    saveItem() {
      this.selectedItem = null;
    }
  }
};
</script>

<template>
  <div class='app-wrapper'>
    <ul>
      <li v-for="(item, index) in data" :key="index" @click="selectItem(index)">
        {{ item.name }}: {{ item.value }}
      </li>
    </ul>

    <form v-if="selectedItem !== null" @submit.prevent="saveItem" class="app-wrapper-form">
      <label for="value">Value:</label>
      <input type="text" id="value" v-model="selectedItem.value">
      <button type="submit">Save</button>
    </form>
  </div>
</template>

<style lang="scss" scoped>
.app-wrapper{
  font-family: "Haas Grot Text R Web", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 20px;
  list-style: none;
li{
  list-style: none;
}
  button{
    background-color: #EA4C89;
    border-radius: 8px;
    border-style: none;
    box-sizing: border-box;
    color: #FFFFFF;
    cursor: pointer;
    display: inline-block;
    margin: 0;
    outline: none;
    padding: 10px 20px;
    position: relative;
    text-align: center;
  }
  input{
    border-radius: 8px;
    box-sizing: border-box;
    padding: 10px 20px;
  }
  &-form{
    margin-top: 30px;
    >label{
      font-weight: 600;
      padding-right: 10px;
    }
    >input{
      margin-right: 20px;
    }
  }
}
</style>
