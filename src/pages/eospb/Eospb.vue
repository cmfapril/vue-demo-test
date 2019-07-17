<template>
  <div class="container">
    <div class="content">
      <div class="top">
        <div class="header">
          <a-row :gutter="8">
            <a-col :span="8">
              <img alt="logo" class="logo" src="static/img/golden-ticket-sm.png" />
              <span class="title">JACKPOT</span>
            </a-col>
            <a-col :span="8" style="padding-left: 4px">
              <span class="title">$10,773.39动态的</span>
            </a-col>
            <a-col :span="8" style="padding-left: 4px">
              <span class="title">0000000</span>
            </a-col>
          </a-row>
        </div>
      </div>
      <div class="tabContent">
        <a-form @submit="onSubmit" :autoFormCreate="(form) => this.form = form">
          <a-tabs size="large" :tabBarStyle="{textAlign: 'center'}" style="padding: 0 2px;">
            <a-tab-pane tab="Manual Bet手动投注" key="1">
              <div class="betbox">
                <a-row :gutter="8" style=" text-align: center;" class="row">
                  <a>HOW TO PLAY</a>
                </a-row>

                <a-divider style="margin-bottom: 32px" />

                <a-row :gutter="8" class="row">
                  <a-col :span="12">
                    <a-row>
                      <span class="title">Bet amount</span>
                      <div>
                        <a-col :span="12">
                          <a-input-number
                            size="large"
                            :min="1"
                            :max="99999999999"
                            v-model="betAmount"
                            style="width:80%"
                          />
                        </a-col>
                        <a-col :span="12" >
                          <a-row :gutter="8">
                            <a-col :span="4">
                              <a @click="toggleCheck(1/2)">1/2</a>
                            </a-col>

                            <a-col :span="4">
                              <a @click="toggleCheck()">2X</a>
                            </a-col>

                            <a-col :span="4">
                              <a @click="toggleCheck()">max</a>
                            </a-col>
                          </a-row>
                        </a-col>
                      </div>
                    </a-row>
                  </a-col>

                  <a-col :span="12">
                    <a-row>
                      <a-col :span="6">
                        <span class="title">
                          JACKPOT
                          <a-icon type="question-circle" />
                        </span>
                        <a-checkbox style="width:80%" :checked="checked" :disabled="disabled"  @change="onCheckboxChange"></a-checkbox>
                      </a-col>
                      <a-col :span="18" style="padding-left: 30px;">
                        <span class="title">payout on win</span>
                        </br>
                        <span>{{betAmount * 1.2222}} </span>
                      </a-col>
                    </a-row>
                  </a-col>
                </a-row>
                <a-divider style="margin-bottom: 32px" />
                <a-row :gutter="8" class="row">
                  <a-col :span="8">
                    <span class="bet-desc">roll under</span>
                    <br />
                    <span class="bet-amount">{{percentage -1}}</span>
                  </a-col>
                  <a-col :span="8">
                    <span class="bet-desc">payout</span>
                    <br />
                    <span class="bet-amount">1.52X</span>
                  </a-col>
                  <a-col :span="8">
                    <span class="bet-desc">wincharge</span>
                    <br />
                    <span class="bet-amount">{{percentage}}%   </span>
                  </a-col>
                </a-row>
                <a-divider style="margin-bottom: 32px" />
                <a-row :gutter="8" class="row">
                  <a-col :span="8">
                    <span class="balance-amount">66</span>
                  </a-col>
                  <a-col :span="8">
                    <a-button
                      style="width: 60%;margin-bottom: 20px;"
                      size="middle"
                      type="primary"
                    >get started</a-button>
                  </a-col>
                  <a-col :span="8">
                    <span class="title">{{percentage}}%  <a-icon type="question-circle" /> </span>
                  </a-col>
                </a-row>
              </div>
            </a-tab-pane>
            <a-tab-pane tab="Atuo Bet 自动投注" key="2">

              <div class="betbox">
                <a-row :gutter="8" style=" text-align: center;" class="row">
                  <a>HOW TO PLAY</a>
                </a-row>

                <a-divider style="margin-bottom: 32px" />

                <a-row :gutter="8" class="row">
                  <a-col :span="12">
                    <a-row>
                      <span class="title">Bet amount</span>
                      <div>
                        <a-col :span="12">
                          <a-input-number
                            size="large"
                            :min="0.0000"
                            :max="99999999999"
                            :step="0.0001"
                            v-model="betAmount"
                            style="width:80%"
                          />
                        </a-col>
                        <a-col :span="12" >
                          <a-row :gutter="8">
                            <a-col :span="4">
                              <a @click="toggleCheck(1/2)">1/2</a>
                            </a-col>

                            <a-col :span="4">
                              <a @click="toggleCheck()">2X</a>
                            </a-col>

                            <a-col :span="4">
                              <a @click="toggleCheck()">max</a>
                            </a-col>
                          </a-row>
                        </a-col>
                      </div>
                    </a-row>
                  </a-col>

                  <a-col :span="12">
                    <a-row>
                      <a-col :span="6">
                        <span class="title">
                          JACKPOT
                          <a-icon type="question-circle" />
                        </span>
                        <a-checkbox style="width:80%" :checked="checked" :disabled="disabled"  @change="onCheckboxChange"></a-checkbox>
                      </a-col>
                      <a-col :span="18" style="padding-left: 30px;">
                        <span class="title">MAX # OF GAMES</span>
                        </br>
                        <a-input-number
                          size="large"
                          :min="0"
                          :max="99999999999"
                          v-model="betAmount"
                          style="width:70%"
                        />
                        <span>NO LIMIT </span>
                      </a-col>
                    </a-row>
                  </a-col>
                </a-row>
                <a-divider style="margin-bottom: 32px" />
                <a-row :gutter="8" class="row">
                  <a-col :span="8">
                    <span class="bet-desc">roll under</span>
                    <br />
                    <span class="bet-amount">{{percentage -1}}</span>
                  </a-col>
                  <a-col :span="8">
                    <span class="bet-desc">payout</span>
                    <br />
                    <span class="bet-amount">1.52X</span>
                  </a-col>
                  <a-col :span="8">
                    <span class="bet-desc">wincharge</span>
                    <br />
                    <span class="bet-amount">{{percentage}}%   </span>
                  </a-col>
                </a-row>
                <a-divider style="margin-bottom: 32px" />
                <a-row :gutter="16" class="row">
                  <a-col :span="16">
                    <span class="bet-desc">ON WIN</span>
                    <br />
                    <a-input-number
                      :min="0"
                      :max="100"
                      :formatter="winValue => `%${winValue}`"
                      v-model="winValue"
                      style="width:70%"
                    />
                  </a-col>

                </a-row>
                <a-divider style="margin-bottom: 32px"/>
                <a-row :gutter="8" class="row">
                  <a-col :span="8">
                    <span class="balance-amount">66</span>
                  </a-col>
                  <a-col :span="8">
                    <!--<a-button-->
                      <!--style="width: 60%;margin-bottom: 20px;"-->
                      <!--size="middle"-->
                      <!--type="primary"-->
                    <!--&gt;get started</a-button>-->
                  </a-col>
                  <a-col :span="8">
                    <span class="title">{{percentage}}%  <a-icon type="question-circle" /> </span>
                  </a-col>
                </a-row>
              </div>

              <!--<a-form-item>-->
                <!--<a-input size="large" placeholder="mobile number">-->
                  <!--<a-icon slot="prefix" type="mobile" />-->
                <!--</a-input>-->
              <!--</a-form-item>-->
              <!--<a-form-item>-->
                <!--<a-row :gutter="8" style="margin: 0 -4px">-->
                  <!--<a-col :span="16">-->
                    <!--<a-input size="large" placeholder="captcha">-->
                      <!--<a-icon slot="prefix" type="mail" />-->
                    <!--</a-input>-->
                  <!--</a-col>-->
                  <!--<a-col :span="8" style="padding-left: 4px">-->
                    <!--<a-button style="width: 100%" class="captcha-button" size="large">获取验证码</a-button>-->
                  <!--</a-col>-->
                <!--</a-row>-->
              <!--</a-form-item>-->
            </a-tab-pane>
          </a-tabs>

          <div style="margin-top: 36px">
            <a-row :gutter="8" style="margin: 0 -4px">
              <a-col :span="24">
                <a-slider
                  :tooltipVisible="true"
                  :min="2"
                  :max="98"
                  :marks="marks"
                  v-model="percentage"
                  style="width:90%"
                />
              </a-col>
            </a-row>
          </div>
        </a-form>
      </div>
    </div>

    <!-- <global-footer :link-list="linkList" :copyright="copyright" /> -->
  </div>
