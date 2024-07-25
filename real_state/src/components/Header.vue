<template>
  <div>
    <div id="app">
      <header>
        <div class="container">
          <div class="logo">
            <h1 style="color: #ffbc00">{{ projectName }}</h1>
          </div>
          <nav>
            <ul>
              <li><a href="#overview">Overview</a></li>
              <li><a href="#location">Location</a></li>
              <li><a href="#photos">Photos</a></li>
              <li><a href="#layouts">Layouts</a></li>
              <li><a href="#amenities">Amenities</a></li>
              <li><a href="#payment">Payment Plans</a></li>
              <li><a href="#loanOffers">Bank Loan Offers</a></li>
            </ul>
          </nav>
          <div class="menu-toggle" @click="toggleMenu">
            <span></span>
            <span></span>
            <span></span>
          </div>
        </div>
      </header>
      <div style=" border-top: 6px solid #ffbc00">
        <img
          src="https://images.pexels.com/photos/106399/pexels-photo-106399.jpeg?cs=srgb&dl=pexels-binyaminmellish-106399.jpg&fm=jpg"
          alt=""
          width="100%"
          height="100%"
          style="object-fit: cover"
        />
      </div>
      <div class="overview_container">
        <section id="overview">
          <h2>Project Building Overview</h2>
          <div>
            <p>{{ projectOverview1 }}</p>
            <p>{{ projectOverview2 }}</p>
          </div>
          <div class="keyFeatures">Key Features</div>
          <ul class="keyType">
            <li>Type: {{ projectType }}</li>
            <li>Total Units: {{ totalUnits }}</li>
            <li>Area: {{ area }}</li>
            <li>Completion Date: {{ completionDate }}</li>
            <li>Developer: {{ developer }}</li>
          </ul>
        </section>
      </div>
      <div class="location_container">
        <section id="location" class="location-section">
      <div class="container">
        <div class="overview-column">
          <h2 class="location-heading">Location Overview</h2>
          <p class="location-description">{{ locationOverview }}</p>
        </div>
        <div class="map-column">
          <div class="map-container">
            <GoogleMap />
          </div>
        </div>
      </div>
    </section>
      </div>
      <div class="sampleFlat_container">
        <section id="photos">
          <h2>Sample Flat Photos</h2>
          <div class="gallery">
            <div v-for="photo in photos" :key="photo.id" style="height: 500px">
              <img
                :src="photo.url"
                :alt="photo.description"
                style="width: 100%; height: 100%; object-fit: cover"
              />
              <div class="imageDescription">
                <div class="photoDes">
                  {{ photo.description }}
                </div>
              </div>
            </div>
          </div>
        </section>
      </div>
      <section id="layouts">
        <h2>Building Floor Layouts</h2>
        <div class="layouts">
          <div v-for="layout in layouts" :key="layout.id" class="layout-card">
            <div class="card-header">
              <h3>{{ layout.title }}</h3>
            </div>
            <div class="card-body">
              <div class="image-container">
                <img
                  :src="layout.url"
                  :alt="layout.title"
                  class="layout-image"
                />
              </div>
              <p class="description">{{ layout.description }}</p>
            </div>
            <div class="card-footer">
              <button @click="viewDetails(layout.id)">View Details</button>
            </div>
          </div>
        </div>
        <!-- Display details of the selected layout -->
        <div v-if="selectedLayout" class="layout-details">
          <h3>{{ selectedLayout.title }}</h3>
          <img
            :src="selectedLayout.url"
            :alt="selectedLayout.title"
            class="layout-image"
          />
          <p class="description">{{ selectedLayout.description }}</p>
          <button @click="selectedLayout = null">Close</button>
        </div>
      </section>
      <div class="sampleFlat_container">
        <section id="amenities">
          <h2>Amenities Details</h2>
          <div class="amenities-container">
            <div
              v-for="(amenity, index) in amenities"
              :key="index"
              class="amenity-item"
            >
              <img
                :src="amenityImages[index]"
                :alt="amenity"
                class="amenity-image"
              />
              <div class="amenity-text">{{ amenity }}</div>
            </div>
          </div>
        </section>
      </div>
      <section id="payment">
        <h2 style="color: #020829">Payment Plan Details</h2>
        <div class="payment-plan-container">
          <div
            v-for="plan in paymentPlans"
            :key="plan.id"
            class="payment-plan-card"
          >
            <div class="icon-container">
              <i class="fas fa-credit-card"></i>
            </div>
            <div class="plan-details">
              <h3>{{ plan.title }}</h3>
              <div class="planDetails">{{ plan.details }}</div>
            </div>
          </div>
        </div>
      </section>
      <section id="loanOffers">
        <h2>Bank Loan Offers</h2>
        <div class="loan-offers-container">
          <div v-for="loan in loanOffers" :key="loan.id" class="loan-offer-card">
            <div class="loan-icon">
              <i class="fas fa-university"></i>
            </div>
            <div class="loan-details">
              <h3>{{ loan.bankName }}</h3>
              <p class="loan-description">{{ loan.details }}</p>
              <a :href="loan.moreInfoLink" class="more-info-link">More Info</a>
            </div>
          </div>
        </div>
      </section>

    </div>
  </div>
