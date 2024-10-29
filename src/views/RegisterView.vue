<template>
  <section class="section">
    <div class="login-description">
      <img
        class="img"
        src="../assets/left-login-image.jpeg"
        alt="Japan image"
      />
      <p>Academia de idioma japonesa Rami School</p>
    </div>

    <div class="login-container">
      <h3 class="h3 text-center">Language Site</h3>
      <p class="text-center">Welcom to Rami School!</p>

      <FloatLabelInput label="Full Name" />
      <FloatLabelInput label="Password" type="password" />

      <div class="actions">
        <div class="links">
          <a href="#">Create account</a>
          <a href="#">Forgot password?</a>
        </div>
        <button class="login-button">Login</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import FloatLabelInput from "@/components/FloatLabelInput.vue";
</script>

<style scoped>
section {
  padding-block-start: 130px;
  width: 100%;
  height: 100%;
  z-index: 4;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  /* gap: 5rem; */
}

/* Estilos del contenedor principal */
.login-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--bg-dark-sakura);
  color: var(--text-white);
  border-radius: var(--radius-24);
  box-shadow: var(--shadow-2);
  padding: 40px;
  width: 400px;
  /* margin: 100px auto; */
  font-family: var(--fontFamily-open-sans);
}

/* Botón de login */
.login-button {
  background-color: var(--bg-vivid-kurenai);
  color: var(--text-white);
  border: none;
  padding: 10px 64px;
  border-radius: var(--radius-24);
  font-size: var(--fontSize-5);
  cursor: pointer;
  transition: background-color var(--transition-1);
  margin-top: 16px;
}

.login-button:hover {
  background-color: var(--bg-nishikigi);
}

/* Enlaces de acciones */
.actions {
  /* margin-top: 24px; */
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.links {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.links a {
  color: var(--text-white-alpha-60);
  text-decoration: none;
  font-size: var(--fontSize-7);
  transition: color var(--transition-1);
}

.links a:hover {
  color: var(--text-white);
}

.login-description {
  display: none;
}

@media (min-width: 768px) {
  .login-description {
    padding-inline: 30px;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    align-items: center;
  }

  .img {
    width: 340px;
    border-radius: var(--radius-24);
  }
}
</style>
