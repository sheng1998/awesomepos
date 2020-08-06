<template>
  <div class="pos">
    <div>
      <el-row>
        <el-col :span='7' class="order" ref="order">
          <el-tabs>
            <el-tab-pane label="点餐">
              <el-table :data="tableData" class="diancan" border>
                <el-table-column prop='goodsName' label='商品名称'></el-table-column>
                <el-table-column prop='count' label='数量' width="50"></el-table-column>
                <el-table-column prop='price' label='金额' width="70"></el-table-column>
                <el-table-column label='操作' width="100" fixed="right">
                  <template slot-scope="scope">
                    <el-button type="text" size="small" @click="deleteSingleOrder(scope.row)">删除</el-button>
                    <el-button type="text" size="small" @click="addOrderCount(scope.row)">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
              <div class="totallDiv">
                <small class="totalCount">数量：</small>{{ totalCount }}
                <small class="totalPrice">金额：</small>{{ totalPrice }}.00元
              </div>
              <div class="order-btn">
                <el-button type="warning">挂单</el-button>
                <el-button type="danger" @click="deleteAllOrder">删除</el-button>
                <el-button type="success" @click="checkout">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单">挂单</el-tab-pane>
            <el-tab-pane label="外卖">外卖</el-tab-pane>
          </el-tabs>
        </el-col>
        <el-col :span="17" class="shop">
          <div class="common-goods">
            <div class="title">常用商品</div>
            <div class="common-goods-list">
              <ul>
                <li v-for="goods in commonGoods" :key="goods.goodsId" @click="addOrderList (goods)">
                  <span class="good-name">{{ goods.goodsName }}</span>
                  <span class="good-price">￥{{ goods.price }}元</span>
                </li>
              </ul>
            </div>
          </div>
          <div class="goods-type">
            <el-tabs>
              <el-tab-pane label="汉堡">
                <ul class='cookList'>
                  <li v-for="goods in type1Goods" :key="goods.goodsId" @click="addOrderList (goods)">
                    <span class="foodImg">
                      <img :src="goods.goodsImg" width="100%">
                    </span>
                    <span class="foodName">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}.00元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="小食">
                <ul class='cookList'>
                  <li v-for="goods in type2Goods" :key="goods.goodsId" @click="addOrderList (goods)">
                    <span class="foodImg">
                      <img :src="goods.goodsImg" width="100%">
                    </span>
                    <span class="foodName">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}.00元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="饮料">
                <ul class='cookList'>
                  <li v-for="goods in type3Goods" :key="goods.goodsId" @click="addOrderList (goods)">
                    <span class="foodImg">
                      <img :src="goods.goodsImg" width="100%">
                    </span>
                    <span class="foodName">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}.00元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="套餐">
                <ul class='cookList'>
                  <li v-for="goods in type4Goods" :key="goods.goodsId" @click="addOrderList (goods)">
                    <span class="foodImg">
                      <img :src="goods.goodsImg" width="100%">
                    </span>
                    <span class="foodName">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}.00元</span>
                  </li>
                </ul>
              </el-tab-pane>
            </el-tabs>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  name: 'pos',
  data () {
    return {
      tableData: [],

      commonGoods: [
        {
          goodsId: 200,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 201,
          goodsName: '田园鸡腿堡',
          price: 15
        },
        {
          goodsId: 202,
          goodsName: '和风汉堡',
          price: 15
        },
        {
          goodsId: 400,
          goodsName: '快乐全家桶',
          price: 80
        },
        {
          goodsId: 302,
          goodsName: '脆皮炸鸡腿',
          price: 10
        },
        {
          goodsId: 303,
          goodsName: '魔法鸡块',
          price: 20
        },
        {
          goodsId: 101,
          goodsName: '可乐大杯',
          price: 10
        },
        {
          goodsId: 105,
          goodsName: '雪顶咖啡',
          price: 18
        },
        {
          goodsId: 304,
          goodsName: '大块鸡米花',
          price: 15
        },
        {
          goodsId: 305,
          goodsName: '香脆鸡柳',
          price: 17
        }
      ],

      type1Goods: [
        {
          goodsId: 200,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '香辣鸡腿堡',
          price: 18
        }, {
          goodsId: 201,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '田园鸡腿堡',
          price: 15
        }, {
          goodsId: 202,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '和风汉堡',
          price: 15
        }
      ],

      type2Goods: [
        {
          goodsId: 300,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '爱心薯条',
          price: 8
        }, {
          goodsId: 301,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '甜筒',
          price: 8
        }, {
          goodsId: 302,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '脆皮炸鸡腿',
          price: 10
        }, {
          goodsId: 303,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '魔法鸡块',
          price: 20
        }, {
          goodsId: 304,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '大块鸡米花',
          price: 15
        }, {
          goodsId: 305,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '香脆鸡柳',
          price: 17
        }
      ],

      type3Goods: [
        {
          goodsId: 100,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '可口可乐',
          price: 8
        }, {
          goodsId: 101,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '可乐大杯',
          price: 10
        }, {
          goodsId: 102,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '雪碧',
          price: 8
        }, {
          goodsId: 105,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '雪顶咖啡',
          price: 18
        }
      ],

      type4Goods: [
        {
          goodsId: 400,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '快乐全家桶',
          price: 80
        }
      ],

      totalCount: 0,
      totalPrice: 0
    }
  },

  mounted: function () {
    var orderHeight = document.body.clientHeight
    this.$refs.order.$el.style.height = orderHeight + 'px'
  },

  methods: {

    // 向商品列表添加商品
    addOrderList (goods) {
      // 判断该商品是否存在于订单列表中，在就直接增加数量，不在就需要添加
      let isHave = false
      for (let i = 0; i < this.tableData.length; i++) {
        if (this.tableData[i].goodsId === goods.goodsId) {
          isHave = true
        }
      }

      if (isHave) {
        this.addOrderCount(goods)
      } else {
        let newGoods = {
          goodsId: goods.goodsId,
          goodsName: goods.goodsName,
          price: goods.price,
          count: 1
        }
        this.tableData.push(newGoods)
        this.getCountAndPrice()
      }
    },

    // 商品列表增加商品数量
    addOrderCount (goods) {
      let arr = this.tableData.filter(item => item.goodsId === goods.goodsId)
      arr[0].count++
      this.getCountAndPrice()
    },

    // 计算商品总数和商品总金额
    getCountAndPrice () {
      this.totalPrice = this.totalCount = 0
      this.tableData.forEach((item) => {
        this.totalCount += item.count
        this.totalPrice = this.totalPrice + (item.count * item.price)
      })
    },

    // 删除商品列表单个商品
    deleteSingleOrder (goods) {
      this.tableData = this.tableData.filter(item => item.goodsId !== goods.goodsId)
      this.getCountAndPrice()
    },

    // 删除商品列表全部商品
    deleteAllOrder () {
      this.tableData = []
      this.totalCount = 0
      this.totalPrice = 0
    },

    // 模拟结账
    checkout () {
      if (this.totalCount !== 0) {
        this.deleteAllOrder()
        this.$message({
          message: '结账成功，感谢您为本店出了一份力！',
          type: 'success'
        })
      } else {
        this.$message.error('不能空结账，老板了解您急切的心情！')
      }
    }
  }
}
</script>