</template>
<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/swiper-bundle.css";
import GoogleMap from "./GoogleMap.vue";
import cardsCarousel from "./cardsCarousel.vue";
import "@fortawesome/fontawesome-free/css/all.min.css";

export default {
  components: { GoogleMap, cardsCarousel, Swiper, SwiperSlide },
  data() {
    return {
      selectedLayout: null,

      projectName: "Galaxy",
      projectOverview2:
        "      Boasting an impressive array of residential units, Galaxy Building provides a diverse selection of floor plans tailored to meet various lifestyle needs. Each apartment is thoughtfully designed to maximize space and natural light, featuring floor-to-ceiling windows that offer breathtaking panoramic views of the city skyline. The interiors are adorned with premium finishes, including state-of-the-art appliances, high-quality flooring, and elegant fixtures, ensuring a sophisticated and comfortable living environment.",
      projectOverview1:
        "Galaxy Building represents a pinnacle of modern urban design, meticulously crafted to offer an unparalleled living experience. Situated in the heart of a bustling metropolis, this iconic structure stands as a testament to innovative architecture and luxury. The building's sleek, contemporary facade is complemented by a blend of high-end materials, creating a striking visual appeal that seamlessly integrates with the cityscape.",
      projectType: "Residential",
      totalUnits: 120,
      area: "1500 sq ft",
      completionDate: "December 2023",
      developer: "Dream Developers",
      locationOverview:
        "The Galaxy project is strategically situated in one of the most sought-after neighborhoods of the city, ensuring that residents have access to a plethora of conveniences and amenities. Nestled in a prime location, Galaxy offers an unparalleled blend of urban vibrancy and serene living.",
      photos: [
        {
          id: 1,
          url: "https://images.pexels.com/photos/1571458/pexels-photo-1571458.jpeg?cs=srgb&dl=pexels-fotoaibe-1571458.jpg&fm=jpg",
          description: "Living Room",
        },

        {
          id: 2,
          url: "https://media.istockphoto.com/id/1222623844/photo/master-bedroom-in-new-luxury-home-with-chandelier-and-large-bank-of-windows-with-view-of-trees.jpg?s=612x612&w=0&k=20&c=BuIObAMmOM6AZ2d2L9bCYh9tfxCCsdzeqWo6tizso9I=",
          description: "Bedroom",
        },
        {
          id: 3,
          url: "https://www.regalokitchens.com/images/design/kitchen/parallel-white-modular-kitchen-design.jpg",
          description: "Kitchen",
        },

        {
          id: 4,
          url: "https://st.hzcdn.com/simgs/pictures/balconies/chenault-michael-lee-architects-img~f991a99e0bd75d8b_14-8239-1-8410c32.jpg",
          description: "Balcony",
        },
        {
          id: 5,
          url: "https://st.hzcdn.com/simgs/pictures/landscapes/idyllic-modern-david-thorne-landscape-architect-img~1a51861a0c5e2432_14-9463-1-ad779bb.jpg",
          description: "Garden",
        },
        {
          id: 6,
          url: "https://www.regalokitchens.com/images/design/kitchen/parallel-white-modular-kitchen-design.jpg",
          description: "Kitchen",
        },
      ],
      layouts: [
        {
          id: 1,
          title: "Ground Floor",
          url: "https://i.pinimg.com/736x/09/79/fc/0979fccb743c995f4bfea3d54f14be97.jpg",
        },
        {
          id: 2,
          title: "First Floor",
          url: "https://png.pngtree.com/background/20231030/original/pngtree-clear-3d-interior-design-of-ground-floor-apartment-in-plan-view-picture-image_5785276.jpg",
        },
        {
          id: 3,
          title: "Second Floor",
          url: "https://png.pngtree.com/background/20231030/original/pngtree-d-interior-design-of-ground-floor-apartment-from-a-top-view-picture-image_5784954.jpg",
        },
      ],
      amenities: [
        "Swimming Pool",
        "Gymnasium",
        "Children's Play Area",
        "Jogging Track",
        "Clubhouse",
        "24/7 Security",
      ],
      amenityImages: [
        "https://t3.ftcdn.net/jpg/02/80/11/26/360_F_280112608_32mLVErazmuz6OLyrz2dK4MgBULBUCSO.jpg", // Replace with actual URLs
        "https://media.istockphoto.com/id/1183038884/photo/view-of-a-row-of-treadmills-in-a-gym-with-people.jpg?s=612x612&w=0&k=20&c=VnTSyKHKl-YFOmpFqW_hNyIlis0sFksfcR9Ei3-r29s=",
        "https://www.wodehousegymkhana.com/wp-content/uploads/whg-play-area-1-1600.jpg",
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTRW8Hq8W4kFuFs8YDu29zlnOKP9xHEmLQphw&s",
        "https://www.nyrentownsell.com/blog/wp-content/uploads/2022/06/Clubhouse.jpg",
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSpCK20x-BFKTsvbBXkdo2pCr-TXUo9U_uBhg&s",
      ],
      paymentPlans: [
        {
          id: 1,
          title: "Plan A",
          details: "10% down payment, 90% on possession",
        },
        {
          id: 2,
          title: "Plan B",
          details:
            "20% down payment, 40% during construction, 40% on possession",
        },
        {
          id: 3,
          title: "Plan C",
          details: "Customizable payment plans available upon request",
        },
      ],
      loanOffers: [
      {
        id: 1,
        bankName: "Bank A",
        details: "Interest Rate: 7.5%, Loan Amount: Up to $500,000",
        moreInfoLink: "https://example.com/bank-a-details",
      },
      {
        id: 2,
        bankName: "Bank B",
        details: "Interest Rate: 6.8%, Loan Amount: Up to $750,000",
        moreInfoLink: "https://example.com/bank-b-details",
      },
      {
        id: 3,
        bankName: "Bank C",
        details: "Interest Rate: 8.0%, Loan Amount: Up to $300,000",
        moreInfoLink: "https://example.com/bank-c-details",
      },
    ],
    };
  },
  methods: {
    toggleMenu() {
      const nav = document.querySelector("header nav ul");
      nav.classList.toggle("active");
    },
    viewDetails(layout) {
      this.selectedLayout = layout;
    },
    closeDetails() {
      this.selectedLayout = null;
    },
  },
};
</script>
<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>
<style scoped>

