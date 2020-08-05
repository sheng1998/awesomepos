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
                  <template>
                    <el-button type="text" size="small">删除</el-button>
                    <el-button type="text" size="small">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
              <div class="order-btn">
                <el-button type="warning">挂单</el-button>
                <el-button type="danger">删除</el-button>
                <el-button type="success">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单">配置管理</el-tab-pane>
            <el-tab-pane label="外卖">角色管理</el-tab-pane>
          </el-tabs>
        </el-col>
        <el-col :span="17" class="shop">
          <div class="common-goods">
            <div class="title">常用商品</div>
            <div class="common-goods-list">
              <ul>
                <li v-for="item in commonGoods" :key="item.goodsId">
                  <span class="good-name">{{ item.goodsName }}</span>
                  <span class="good-price">￥{{ item.price }}元</span>
                </li>
              </ul>
            </div>
          </div>
          <div class="goods-type">
            <el-tabs>
              <el-tab-pane label="汉堡">
                <ul class='cookList'>
                  <li v-for="item in typeGoods" :key="item.goodsId">
                    <span class="foodImg">
                      <img :src="item.goodsImg" width="100%">
                    </span>
                    <span class="foodName">{{ item.goodsName }}</span>
                    <span class="foodPrice">￥{{ item.price }}.00元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="小食">小食</el-tab-pane>
              <el-tab-pane label="饮料">饮料</el-tab-pane>
              <el-tab-pane label="套餐">套餐</el-tab-pane>
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
      tableData: [
        {
          goodsName: '可口可乐',
          price: 8,
          count: 1
        },
        {
          goodsName: '香辣鸡腿堡',
          price: 15,
          count: 1
        },
        {
          goodsName: '爱心薯条',
          price: 8,
          count: 1
        },
        {
          goodsName: '甜筒',
          price: 8,
          count: 1
        }
      ],

      commonGoods: [
        {
          goodsId: 1,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 2,
          goodsName: '田园鸡腿堡',
          price: 15
        },
        {
          goodsId: 3,
          goodsName: '和风汉堡',
          price: 15
        },
        {
          goodsId: 4,
          goodsName: '快乐全家桶',
          price: 80
        },
        {
          goodsId: 5,
          goodsName: '脆皮炸鸡腿',
          price: 10
        },
        {
          goodsId: 6,
          goodsName: '魔法鸡块',
          price: 20
        },
        {
          goodsId: 7,
          goodsName: '可乐大杯',
          price: 10
        },
        {
          goodsId: 8,
          goodsName: '雪顶咖啡',
          price: 18
        },
        {
          goodsId: 9,
          goodsName: '大块鸡米花',
          price: 15
        },
        {
          goodsId: 20,
          goodsName: '香脆鸡柳',
          price: 17
        }
      ],

      typeGoods: [
        {
          goodsId: 1,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '香辣鸡腿堡',
          price: 18
        }, {
          goodsId: 2,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '田园鸡腿堡',
          price: 15
        }, {
          goodsId: 3,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '和风汉堡',
          price: 15
        }, {
          goodsId: 4,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '快乐全家桶',
          price: 80
        }, {
          goodsId: 5,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '脆皮炸鸡腿',
          price: 10
        }, {
          goodsId: 6,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '魔法鸡块',
          price: 20
        }, {
          goodsId: 7,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '可乐大杯',
          price: 10
        }, {
          goodsId: 8,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '雪顶咖啡',
          price: 18
        }, {
          goodsId: 9,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '大块鸡米花',
          price: 15
        }, {
          goodsId: 20,
          goodsImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1596631975621&di=6ec945ccfb017978eeea0214321c0fe3&imgtype=0&src=http%3A%2F%2Fa2.att.hudong.com%2F36%2F48%2F19300001357258133412489354717.jpg',
          goodsName: '香脆鸡柳',
          price: 17
        }
      ]
    }
  },
  mounted: function () {
    var orderHeight = document.body.clientHeight
    this.$refs.order.$el.style.height = orderHeight + 'px'
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