<style lang="less">
.pos {
  height: 100%;
  width: 100%;
  text-align: center;

  .order {
    background-color: #F9FAFC;
    border-right: 1px solid #C0CCDA;

    .diancan {
      width: 100%;
    }

    .el-table {
      td, th {
        .cell {
          text-align: center;
        }
      }
    }

    .el-tabs--bottom .el-tabs__item.is-bottom:nth-child(2), .el-tabs--bottom .el-tabs__item.is-top:nth-child(2), .el-tabs--top .el-tabs__item.is-bottom:nth-child(2), .el-tabs--top .el-tabs__item.is-top:nth-child(2) {
      padding-left: 10px;
    }

    .order-btn {
      margin-top: 10px;
    }

    .totallDiv {
      background-color: #fff;
      padding: 10px;
      border-bottom: 1px solid #D3dce6;

      small {
        font-size: 12px;
      }

      .totalPrice {
        margin-left: 40px;
      }
    }
  }

  .shop {
    .common-goods {
      .title {
        text-align: left;
        height: 20px;
        padding: 10px;
        background-color: #F9FAFC;
        border-bottom: 1px solid #D3DCE6;
      }

      .common-goods-list {
        ul {
          li {
            list-style: none;
            float: left;
            border: 1px solid #E5E9F2;
            padding: 10px;
            margin: 10px;
            background-color: #FFF;
            cursor: pointer;

            .good-price {
              color: #58B7FF;
            }
          }
        }
      }
    }

    .goods-type {
      clear: both;

      .cookList{
        margin: 10px 20px;

        li{
          list-style: none;
          width:23%;
          border:1px solid #E5E9F2;
          height: auot;
          overflow: hidden;
          background-color:#fff;
          padding: 2px;
          float:left;
          margin: 2px;
          cursor: pointer;

          span {
            display: block;
            float:left;
          }

          .foodImg{
            width: 40%;
          }

          .foodName{
            font-size: 18px;
            padding-left: 10px;
            color:brown;
          }

          .foodPrice{
            font-size: 16px;
            padding-left: 10px;
            padding-top:10px;
          }
        }
      }
    }

    .el-tabs--top .el-tabs__item.is-top:nth-child(2) {
      padding-left: 10px;
    }
  }
}
</style>