header {
  background-color: #020829;
  color: white;
  padding: 1em 0;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

header .logo h1 {
  margin: 0;
}

header nav ul {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
}

header nav ul li {
  margin: 0 1em;
}
header nav ul li a {
  color: white;
  text-decoration: none;
  font-size: 1.2rem;
  font-weight: 600;
  padding: 0.5em 0;
  position: relative;
  transition: color 0.3s ease;
}
header nav ul li a:hover {
  color: #ffbc00;
}

header nav ul li a::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: 0;
  width: 0;
  height: 2px;
  background-color: #ffbc00;
  transition: width 0.3s ease;
}

header nav ul li a:hover::after {
  width: 100%;
}

header .menu-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
}

header .menu-toggle span {
  background: white;
  height: 2px;
  margin: 3px 0;
  width: 25px;
}

section {
  padding: 2em 1rem;
  border-bottom: 1px solid #ccc;
}
.overview_container,
.sampleFlat_container {
  background-color: #020829;
  color: white;
  border-top: 10px solid #ffbc00;
}
/* .location_container {
  background-color: #ffbc00;
  color: white;
  border-top: 10px solid #fff;
} */
h2 {
  color: #ffbc00;
  font-size: 2rem;
  font-weight: 700;
  text-align: center;
}
p {
  font-size: 1.1rem;
  font-weight: 500;
  line-height: 1.5rem;
  padding: 0rem 4rem;
}
.keyFeatures {
  color: #ffbc00;
  font-size: 1.5rem;
  font-weight: 700;
  padding: 0rem 4rem;
}
.keyType {
  padding: 0rem 5rem;
}
li {
  font-size: 1.3rem;
  line-height: 2rem;
  font-weight: 600;
  color: #fff;
}
.imageDescription {
  background-color: #ffeb3b33;
  text-align: center;
  position: relative;
  top: -110px;

  display: flex;
  justify-content: center;
}
.photoDes {
  color: black;
  font-size: 1.5rem;
  font-weight: 700;
}
.gallery,
.layouts {
  display: flex;
  flex-wrap: wrap;
}

