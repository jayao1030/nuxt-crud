<template lang="pug">
  div
    Button(type="primary"  @click="handleAddBtn()") 新增
    Modal(v-model="isModalOn" title="新增商品" footer-hide)
      form(@submit.prevent="handleSubmit" class="form")
        label 品項名稱:
        input(type="text" v-model="name" placeholder="請輸入名稱" required /)
        label 價格:
        input(type="text" v-model="price" placeholder="請輸入價格" required /)
        label 尺寸:
        select(name="size" v-model="size")
          option(value="" disabled) 請選擇尺寸
          option(value="L") L
          option(value="M") M
          option(value="S") S
        button.btnEdit 新增
        button(type="button" class="btnCancel" @click="handleCancel") 取消
</template>
<script>
import axios from "axios";
export default {
  props: {},
  data() {
    return {
      isModalOn: false,
      name: "",
      price: "",
      size: "",
      uri: "http://localhost:3000/products",
    };
  },
  methods: {
    handleAddBtn() {
      this.isModalOn = !this.isModalOn;
    },

    handleSubmit() {
      const product = {
        name: this.name,
        price: this.price,
        size: this.size,
        notes: this.notes,
      };
      axios
        .post(this.uri, product)
        .then(() => {
          alert("新增成功");
          this.$nuxt.refresh();
        })
        .catch((err) => console.log(err));
      this.closeModal();
    },
    handleCancel() {
      this.closeModal();
    },
    closeModal() {
      this.isModalOn = false;
    },
  },
};
</script>
<style lang="sass" scoped>


</style>
