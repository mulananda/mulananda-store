<template>
  <!-- Header Section Begin -->
  <header class="header-section">
    <div class="header-top">
      <div class="container">
        <div class="ht-left">
          <div class="mail-service">
            <i class="fa fa-envelope"></i> mulanandaa@gmail.com
          </div>
          <div class="phone-service">
            <i class="fa fa-phone"></i> +628 99999999
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="inner-header">
        <div class="row">
          <div class="col-lg-2 col-md-2">
            <div class="logo">
              <a href="./index.html">
                <img src="img/logo_website_mulananda.png" alt />
              </a>
            </div>
          </div>
          <div class="col-lg-7 col-md-7"></div>
          <div class="col-lg-3 text-right col-md-3">
            <ul class="nav-right">
              <li class="cart-icon">
                Keranjang Belanja &nbsp;
                <a href="#">
                  <i class="icon_bag_alt"></i>
                  <span>{{ keranjangUser.length }}</span>
                </a>
                <div class="cart-hover">
                  <div class="select-items">
                    <table>
                      <tbody v-if="keranjangUser.length > 0">
                        <tr v-for="keranjang in keranjangUser" :key="keranjang.id">
                          <td class="si-pic">
                            <img class="photo-item" v-bind:src="keranjang.photo" alt />
                          </td>
                          <td class="si-text">
                            <div class="product-selected">
                              <p>${{ keranjang.price }} x 1</p>
                              <h6>{{ keranjang.name }}</h6>
                            </div>
                          </td>
                          <td @click="removeItem(keranjang.id)" class="si-close">
                            <i class="ti-close"></i>
                          </td>
                        </tr>
                      </tbody>
                      <tbody v-else>
                        <tr>
                          <td>Keranjang Kosong</td>
                        </tr>
                      </tbody>
                    </table>
                  </div>
                  <div class="select-total">
                    <span>total:</span>
                    <h5>${{ totalHarga }}.00</h5>
                  </div>
                  <hr />
                  <div class="select-button">
                    <a href="#" class="primary-btn view-card">
                      <router-link to="/cart" style="color: #FFF;">VIEW CARD</router-link>
                    </a>
                    <!-- <a href="#" class="primary-btn checkout-btn">CHECK OUT</a> -->
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </header>
  <!-- Header End -->
</template>

<script>
export default {
  name: "HeaderStore",
  data() {
    return {
      // untuk keranjang
      keranjangUser: []
    };
  },
  // hapus isi keranjang
  methods: {
    removeItem(xx) {
      // this.keranjangUser.splice(index, 1);
      // const parsed = JSON.stringify(this.keranjangUser);
      // localStorage.setItem("keranjangUser", parsed);
      // window.location.reload();
      let faveGifs = JSON.parse(localStorage.getItem("keranjangUser"));
      let faveGif = faveGifs.map(faveGif => faveGif.id);
      let index = faveGif.findIndex(id => id == xx);
      this.keranjangUser.splice(index, 1);
      const parsed = JSON.stringify(this.keranjangUser);
      localStorage.setItem("keranjangUser", parsed);
      window.location.reload();
      // eslint-disable-next-line no-console
      console.log(index);
    }
  },
  // end hapus isi keranjang
  mounted() {
    // jika dilocal storage item tersedia
    if (localStorage.getItem("keranjangUser")) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
      } catch (e) {
        localStorage.removeItem("keranjangUser");
      }
    }
    // end keranjang
  },
  // menghitung total harga pada keranjang
  computed: {
    totalHarga() {
      return this.keranjangUser.reduce(function(items, data) {
        return items + data.price;
      }, 0);
    }
  }
  // end menghitung total harga pada keranjang
};
</script>
<style scoped>
.photo-item {
  width: 60px;
  height: 80px;
}
</style>