</template>

<script>
import GlobalFooter from "../../layouts/GlobalFooter";
import ARow from "ant-design-vue/es/grid/Row";

export default {
  name: "Eospb",
  components: {ARow, GlobalFooter },
  data() {
    return {
      logging: false,
      error: "",
      percentage: 50,
      marks: {
        0: "0",
        100: {
          style: {
            color: "#f50"
          },
          label: <strong>100</strong>
        }
      },

      betAmount: 1, // 投注金额
      // 赢得的金额
      payWinAmount: 1,
      checked:false,
      disabled:true,
      winValue:0,// 赢得金额
      lossValue:0,//输的金额
    };
  },
  computed: {
    systemName() {
      return this.$store.state.setting.systemName;
    },
    linkList() {
      return this.$store.state.setting.footerLinks;
    },
    copyright() {
      return this.$store.state.setting.copyright;
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          this.logging = true;
          this.$axios
            .post("/login", {
              name: this.form.getFieldValue("name"),
              password: this.form.getFieldValue("password")
            })
            .then(res => {
              this.logging = false;
              const result = res.data;
              if (result.code >= 0) {
                const user = result.data.user;
                this.$router.push("/dashboard/workplace");
                this.$store.commit("account/setuser", user);
                this.$message.success(result.message, 3);
              } else {
                this.error = result.message;
              }
            });
        }
      });
    },
    toggleCheck(num) {
      if(num ===1/2) {
        console.log(num);
        this.disabled = false;
        //this.checked = ! this.checked;


      }else{
        this.disabled = true;
        this.checked = false;
      }
    },
    onCheckboxChange(e){
      this.checked = e.target.checked
    },

  }
};
</script>

