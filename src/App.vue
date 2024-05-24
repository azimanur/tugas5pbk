<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-pink-custom text-white" height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img
              src="https://i.pinimg.com/474x/73/3f/78/733f787fc774c95712c980536e62cce3.jpg"
            />
          </q-avatar>
          NA Store
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/page1" label="Beranda" />
        <q-route-tab to="/page2" label="Produk" />
        <q-route-tab to="/page2" label="Kontak" />
        <q-route-tab to="/page2" label="Tentang Kami" />
      </q-tabs>
    </q-header>

    <q-page-container>
      <div class="content-wrapper q-pa-md">
        <div class="carousel-wrapper">
          <q-carousel
            v-model="slide"
            vertical
            transition-prev="slide-down"
            transition-next="slide-up"
            swipeable
            animated
            control-color="white"
            navigation-icon="radio_button_unchecked"
            navigation
            padding
            arrows
            height="600px"
            class="bg-purple text-white shadow-1 rounded-borders"
          >
            <q-carousel-slide
              v-for="image in images"
              :key="image.name"
              :name="image.name"
              class="carousel-slide"
            >
              <div class="carousel-image-wrapper">
                <img :src="image.src" class="carousel-image" />
              </div>
            </q-carousel-slide>
          </q-carousel>
        </div>

        <div class="card-wrapper">
          <div class="card-aspect-ratio">
            <q-card flat bordered class="my-card">
              <q-card-section>
                <div class="text-h6">NA Store</div>
                <div class="text-subtitle2">by Nur Azima</div>
              </q-card-section>

              <q-tabs v-model="tab" class="text-teal">
                <q-tab label="Info" name="one" />
                <q-tab label="Terbaru" name="two" />
              </q-tabs>

              <q-separator />

              <q-tab-panels v-model="tab" animated>
                <q-tab-panel name="one">
                  <div class="info-content">{{ tentangKami }}</div>
                </q-tab-panel>

                <q-tab-panel name="two">
                  <ul>
                    <li v-for="item in terbaru" :key="item.name">
                      <div class="product-name">{{ item.name }}</div>
                      <div class="product-price">{{ item.price }}</div>
                    </li>
                  </ul>
                </q-tab-panel>
              </q-tab-panels>
            </q-card>
          </div>
        </div>
      </div>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-purple-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <div class="foot">&copy; Nur Azima 2024</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const slide = ref("style");
    const tab = ref("one");

    const images = [
      {
        name: "image1",
        src: "https://akcdn.detik.net.id/visual/2018/12/13/f48708c8-35e1-4d40-9124-22b21e5d6f00_169.jpeg?w=750",
      },
      {
        name: "image2",
        src: "https://shopee.co.id/inspirasi-shopee/wp-content/uploads/2020/07/ezgif.com-gif-maker-2021-08-10T081932.319.webp",
      },
      {
        name: "image3",
        src: "https://aseranishi.com/wp-content/uploads/2023/11/rekomendasi-jenis-alat-elektronik-rumah-tangga.jpg",
      },
      {
        name: "image4",
        src: "https://www.blibli.com/friends-backend/wp-content/uploads/2023/03/B300340-Cover-Peralatan-Rumah-Tangga-untuk-Persiapan-Lebaran.jpg",
      },
    ];

    const tentangKami = `NA Store adalah toko yang menjual berbagai macam produk berkualitas. 
    Berdiri sejak tahun 2020, kami telah melayani ribuan pelanggan dengan produk-produk unggulan 
    dan layanan terbaik. Kami berkomitmen untuk memberikan pengalaman berbelanja yang nyaman dan 
    menyenangkan bagi seluruh pelanggan kami. Produk yang kami tawarkan meliputi berbagai macam 
    kategori, mulai dari elektronik, peralatan rumah tangga, hingga produk fashion dan kecantikan. 
    Kami juga menyediakan layanan purna jual yang handal untuk memastikan kepuasan pelanggan kami 
    selalu terjaga. NA Store berlokasi di pusat kota, menjadikan kami mudah diakses oleh pelanggan. 
    Kami selalu berusaha untuk terus berinovasi dan mengikuti perkembangan tren untuk menghadirkan 
    produk-produk terbaru yang sesuai dengan kebutuhan dan keinginan pelanggan. Terima kasih telah 
    mempercayakan NA Store sebagai pilihan belanja Anda. Kami berharap dapat terus melayani Anda 
    dengan lebih baik di masa yang akan datang.`;

    const terbaru = [
      {
        name: "Blender Multifungsi",
        price: "Rp 500.000",
      },
      {
        name: "Setrika Listrik",
        price: "Rp 300.000",
      },
      {
        name: "Vacuum Cleaner Portable",
        price: "Rp 700.000",
      },
      {
        name: "Kipas Angin Meja",
        price: "Rp 200.000",
      },
      {
        name: "Mesin Cuci Mini",
        price: "Rp 1.200.000",
      },
    ];

    const kontak =
      "Hubungi kami di email@example.com atau telepon di (123) 456-7890.";

    return {
      slide,
      tab,
      images,
      tentangKami,
      terbaru,
      kontak,
    };
  },
};
</script>

<style>
body {
  background-image: url("https://e0.pxfuel.com/wallpapers/602/768/desktop-wallpaper-purple-and-pink.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.bg-pink-custom {
  background-color: #ff69b4;
}

.foot {
  text-align: center;
}

.content-wrapper {
  display: flex;
  justify-content: space-between;
}

.carousel-wrapper {
  flex: 2;
  margin-right: 1rem;
}

.card-wrapper {
  transform: translateY(-8%);
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card-aspect-ratio {
  position: relative;
  width: 100%;
  padding-top: 100%;
}

.my-card {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.carousel-slide {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.carousel-image-wrapper {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.carousel-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.info-content {
  white-space: pre-line;
}

.product-name {
  font-weight: bold;
}

.product-price {
  color: #888;
}
</style>
