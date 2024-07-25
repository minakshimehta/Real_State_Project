<template>
  <div class="footerMain">
    <footer>
      <div class="footer-container">
        <div class="footer-section">
          <h3>{{ footerTitle }}</h3>
          <p>{{ footerDescription }}</p>
        </div>
        <div class="footer-section">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#overview">Overview</a></li>
            <li><a href="#location">Location</a></li>
            <li><a href="#photos">Photos</a></li>
            <li><a href="#layouts">Layouts</a></li>
            <li><a href="#amenities">Amenities</a></li>
            <li><a href="#payment">Payment Plans</a></li>
            <li><a href="#loanOffers">Bank Loan Offers</a></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>Contact Us</h4>
          <p>123 Main Street, City, Country</p>
          <p>Email: info@example.com</p>
          <p>Phone: +123 456 7890</p>
        </div>
        <div class="footer-section">
          <h4>Follow Us</h4>
          <ul class="social-links">
            <li>
              <a href="#"><i class="fab fa-facebook-f"></i></a>
            </li>
            <li>
              <a href="#"><i class="fab fa-twitter"></i></a>
            </li>
            <li>
              <a href="#"><i class="fab fa-linkedin-in"></i></a>
            </li>
            <li>
              <a href="#"><i class="fab fa-instagram"></i></a>
            </li>
          </ul>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} {{ projectName }}. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script>
import "@fortawesome/fontawesome-free/css/all.min.css";

export default {
  data() {
    return {
      footerTitle: "Galaxy Residences",
      footerDescription:
        "Your dream home awaits. Discover luxury living with Galaxy Residences.",
      currentYear: new Date().getFullYear(),
      projectName: "Galaxy",
    };
  },
};
</script>

