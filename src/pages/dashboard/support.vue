<template>
  <div
    class="
      support
      full-height
      col-flex
      align-items-center
      justify-content-center
    "
  >
    <button class="go-back" @click.prevent="$router.go(-1)" type="button">
      <i class="icon-arrow-left-middle"></i>
    </button>
    <h1 class="page__title">
      <i class="page__title_icon icon-about"></i>
      Support
    </h1>
    <div class="row flex-full">
      <div class="col-6 card card--white col-flex">
        <h2 class="mb15">Support Service</h2>
        <p>
          Please leave a message and we'll happily address your issues. You will
          get our reply via the email indicated on your profile
        </p>
        <div class="flex-full">
          <textarea class="textarea" placeholder="Your message"></textarea>
          <beInputFile
            v-model="files"
            :isButton="false"
            label="Attach file"
            class="attach"
          >
            <i slot="attach-icon" class="icon-attach"></i>
            <i slot="delete" class="icon-close"></i>
          </beInputFile>
        </div>
        <div>
          <beButton title="Send" @click="sendMessage"></beButton>
        </div>
      </div>
      <div class="col-6 card card--white col-flex">
        <h2 class="mb35">
          You can also find answers to common questions here:
        </h2>
        <div class="row flex-full">
          <div class="col-6">
            <h3 class="title__devider">Investments</h3>
            <ul class="support__issues">
              <li><a href="#">Glossary</a></li>
              <li><a href="#">How we accrue percentages</a></li>
              <li><a href="#">How much you can earn?</a></li>
              <li><a href="#">Deposit opening</a></li>
              <li><a href="#">How to use the calculator</a></li>
              <li>
                <a href="#">How to withdraw from the balance of investment</a>
              </li>
            </ul>
          </div>
          <div class="col-6">
            <h3 class="title__devider">Wallets</h3>
            <ul class="support__issues">
              <li><a href="#">Creating a Wallet</a></li>
              <li><a href="#">Replenish wallet</a></li>
              <li><a href="#">"Money gone - balance not replenished."</a></li>
              <li><a href="#">Withdrawing money from a wallet</a></li>
              <li><a href="#">Be in Wallet - the best exchanger</a></li>
            </ul>
          </div>
        </div>
        <div>
          <beButton
            title="Read more"
            :outline="true"
            :arrowRight="true"
          ></beButton>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import transactionsSend from "@/components/modalTemplates/transactionsSend";
export default {
  layout: "lClient",
  data() {
    return {
      files: null,
    };
  },
  methods: {
    sendMessage() {
      this.$modal.show(
        transactionsSend,
        {
          successTitle: "Your message has been sent to the support service!",
          successText:
            "You will receive an answer to the email indicated in your profile. You can communicate with the support agent by replying to the email.",
          buttonText: "Continue",
        },
        { height: "auto", width: "90%", maxWidth: 540, adaptive: true }
      );
    },
  },
};
</script>
