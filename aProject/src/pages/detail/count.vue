<template>
  <div class="sales-board">
    <div class="sales-board-intro">
      <h2>数据统计</h2>

      <p>历史资料、科学实验、检验、统计等所获得的和用于科学研究、
        技术设计、查证、决策等的数值加以统计为解决方案做前期准备。
      </p>
    </div>
    <div class="sales-board-form">
      <div class="sales-board-line">
        <div class="sales-board-line-left">购买数量</div>
        <div class="sales-board-line-right">
          <v-counter :max="buyNumberRange.max" :min="buyNumberRange.min"
                     @on-change="onParamChange('buyNum',$event)"></v-counter>
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">产品类型</div>
        <v-selection :selections="buyTypes"
                     @on-change="onParamChange('buyType',$event)"></v-selection>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">适用地区</div>
        <v-mul-chooser :selections="districtsList"
                       @on-change="onParamChange('districts',$event)"></v-mul-chooser>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          有效时间
        </div>
        <div class="sales-board-line-right">
          <v-chooser :selections="periodList"
                     @on-change="onParamChange('period',$event)"></v-chooser>
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          总价
        </div>
        <div class="sales-board-line-left">
          {{price}}
        </div>
      </div>
      <div class="sale-board-line">
        <div class="sales-board-line-left">
          &nbsp;
        </div>
        <div class="sales-board-line-right">
          <div class="button" @click="showPayDialog">
            立即购买
          </div>
        </div>
      </div>
    </div>
    <div class="sales-board-des">
      <h2>产品说明</h2>

      <p>历史资料、科学实验、检验、统计等所获得的和用于科学研究、技术设计、
        查证、决策等的数值加以统计为解决方案做前期准备。
      </p>
      <table class="sales-board-table">
        <tbody>
        <tr class="ui-table-row">
          <td class="col-first">
            <div class="intro-pic">
              <label>安全安保</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>办公文教</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>彩票</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>车辆物流</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>成人用品</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>出版传媒</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>电脑硬件</label>
            </div>
          </td>
        </tr>
        <tr class="ui-table-row">
          <td class="col-first">
            <div class="intro-pic">
              <label>电子电工</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>房地产建筑装修</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>分类平台</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>服装鞋帽</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>箱包饰品</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>化工原料制品</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>机械设备</label>
            </div>
          </td>
        </tr>
        <tr class="ui-table-row">
          <td class="col-first">
            <div class="intro-pic">
              <label>家庭日用品</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>家用电器</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>教育培训</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>节能环保</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>金融服务</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>礼品</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>旅游住宿</label>
            </div>
          </td>
        </tr>
        <tr class="ui-table-row">
          <td class="col-first">
            <div class="intro-pic">
              <label>美容化妆</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>母婴护理</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>农林牧渔</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>软件</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>商务服务</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>生活服务</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>食品保健品</label>
            </div>
          </td>
        </tr>
        <tr class="ui-table-row">
          <td class="col-first">
            <div class="intro-pic">
              <label>手机数码</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>通讯服务设备</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>网络服务</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>医疗服务</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>游戏</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>运动休闲娱乐</label>
            </div>
          </td>
          <td>
            <div class="intro-pic">
              <label>招商加盟</label>
            </div>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
    <pay-dialog :is-show="isShowPayDialog" @on-close="hidePayDialog">
      <table class="buy-dialog-table">
        <tr>
          <th>购买数量</th>
          <th>产品类型</th>
          <th>适用地区</th>
          <th>有效时间</th>
          <th>总价</th>
        </tr>
        <tr>
          <td>{{buyNum}}</td>
          <td>{{buyType.label}}</td>
          <td>
            <span v-for="item in districts">{{item.label}}&nbsp;</span>
          </td>
          <td>{{period.label}}</td>
          <td>{{price}}</td>
        </tr>
      </table>
      <h3>请选择银行</h3>
      <bank-chooser @on-change="onChangeBanks"></bank-chooser>
      <div class="button buy-dialog-btn" @click="confirmBuy">确认购买</div>
    </pay-dialog>
    <check-order :is-show-check-dialog="isShowCheckDialog" :order-id="orderId"
                 @on-close-check-dialog="hideCheckOrder"></check-order>
  </div>
</template>

<script>
  import VCounter from '../../components/base/counter.vue'
  import VSelection from '../../components/base/selection.vue'
  import VChooser from '../../components/base/chooser.vue'
  import Dialog from '../../components/base/dialog.vue'
  import VMulChooser from '../../components/base/multiplyChooser.vue'
  import BankChooser from '../../components/bankChooser.vue'
  import CheckOrder from '../../components/checkOrder.vue'
  export default {
    components: {
      VCounter: VCounter,
      VSelection: VSelection,
      VChooser: VChooser,
      VMulChooser: VMulChooser,
      PayDialog: Dialog,
      BankChooser: BankChooser,
      CheckOrder: CheckOrder
    },
    data: function () {
      return {
        buyNum: 0,
        buyType: {},
        districts: [],
        period: {},
        bankId: '',
        orderId: null,
        price: 0,
        isShowPayDialog: false,
        isShowCheckDialog: false,
        buyNumberRange: {
          max: 6,
          min: 1
        },
        buyTypes: [
          {
            label: '红色版',
            value: 0
          },
          {
            label: '绿色版',
            value: 1
          },
          {
            label: '紫色版',
            value: 2
          }
        ],
        districtsList: [{
          label: '北京',
          value: 0
        }, {
          label: '上海',
          value: 1
        }, {
          label: '广州',
          value: 2
        }],
        periodList: [{
          label: '半年',
          value: 0
        }, {
          label: '一年',
          value: 1
        }, {
          label: '三年',
          value: 2
        }]
      }
    },
    mounted: function () {
      this.buyNum = 0;
      this.buyType = this.buyTypes[0];
      this.period = this.periodList[0];
      this.districts = [this.districtsList[0]]
      this.getPrice();
    },
    methods: {
      onParamChange: function (attr, value) {
        this[attr] = value;
      },
      getPrice: function () {
        let buyDistrictsArray = this.districts.map(function (item) {
          return item.value;
        });
        let reqParams = {
          buyNumber: this.buyNum,
          buyType: this.buyType.value,
          period: this.period.value,
          district: buyDistrictsArray.join(',')
        };
        this.$http.post('/api/getPrice', reqParams)
          .then(function (res) {
            this.price = res.data.amount;
          }, function (err) {
            console.log(err)
          })
      },
      showPayDialog: function () {
        this.isShowPayDialog = true;
      },
      hidePayDialog: function () {
        this.isShowPayDialog = false;
      },
      onChangeBanks: function (obj) {
        this.bankId = obj.id;
      },
      confirmBuy: function () {
        let buyDistrictsArray = this.districts.map(function (item) {
          return item.value;
        });
        let reqParams = {
          buyNumber: this.buyNum,
          buyType: this.buyType.value,
          period: this.period.value,
          district: buyDistrictsArray.join(','),
          bankId: this.bankId
        };
        let self = this;
        this.$http.post('/api/createOrder', reqParams)
          .then(function (res) {
            self.isShowCheckDialog = true;
            self.isShowPayDialog = false;
          }, function (err) {
            console.log(err)
          });

      },
      hideCheckOrder: function () {
        this.isShowCheckDialog = false
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