<style scoped>
.footerMain {
  background: url("data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBwgHBgkIBwgKCgkLDRYPDQwMDRsUFRAWIB0iIiAdHx8kKDQsJCYxJx8fLT0tMTU3Ojo6Iys/RD84QzQ5OjcBCgoKDQwNGg8PGjclHyU3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3N//AABEIAIEA5AMBIgACEQEDEQH/xAAaAAEAAwEBAQAAAAAAAAAAAAACAAEDBAUH/8QAKxAAAgIBBAAFAwQDAAAAAAAAAAECEQMSITFBIjJRYYEEcfETM5GxYqHR/8QAGQEAAwEBAQAAAAAAAAAAAAAAAAECAwUE/8QAHhEBAQEBAQEAAgMAAAAAAAAAAAERAjEhQWEDElH/2gAMAwEAAhEDEQA/APlzKZbKZ0a56t+jbHjb3Zkub9Dphk1quPYcK1HsqIiMMuBoKwsKe4r2AxYGNgYHBYWJhZNULCxMLEoGFiYWJQstIeiSWp8FMRqom/XyQgCOr6b6e0sk9l0jrftwcH02d43pfkfJ37NXHddM058Zd7v0WUy2UxpgMLEwsDgMLEwshUFkIyApsymWymOoUWm07XJRADojNTV8PtElwc9tbo2hNTV9jhXnFSKUtLLYGAjR7qwMpS0l8qwAsLEwsVOCwsTCxKB/6NsWJXqe3oisenV4vg3lyEgtU/EqfBzZIODro6HwBtcPsdhSubslWOeOSe3AoxS+5OL1UVSNcGWUPDLy9gYabdJW30Mrld6acbjuumUwYoPHHS3916DZbIGFiYWBwGFiYWQqCyEZAU2ZTLZTHUKIQgGhVtO0WyACU1JX2RsD2KTAYtkUtLKbCxHjXlWFhTE3sAFkSHGGp6iTelAN/ASi62Fhk2qfRUYOctvk20qC0oZW/gWCQ2CQCCmW2CRSmuGLVYVNulz0deHEsat+Z8+xxQyzhPVHo74T/UxprZPofPqO9RlUKimUzZvkLFILBcBhYmFkKgshGQFNmUy2Ux1CiELjHU6AIlZdUhcbBYDdGQGOQGJUVZLCyJiPCNMOOTSb8ocUdcktNna1UajsipEdXGOWShzt6IwjGWae3AcmrW9XJ1/Tzi8elbPteo/R5NXGChGl+QSNGZyGmUGCQ2CRK4zkZs0kZS9yVxp9MozzKMr34PSfPX/Dh+hyQjNwlHxviR3Pll8+Mv5PVMzkx5FJx8HPuYa04+jWzT5Q7SkWwFOW5Lsla3wBkZUnsIRTIBvcgKdLKLZcYa3RWIVGOp0apUqXA0tMaXAWOJ3QYGNgYqcGQGOQGSsGFqxMMgOFizfpzv8Ak7dUci1w39UebIWHM8U6/kJcF412ZIrIvf8Ao594y/yXB0Nxn44fIJpSV9j/AGib5WuLKsip7SXK9SSOVRala5R0RmpL37HovKmCQ2CQqcZyM9Lk6XPRo1Za8O6JVrpwYFiVveT5fobGWLLqWl+b+xylSNIxu2/SMpw1ISlZfICfHLLbYKOnJHUjmls6JrSXVtgbS3ZLpmGaVy9PYm1cn1Upyk7XBAEJ1pj0nwbYZRcaSp+nqYsr3XRrrzWOlhZUMmtU/MWxpBgY2BiqoMgMcgMlYMMhMMhKgMG/CGxxhXiFitLA5Y4/c2tNX2Y7dmmKLk/YcRf9Xp1Oh8KlwX1S4JRWI0ZcAZqw0AZ0QtouENToSqkIapL23NmJKo0uAspG6LFCdugsDDRjo5RlkjqRITvYfIejxyS2dGc46lR1ZIakc72dEWNOa5ns6IbMhOL12MplspmlYqujWMrRkS6HoxqwMtOymFKDIDHIDJVAYWrE1ZaVCVoxVCZbLhBzlS+QwamKOqVdVudFUqXHQowUI6V+SVRbO0aKYmUuQAhY2SMNToMAwhqdG6WmNLgSVRpcBY026LCxMLA4LCJhJqhYozvYLAw08dHKMskNSokJ3sPlAPHJJU6IdDRBH/Y2Uy2Ux1KiEIBo3Rd2UV2ARhYrCxHFUQsUIOcqj8gKqEHOVL5OqMFBaV+S4wUFpX5LouTGdqiK+i9+jHLlUFpXmC0p9XKcYvTIUlT24OGUrla39WbYs3Ut/RkyrvLVihkUXpYd69gSGXsdWzVoLMseVRehm29ew05gMLEwsDgsImEmqFgY2BiULHCd7AYWLTx02UYrLWxA0sdDKZCFVKiEIBoUQgjgshCAEOn6X9t/csg56nrxp2W+CELZgzizfuyLIT0vhmyFEIaV1x8kfsGRCF1nAfJ0w/bj9iEDkdIwssgygMJCE1QsDIQShYWQglKIQgB//9k=")
    no-repeat center center;
  background-size: cover;
}
footer {
  /* background-color: #020829; */
  color: black;
  padding: 2rem 1rem;
}

.footer-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  max-width: 1200px;
  margin: 0 auto;
}

.footer-section {
  flex: 1 1 200px;
  margin: 1rem;
}

.footer-section h3,
.footer-section h4 {
  color: #ffbc00;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  text-align: center;

}

.footer-section p {
  font-size: 1rem;
  line-height: 1.5;
}

.footer-section ul {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: center;

}

.footer-section ul li {
  margin-bottom: 0.5rem;
}

.footer-section ul li a {
  color: white;
  text-decoration: none;
  font-size: 1.2rem;
  font-weight: 600;
  padding: 0.5em 0;
  position: relative;
  transition: color 0.3s ease;
}

.footer-section ul li a:hover {
  color: #ffbc00;
}

.social-links {
  display: flex;
  gap: 1rem;
  align-items: center;
    justify-content: center;
}

.social-links li {
  display: inline;
}

.social-links a {
  color: white;
  font-size: 1.5rem;
  transition: color 0.3s;
}

.social-links a:hover {
  color: #ffbc00;
}

.footer-bottom {
  text-align: center;
  margin-top: 2rem;
  border-top: 1px solid #ccc;
  padding-top: 1rem;
}

.footer-bottom p {
  margin: 0;
}
p {
  font-size: 1rem;
  font-weight: 600;
  text-align: center;
  line-height: 1.4rem;
  color: #fff;
}
</style>