.gallery div,
.layouts div {
  flex: 1 1 calc(33.333% - 1em);
  margin: 0.5em;
}

.gallery img,
.layouts img {
  max-width: 100%;
  height: auto;
}

@media (max-width: 768px) {
  header nav ul {
    display: none;
    flex-direction: column;
    width: 100%;
  }
  header .container {
    flex-direction: row;

}


  header nav ul.active {
    display: flex;
  }

  header .menu-toggle {
    display: flex;
  }

  .gallery div,
  .layouts div {
    flex: 1 1 calc(50% - 1em);
  }
}

@media (max-width: 480px) {
  .gallery div,
  .layouts div {
    flex: 1 1 100%;
  }
}
</style>
<style scoped>
.location-section {
  /* background-color: #ffbc00; */

  padding: 2em 1rem;
  color: #020829;
  border-top: 10px solid #ffbc00;
}

.container {
  display: flex;
  flex-wrap: wrap;
  gap: 2em;
}

.overview-column,
.map-column {
  flex: 1;
  min-width: 300px;
}

.location-heading {
  font-size: 2.5rem;
  font-weight: 700;
  color: #020829;
  margin-bottom: 1em;
}

.location-description {
  font-size: 1.1rem;
  font-weight: 500;
  line-height: 1.5;
}

.map-container {
  width: 100%;
  height: 400px; 
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
    /* align-items: center; */
  }

  .map-container {
    height: 300px;
  }
}
</style>
<style>
.layout-card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  width: 300px;
  margin: 1em;
  text-align: center;
  transition: transform 0.3s ease;
}

.layout-card:hover {
  transform: scale(1.05);
}

.card-header {
  background-color: #020829;
  color: white;
  padding: 1em;
}

.card-body {
  padding: 1em;
}

.image-container {
  height: 200px;
  overflow: hidden;
  position: relative;
}

.layout-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  position: absolute;
  top: 0;
  left: 0;
}

.description {
  font-size: 1rem;
  color: #333;
  margin: 1em 0;
}

.card-footer {
  padding: 1em;
  background-color: #f1f1f1;
}

.card-footer button {
  background-color: #ffbc00;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 0.5em 1em;
  cursor: pointer;
  font-size: 1rem;
}

.card-footer button:hover {
  background-color: #e0a700;
}
</style>
<style>
.amenities-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1em;
}

.amenity-item {
  display: flex;
  align-items: center;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 1em;
  width: 200px;
  text-align: center;
}

.amenity-image {
  width: 50px;
  height: 50px;
  object-fit: cover;
  margin-right: 1em;
}

.amenity-text {
  font-size: 1rem;
  color: #333;
  font-weight: 600;
}
</style>
<style scoped>
section#payment {
  padding: 2em 1rem;
  border-bottom: 5px solid #ffff;
  background-color: #ffbc00;
}

.payment-plan-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1em;
}

.payment-plan-card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 1em;
  width: 300px;
  text-align: center;
  transition: transform 0.3s ease;
  display: flex;
  align-items: center;
  gap: 1em;
}

.payment-plan-card:hover {
  transform: scale(1.05);
}

.icon-container {
  font-size: 2rem;
  color: #ffbc00;
  margin: 1em 0.2em;
}

.plan-details {
  flex: 1;
}

.plan-details h3 {
  margin: 0;
  font-size: 1.5rem;
  color: #020829;
}

.plan-details .planDetails {
  font-size: 1rem;
  color: #333;
}
</style>
<style scoped>
section#loanOffers {
  padding: 2em 1rem;
  background-color: #f4f4f4;
  border-bottom: 5px solid #020829;
}

.loan-offers-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5em;
}

.loan-offer-card {
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  padding: 1.5em;
  width: 320px;
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.loan-offer-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.loan-icon {
  font-size: 3rem;
  color: #ffbc00;
  margin-bottom: 1em;
}

.loan-details {
  flex: 1;
}

.loan-details h3 {
  margin: 0;
  font-size: 1.75rem;
  color: #020829;
  margin-bottom: 0.5em;
}

.loan-description {
  font-size: 1rem;
  color: #333;
  margin-bottom: 1em;
}

.more-info-link {
  color: #ffbc00;
  text-decoration: none;
  font-weight: 600;
}

.more-info-link:hover {
  text-decoration: underline;
}

</style>