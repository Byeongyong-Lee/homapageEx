<template>
  <header class="header1">
    <!-- Header desktop -->
    <div class="container-menu-header">
      <div class="topbar">
        <div class="topbar-child2">
          <a href="#" class="topbar-item">로그인</a>
          <a href="#" class="topbar-item">회원가입</a>
          <a href="#" class="topbar-item">고객센터</a>
        </div>
      </div>

      <div class="wrap_header">
        <!-- Logo -->
        <a href="index.html" class="logo">
          <img src="images/icons/logo.jpg" alt="IMG-LOGO">
        </a>

        <!-- Menu -->
        <div class="wrap_menu">
          <nav class="menu">
            <ul class="main_menu">
              <router-link :to="{name: 'home'}" tag="li" active-class="sale-noti" exact>
                <a>Men</a>
              </router-link>

              <router-link :to="{name: 'shop'}" tag="li" active-class="sale-noti" exact>
                <a>Women</a>
              </router-link>

              <router-link :to="{name: 'features'}" tag="li" active-class="sale-not" exact>
                <a>Shoes</a>
              </router-link>
            </ul>
          </nav>
        </div>

        <!-- Header Icon -->
        <div class="header-icons">
          <div class="header-wrapicon1" >
            <img @mouseover="showDropDown" @mouseleave="closeDropDown" src="images/icons/icon-header-01.png" class="header-icon1" alt="ICON">
            <!-- Header dropdown -->
            <div id="dropdown" class="header-dropdown" @mouseover="showDropDown" @mouseleave="closeDropDown" v-show="active">
              <li>
                <a href="#" class="topbar-item">주문/배송내역</a>
              </li>
              <li>
                <a href="#" class="topbar-item">취소/반품/교환신청</a>
              </li>
              <li>
                <a href="#" class="topbar-item">실시간채팅문의</a>
              </li>
            </div>
          </div>

          <span class="linedivide1"></span>

          <div class="header-wrapicon2">
            <a href="#">
              <img src="images/icons/icon-header-02.png" class="header-icon2" alt="ICON">
            </a>
            <span class="header-icons-noti">{{ totalCartQty }}</span>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
<script>
import {mapState, mapGetters} from 'vuex';

export default {
  name: "Header",
  computed: {
    ...mapState('cart', {
      cartItems: state => state.items
    }),
    ...mapGetters('cart', {
      totalCartPrice: 'totalPrice',
      totalCartQty: 'totalQty'
    })
  },
  data(){
    return{
      active: false
    }
  },
  methods: {
    showDropDown(){
      this.active = true;
    },
    closeDropDown(){
      this.active = false;
    }
  }
}
</script>