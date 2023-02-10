<template>
  <div class="goods-container">
    <!-- 左侧图片   -->
    <div class="thumb">
      <div class="custom-control custom-checkbox">

        <!-- 20、23、复选框 ,在子组件中，通过v-model要监听 复选框 状态变化的事件-->
        <input type="checkbox" class="custom-control-input" :id="'cb'+id"  v-model="state"/>

        <label class="custom-control-label" :for="'cb'+id">

          <!--17、商品的缩略图 -->
          <img :src="pic" alt="" />
        </label>
      </div>
    </div>
    <!-- 右侧信息区域 -->
    <div class="goods-info">
      <!-- 12、商品标题 -->
      <h6 class="goods-title">{{title}}</h6>
      <div class="goods-info-bottom">
        <!-- 15、商品价格 -->
        <span class="goods-price">{{ price }}</span>
        <!-- 商品的数量 -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    //22、为什么要封装一个 商品的id 的 自定义属性 呢？将来子组件中商品的勾选状态变化之后，
    //   需要通过 子--》父的形式，通知 父组件根据 id 修改对应商品的勾选状态
    id: {
      type: Number,
      default:''
    },
    // 11 、要渲染的商品的名称
    title: {
      type: String,
      default:''
    },
    // 14、要渲染的商品的价格
    price: {
      type: Number,
      default:''
    },
    //16、 要渲染的商品的图片
    pic: {
      type: String,
      default:''
    },
    //19、 要渲染的商品的状态，是否已勾选
    state: {
      type:Boolean,
      default:false
    },
  },
  
}
</script>

<style lang="less" scoped>
.goods-container {
  + .goods-container {
    border-top: 1px solid #efefef;
  }
  padding: 10px;
  display: flex;
  .thumb {
    display: flex;
    align-items: center;
    img {
      width: 100px;
      height: 100px;
      margin: 0 10px;
    }
  }

  .goods-info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex: 1;
    .goods-title {
      font-weight: bold;
      font-size: 12px;
    }
    .goods-info-bottom {
      display: flex;
      justify-content: space-between;
      .goods-price {
        font-weight: bold;
        color: red;
        font-size: 13px;
      }
    }
  }
}
</style>
