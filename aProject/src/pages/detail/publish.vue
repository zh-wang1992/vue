<template>
  <div class="sales-board">
    <div class="sales-board-intro">
      <h2>广告发布</h2>

      <p>
        广告活动按照广告计划执行，到完成广告创作并形成广告作品之后，经过广告主的
        最后审核同意，即可送到预定的媒介发布刊播。这项工作一般由媒介部门的有关专
        业人员负责，他们的任务就是专门负责与有关媒介单位接洽，安排有关广告的发播
        事宜，并对发播质量实施监督。</p>
    </div>
    <div class="sales-board-form">
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          购买数量：
        </div>
        <div class="sales-board-line-right">
          <v-counter :max="100" :min="20"
                     @on-change="onParamChange('buyNum',$event)"></v-counter>
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          行业：
        </div>
        <div class="sales-board-line-right">
          <v-selection :selections="tradeList"
                       @on-change="onParamChange('trade',$event)"></v-selection>
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          产品版本：
        </div>
        <div class="sales-board-line-right">
          <v-mul-chooser :selections="versionList"
                         @on-change="onParamChange('versions',$event)"></v-mul-chooser>
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          有效时间：
        </div>
        <div class="sales-board-line-right">
          <v-chooser :selections="periodList"
                     @on-change="onParamChange('period',$event)"></v-chooser>
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">
          总价：
        </div>
        <div class="sales-board-line-right">
          {{price}}元
        </div>
      </div>
      <div class="sales-board-line">
        <div class="sales-board-line-left">&nbsp;</div>
        <div class="sales-board-line-right">
          <div class="button" @click="showPayDialog">
            立即购买
          </div>
        </div>
      </div>
    </div>
    <div class="sales-board-des">
      <h2>产品说明</h2>

      <p>
        广告活动按照广告计划执行，到完成广告创作并形成广告作品之后，
        经过广告主的最后审核同意，即可送到预定的媒介发布刊播。这项工作
        一般由媒介部门的有关专业人员负责，他们的任务就是专门负责与有关
        媒介单位接洽，安排有关广告的发播事宜，并对发播质量实施监督。</p>

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
    <pay-dialog :is-show="isShowPayDialog">
      <table class="buy-dialog-table">
        <tr>
          <th>购买数量</th>
          <th>行业</th>
          <th>产品版本</th>
          <th>有效时间</th>
          <th>总价</th>
        </tr>
        <tr>
          <td>{{buyNum}}</td>
          <td>{{trade.label}}</td>
          <td><span v-for="item in versions">{{item.label}}&nbsp;</span></td>
          <td>{{period.label}}</td>
          <td>{{price}}</td>
        </tr>
      </table>
      <h3 class="buy-dialog-title">请选择银行</h3>
      <bank-chooser @on-change="onChangeBanks"></bank-chooser>
      <div class="button buy-dialog-btn" @click="confirmBuy">确认购买</div>
    </pay-dialog>

    <check-order :is-show-check-dialog="isShowCheckOrder" :order-id="orderId"
                 @on-close-check-dialog="hideCheckOrder"></check-order>
  </div>
</template>

<script>
  import VSelection from '../../components/base/selection'
  import VCounter from '../../components/base/counter'
  import VMulChooser from '../../components/base/multiplyChooser'
  import VChooser from '../../components/base/chooser.vue'
  import PayDialog from '../../components/base/dialog.vue'
  import BankChooser from '../../components/bankChooser.vue'
  import CheckOrder from '../../components/checkOrder.vue'
  export default {
    components: {
      VSelection: VSelection,
      VCounter: VCounter,
      VMulChooser: VMulChooser,
      VChooser: VChooser,
      PayDialog: PayDialog,
      BankChooser: BankChooser,
      CheckOrder: CheckOrder
    },
    data: function () {
      return {
        buyNum: 0,
        trade: {},
        period: {},
        versions: [],
        price: 0,
        orderId: null,
        bankId: null,
        isShowPayDialog: false,
        isShowCheckOrder: false,
        tradeList: [
          {
            label: '出版业',
            value: 0
          },
          {
            label: '媒体',
            value: 1
          },
          {
            label: '金融',
            value: 2
          },
          {
            label: '互联网',
            value: 3
          },
          {
            label: '游戏',
            value: 4
          }
        ],
        versionList: [
          {
            label: '初级版',
            value: 0
          },
          {
            label: '中级版',
            value: 1
          },
          {
            label: '高级版',
            value: 2
          },
          {
            label: '专家版',
            value: 3
          }
        ],
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
      this.buyNum = 1;
      this.trade = this.tradeList[0];
      this.period = this.periodList[0];
      this.versions = [this.versionList[0]]
    },
    methods: {
      onParamChange: function (attr, value) {
        this[attr] = value;
      },
      showPayDialog: function () {
        this.isShowPayDialog = true;
      },
      onChangeBanks: function (obj) {
        this.bankId = obj.id;
      },
      hideCheckOrder: function () {
        this.isShowCheckOrder = false;
      },
      getPrice: function () {
        let buyVersionsArray = this.versions.map(function (item) {
          return item.value;
        });
        let reqParams = {
          buyNumber: this.buyNum,
          trade: this.trade.value,
          period: this.period.value,
          version: buyVersionsArray.join(',')
        };
        this.$http.post('/api/getPrice', reqParams)
          .then(function (res) {
            this.price = res.data.amount;
            // console.log(res.data.amount)
          }, function (err) {
            console.log(err)
          })
      },
      confirmBuy: function () {
        this.isShowCheckOrder = true;
        let buyVersionsArray = this.versions.map(function (item) {
          return item.value;
        });
        let reqParams = {
          buyNumber: this.buyNum,
          period: this.period.value,
          version: buyVersionsArray.join(','),
          bankId: this.bankId
        };
        let self = this;
        this.$http.post('/api/createOrder', reqParams)
          .then(function (res) {
            this.orderId = res.data.orderId;
            this.isShowCheckOrder = true;
            this.isShowPayDialog = false;
          }, function (err) {
            console.log(err);
          })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>

