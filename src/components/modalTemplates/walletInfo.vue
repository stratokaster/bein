<template>
  <div class="beModal">
    <div class="beModal__header">
      <div class="beModal__close">
        <div slot="top-right">
          <button @click="$modal.hideAll()">
            <i class="icon-close"></i>
          </button>
        </div>
      </div>
    </div>
    <div class="beModal__body">
      <div
        class="card wallet card--bg-lines"
        :class="waletUSDX ? 'card--gradient-purple' : 'card--gradient'"
      >
        <div class="wallet__header">
          <div class="wallet__icon"><i class="icon-wallet-outline"></i></div>
          <div class="balance__info">
            <div class="balance__actual">
              <div class="atual__item">
                <!-- <small class="balance__currancy" v-if="!waletUSDX"><i class="icon-currancy"></i></small> -->
                12,021<small
                  >.{{ 23 || "00" }}
                  <span v-if="waletUSDX">BIXRP</span>
                  <span v-else>XRP</span>
                </small>
              </div>
            </div>
            <div class="balance__title">{{ waletName }}</div>
          </div>
        </div>
        <div class="wallet__body"></div>
        <div class="btns wallet__footer row-flex">
          <beButton
            class="flex-full"
            type="button"
            title="Send"
            :outline="true"
            :white="true"
            ><i class="icon-sign-out" slot="icon-left"></i
          ></beButton>
          <beButton
            type="button"
            title="Receive"
            :outline="false"
            :white="true"
            class="ml10 flex-full"
            ><i class="icon-sign-in" slot="icon-left"></i
          ></beButton>
        </div>
      </div>
      <div class="mt40" v-if="getHistory">
        <vueCustomScrollbar
          class="modal_history__wrapper rail__normal"
          :settings="{
            wheelPropagation: false,
          }"
        >
          <div
            class="history"
            v-for="(item, idx) in getHistory"
            :key="idx"
            :class="[
              item.status == 'Rejected'
                ? 'alert'
                : item.status == 'Approved'
                ? 'success'
                : 'inprogress',
            ]"
          >
            <div class="history__date">{{ item.date }}</div>
            <div class="history__planish_link">
              <button class="wallet_btn">
                <span v-if="item.buttonText === 'Wallet replenishment'"
                  ><i class="icon-sign-in" slot="icon-left"></i
                ></span>
                <span v-else
                  ><i class="icon-sign-out" slot="icon-left"></i
                ></span>
                <span class="wallet_btn__text">
                  <span class="wallet_btn__title">{{ item.buttonText }}</span>
                  <span class="wallet__name">Wallet: {{ item.waletName }}</span>
                </span>
              </button>
            </div>
            <div class="history__status">{{ item.status }}</div>
            <div class="history__finance">
              {{ item.summ }}
              <small>{{ item.currency == 1 ? "BIXRP" : "XRP" }}</small>
            </div>
          </div>
        </vueCustomScrollbar>
      </div>
      <div class="transactions__body empty" v-else>
        <div class="card card--white text-center">
          <p class="icon"><i class="icon-smile-sad"></i></p>
          <p class="empty__text">You don't have any transactions yet</p>
        </div>
      </div>
    </div>
    <div class="beModal__footer"></div>
  </div>
</template>
<script>
import { mapGetters } from "vuex";
export default {
  props: {
    waletName: {
      default: "",
    },
    waletUSDX: {
      default: false,
    },
  },
  data() {
    return {
      getHistory: {
        "Apr 10, 2021": [
          {
            id: 1,
            from: "-10.214 XRP",
            to: "+90.78 BIXRP",
            usd: "$102.83",
            status: "complete",
          },
          {
            id: 2,
            from: "-10.214 XRP",
            to: "+90.78 BIXRP",
            usd: "$102.83",
            status: "rejected",
          },
          {
            id: 3,
            from: "-10.214 XRP",
            to: "+90.78 BIXRP",
            usd: "$102.83",
            status: "waiting",
          },
        ],
        "Apr 11, 2021": [
          {
            id: 4,
            from: "-10.214 XRP",
            to: "+90.78 BIXRP",
            usd: "$102.83",
            status: "rejected",
          },
        ],
        "Apr 12, 2021": [
          {
            id: 5,
            from: "-10.214 XRP",
            to: "+90.78 BIXRP",
            usd: "$102.83",
            status: "rejected",
          },
        ],
      },
    };
  },
};
</script>
<style lang="scss" scoped>
@media (max-width: 767px) {
  .beModal__close {
    top: -60px;
    right: -10px;
    background-color: #fff;
    border-radius: 50%;
  }
}
.wallet {
  max-width: 515px;
  margin: -105px auto 0;
  @media (max-width: 767px) {
    margin: -75px auto 0;
  }
  &__header {
    margin-bottom: 80px;
  }
}
.history {
  border-bottom: 1px solid #c4c4c4;
  margin-bottom: 0px;
  padding: 10px;
  @media (max-width: 767px) {
    padding-bottom: 40px;
  }
}
.modal_history__wrapper {
  height: 35vh;
  margin: 0 -40px;
  padding: 0 40px;
  @media (max-width: 767px) {
    margin: 0 -30px;
    padding: 0 0px;
  }
}
</style>
