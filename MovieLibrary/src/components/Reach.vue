<template>
  <section class="reach-section" aria-labelledby="reach-heading">
    <div class="reach-container">
      <div class="reach-form-area">
        <h2 id="reach-heading">How to reach us</h2>
        <p class="reach-desc">Lorem ipsum dolor sit amet, consetetur.</p>
        <form class="reach-form" @submit.prevent>
          <div class="form-row">
            <div class="form-group">
              <label for="firstName">First Name *</label>
              <input id="firstName" name="firstName" type="text" required autocomplete="given-name" />
            </div>
            <div class="form-group">
              <label for="lastName">Last Name *</label>
              <input id="lastName" name="lastName" type="text" required autocomplete="family-name" />
            </div>
          </div>
          <div class="form-group">
            <label for="email">Email *</label>
            <input id="email" name="email" type="email" required autocomplete="email" />
          </div>
          <div class="form-group">
            <label for="telephone">Telephone</label>
            <input id="telephone" name="telephone" type="tel" autocomplete="tel" />
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" name="message" rows="3"></textarea>
          </div>
          <div class="form-note">* required fields</div>
          <div class="form-group checkbox-group">
            <input id="terms" name="terms" type="checkbox" required />
            <label for="terms">
              I agree to the <a href="#" tabindex="0">Terms &amp; Conditions</a>
            </label>
          </div>
          <button type="submit" class="submit-btn">SUBMIT</button>
        </form>
      </div>
      <div class="reach-map-area align-to-inputs">
        <a
          href="https://goo.gl/maps/5sW9xsCNvByPnxXE9"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="Open location in Google Maps"
          style="width:100%;display:block;"
        >
          <iframe
            class="map-img"
            src="https://www.google.com/maps?q=40.3387,-3.7533&z=15&output=embed"
            title="Map location"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Reach'
}
</script>

<style scoped>
.reach-section {
  background: #000;
  color: #fff;
  padding: 3rem 0 0 0;
  font-family: 'Poppins', sans-serif;
}
.reach-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2.5vw 3rem 2.5vw;
  gap: 2.5rem;
  /* Remove align-items: flex-start for custom alignment */
}
.reach-form-area {
  flex: 1 1 420px;
  max-width: 540px;
  /* No margin-bottom so map aligns with inputs */
  display: flex;
  flex-direction: column;
}
.reach-form-area h2,
.reach-desc {
  /* Keep heading and desc above form */
}
.reach-form {
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
}
.form-row {
  display: flex;
  gap: 1.2rem;
}
.form-group {
  display: flex;
  flex-direction: column;
  flex: 1;
}
.form-group label {
  font-size: 1.1rem;
  margin-bottom: 0.3rem;
  font-weight: 500;
  letter-spacing: 1px;
}
.form-group input,
.form-group textarea {
  background: #333;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 0.7rem 1rem;
  font-size: 1.1rem;
  margin-bottom: 0.1rem;
  outline: none;
  transition: border 0.2s;
}
.form-group input:focus,
.form-group textarea:focus {
  border: 2px solid #ffc107;
}
.form-group textarea {
  resize: vertical;
  min-height: 70px;
  max-height: 200px;
}
.form-note {
  font-size: 1rem;
  color: #b2c2c2;
  margin-bottom: 0.5rem;
}
.checkbox-group {
  flex-direction: row;
  align-items: center;
  gap: 0.7rem;
  margin-bottom: 0.5rem;
}
.checkbox-group input[type="checkbox"] {
  width: 22px;
  height: 22px;
  accent-color: #ffc107;
  margin: 0;
}
.checkbox-group label {
  font-size: 1.1rem;
  color: #fff;
  margin: 0;
}
.checkbox-group a {
  color: #ffc107;
  text-decoration: underline;
}
.submit-btn {
  margin: 1.5rem auto 0 auto;
  display: block;
  background: #ffc107;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 1.2rem;
  font-weight: 600;
  padding: 0.8rem 0;
  width: 240px;
  cursor: pointer;
  transition: background 0.2s;
}
.submit-btn:hover,
.submit-btn:focus {
  background: #e0a800;
}
.reach-map-area {
  flex: 1 1 520px;
  max-width: 700px;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  min-width: 320px;
  /* Remove margin-top/margin-bottom for alignment */
}
.align-to-inputs {
  margin-top: 3.7rem; /* Adjust this value to align the map with the top of the input row */
}
.map-img {
  width: 100%;
  max-width: 600px;
  min-width: 320px;
  height: 450px;
  object-fit: cover;
  border-radius: 8px;
  border: none;
  box-shadow: 0 2px 16px 0 rgba(0,0,0,0.25);
  background: #222;
  display: block;
}
@media (max-width: 1100px) {
  .reach-container {
    flex-direction: column;
    align-items: stretch;
    gap: 2.5rem;
  }
  .reach-map-area, .reach-form-area {
    max-width: 100%;
  }
  .map-img {
    width: 100%;
    min-width: 0;
    max-width: 100%;
    height: 320px;
  }
  .align-to-inputs {
    margin-top: 8rem;
  }
}
@media (max-width: 900px) {
  .reach-container {
    flex-direction: column;
    align-items: stretch;
    gap: 2.5rem;
    padding-left: 1rem;
    padding-right: 1rem;
  }
  .reach-form-area {
    max-width: 100%;
    padding: 0;
  }
  .reach-form {
    gap: 1rem;
  }
  .form-row {
    flex-direction: column;
    gap: 0.5rem;
  }
  .form-group input,
  .form-group textarea {
    width: 90%;
    font-size: 1.1rem;
    padding: 0.7rem 1rem;
    margin-bottom: 0.2rem;
  }
  .submit-btn {
    width: 100%;
    font-size: 1.1rem;
    margin: 1.2rem 0 0 0;
  }
  .checkbox-group {
    margin-bottom: 1.2rem;
  }
}
</style>