<style lang="less" scoped>
.container {
  display: flex;
  flex-direction: column;
  height: 100vh;
  overflow: auto;
  background: #f0f2f5
    url("https://gw.alipayobjects.com/zos/rmsportal/TVYTbAXWheQpRcWDaDMu.svg")
    no-repeat center 110px;
  background-size: 100%;
  .content {
    padding: 32px 0;
    flex: 1;
    @media (min-width: 768px) {
      padding: 112px 0 24px;
    }
    .top {
      text-align: center;
      .header {
        width: 60%;
        margin: 0 auto;
        height: 44;
        //line-height: 44px;
        border: 2px solid #fecd4b;
        border-radius: 8px;
        cursor: pointer;
        a {
          text-decoration: none;
        }
        .logo {
          height: 28px;
          vertical-align: middle;
          padding-left: 4px;
          border-style: none;
        }
        .title {
          font-size: 16px;
          font-family: "Myriad Pro", "Helvetica Neue", Arial, Helvetica,
            sans-serif;
          font-weight: 600;
          position: relative;
          top: 2px;
          color: #fecd4b !important;
        }
      }
      .desc {
        font-size: 14px;
        color: rgba(0, 0, 0, 0.45);
        margin-top: 12px;
        margin-bottom: 40px;
      }
    }
    .tabContent {
      width: 60%;
      margin: 0 auto;
      @media screen and (max-width: 576px) {
        width: 95%;
      }
      @media screen and (max-width: 320px) {
        .captcha-button {
          font-size: 14px;
        }
      }
      .icon {
        font-size: 24px;
        color: rgba(0, 0, 0, 0.2);
        margin-left: 16px;
        vertical-align: middle;
        cursor: pointer;
        transition: color 0.3s;

        &:hover {
          color: #1890ff;
        }
      }

      .betbox {
        background: #063464;
        color: #fff;
        font-weight: 500;
        border-radius: 10px;
        .row {
          display: flex;
          flex-wrap: wrap;
          display: block;
          padding-left: 15px;
          padding-right: 15px;
        }
        .bet-amount {
          font-size: 28px;
          border-radius: 5px;
          display: inline-block;
          color: #dde0e3;
        }
        .bet-desc {
          color: #6685a5;
          font-size: 14px;
          font-weight: 600;
          margin-top: 10px;
        }
        .balance-amount {
          font-size: 16px;
        }
      }
    }
  }
}
</style>
