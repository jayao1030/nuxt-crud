<template lang="pug">
 .list 
  .d-flex
    AddModal.add 
  Table(border :columns="columns1" :data="data")
    template(slot-scope="{ row }" slot="name")
      strong {{ row.name }}
    template(slot-scope="{ row, index }" slot="action")
      EditModal
      Button(
        type="error"
        size="small"
        @click="remove(data.id, index)"
        ) 刪除
    </template>
  </Table>
</template>
<script>
import axios from "axios";
import AddModal from "../../components/AddModal.vue";
import EditModal from "../../components/EditModal.vue";
export default {
  components: {
    AddModal, EditModal
  },
  asyncData(context) {
    // const res = await axios.get("http://localhost:3000/products");
    // return { data: res.data };
    return { data: context.app.store.state.data }
  },
  data() {
    return {
      columns1: [
        {
          title: "Name",
          slot: "name",
        },
        {
          title: "Price",
          key: "price",
        },
        {
          title: "Size",
          key: "size",
        },
        {
          title: "Action",
          slot: "action",
          width: 150,
          align: "center",
        },
      ],
      data: []
    };
  },
  methods: {
    Edit(index) {
      this.$Modal.info({
        title: "User Info",
        content: `Name：${this.data[index].name}<br>Price${this.data[index].price}<br>Size${this.data[index].size}`,
      });
    },
    remove(id, index) {
      const target = this.data[index];
      if (window.confirm(`刪除訂單編號${target.id}?`)) {
        axios
          .delete(`http://localhost:3000/products/${id}`)
          .then(() => {
            this.data.splice(index, 1);
            alert("刪除成功");
            this.$nuxt.refresh()
          })
          .catch((err) => console.log(err));
      }
    },
  },
  mounted() {
    this.$store.dispatch('getData')
  }
};
</script>
<style lang='sass' scoped>
.d-flex
  display: flex
  justify-content: flex-end
.add
  margin-bottom: 10px
</style>