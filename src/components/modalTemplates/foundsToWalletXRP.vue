<template>
  <div class="beModal">
    <div class="beModal__header">
      <div class="beModal__close">
        <div slot="top-right">
          <button @click="$modal.hide('modal')">
            <i class="icon-close"></i>
          </button>
        </div>
      </div>
    </div>
    <vueCustomScrollbar
      class="modal_scroll rail__normal"
      :settings="{
        wheelPropagation: false,
        suppressScrollX: true,
      }"
    >
      <div class="beModal__body text-center">
        <h2 class="beModal__title">Receive XRP</h2>
        <beSelect
          :selectArray="selectList"
          v-model="selectedItem"
          class="wallet_select text--black"
        >
          <span slot="small_text">X 354.12</span>
        </beSelect>
        <div class="beModal__qr_code">
          <img src="/images/client/qr.svg" alt="" />
        </div>
        <div class="qr_code__label">Your XRP Address</div>
        <beCopyText
          :bordered="true"
          class="walet__hash"
          text="13tL5oHakHbsv1kGUtkLuE4hkyzGcyijmt"
        ></beCopyText>
      </div>
      <div class="beModal__footer text-center">
        <beButton
          type="button"
          title="Confirm"
          class="confirm_button"
          :shadow="true"
          @click="confirmSending"
        ></beButton>
      </div>
    </vueCustomScrollbar>
  </div>
</template>
<script>
import { mapGetters } from "vuex";
export default {
  data() {
    return {
      selectList: null,
      selectedItem: null,
    };
  },
  computed: {
    ...mapGetters({
      getSelectList: "lists/getSelectList",
      getSelectedItem: "lists/getSelectedItem",
    }),
  },
  created() {
    this.selectList = this.getSelectList;
    this.selectedItem = this.getSelectedItem;
  },
  methods: {
    confirmSending() {
      this.$modal.hide("modal");
      this.$modal.show("modal-confirm");
    },
  },
};
</script>
