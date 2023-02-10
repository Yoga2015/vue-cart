<template>
  <div class="app-container">
    <!--3、 引入 Header组件 的实例 -->
    <Header title="购物车"></Header>

    <!-- 6、10.1、13、18、21、24、引入 Goods组件 的实例   -->
    <Good v-for="item in list" :key="item.id"
    :id="item.id"
    :title="item.goods_name"
    :price="item.goods_price"
    :pic="item.goods_img"
    :state="item.goods_state">
    </Good>

  </div>
</template>

<script>
// 1、导入 Header组件
import Header from "@/components/Header/Header.vue";
// 4、导入 Goods组件
import Good from "@/components/Goods/Goods.vue";
// 7、导入 axios 请求库   （先 yarn add axios -S 安装 ）   
import axios from 'axios';

export default {
  data() { 
    return {
      //10、list 数组容器 接收 axios请求 响应回来的数据
      list: []
    }
  },

  // 局部注册组件 私有组件
  components: {
    // 2、5、注册 Header 组件，这样就可以以标签的形式来使用 Header组件的实例
      Header,Good
  },
  created() {
    console.log(this);
    this.initCartList();   // 9、一般在 created 发起网络请求
  },
  methods: {
    // 8、利用 axios 发请求 , 获取 商品数据
     async initCartList() { 
        const { data: res } = await axios.get('https://escook.cn/api/cart');
        if (res.status === 200) { 
          this.list = res.list;
        }
     },
  },
}
</script>

<style lang="less" scoped>
.app-container {
  padding-top: 45px;
  padding-bottom: 50px;
}
</style>
