<template>
  <div class="footer">
    <div class="container">
      <div class="footer-blocks">
        <div class="block">
          <div class="heading">Quick Links</div>
          <div class="link">Sublink</div>
          <div class="link">Sublink</div>
          <div class="link">Sublink</div>
          <div class="link">Sublink</div>
        </div>
        <div class="block">
          <div class="heading">Get In Touch</div>
          <div class="link">yourbusiness@yourdomain.com</div>
          <div class="link">Your phone number</div>
        </div>
        <div class="block">
          <div class="heading">Newsletter</div>
          <div class="mb-12 subheading">
            Keep up to date with our latest offers, events and promotions
          </div>
          <Input
            :model.sync="email"
            :background="'transparent'"
            :border="'1px solid white'"
            :placeholder="'Email'"
            class="mb-8"
          />
          <Button
            :text="'Subscribe'"
            :width="'100%'"
            :text-colour="'white'"
            :background="'transparent'"
            :border="'1px solid white'"
            :height="'30px'"
          />
        </div>
      </div>
      <div class="flex col w-100 align-center mt-48">
        <div class="copyright">Copyright © 2022 Your Business Name</div>
        <div class="address mb-12">House number, street address, postcode in Area</div>
        <div class="flex">
          <img
            class="payment-icon"
            src="~/assets/icons/payments/amex.svg"
            alt="amex"
          />
          <img
            class="payment-icon"
            src="~/assets/icons/payments/apple-pay.svg"
            alt="apple-pay"
          />
          <img
            class="payment-icon"
            src="~/assets/icons/payments/mastercard.svg"
            alt="mastercard"
          />
          <img
            class="payment-icon"
            src="~/assets/icons/payments/visa.svg"
            alt="visa"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      email: "",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/components/footer";
</style>