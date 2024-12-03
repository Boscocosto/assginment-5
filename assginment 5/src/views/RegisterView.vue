<script setup></script>

<template>
  <div class="header">
    <div class="logo">
      <img src="/movie.png" class="logo" />
      <h1>Pop Movies</h1>
    </div>
    <div class="buttons">
      <RouterLink to="/login" class="button register">Log in</RouterLink>
    </div>
  </div>
  <div class="login">
    <h2>Create an Account</h2>
    <form>
      <input type="text" placeholder="Name" class="input-field" required>
      <input type="email" placeholder="Email" class="input-field" required>
      <input type="password" placeholder="Password" class="input-field" required>
      <button type="submit" class="button register">Register</button>
    </form>
  </div>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1%;
  background-color: white;
  border: 2px solid rgba(0, 0, 0, 0.8);
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  margin: 20px;
}

.logo {
  display: flex;
  align-items: center;
}

.logo img {
  height: 50px;
  margin-right: 10px;
}

.buttons {
  display: flex;
  gap: 10px;
}

.button {
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  background-color: #000000;
  color: white;
  transition: background-color 0.3s;
}

.button:hover {
  background-color: #0000008d;
}

/* Login Section Styles */
.login {
  margin: 0 auto;
  padding: 20px;
  max-width: 900px;
  /* Increase the width to allow space for the row */
  margin-top: 10%;
  /* Adjust the margin-top to move the form down */
  text-align: center;
}

.login h2 {
  font-size: 24px;
  margin-bottom: 20px;
}

/* Form Styles to fit inputs and button in one line */
.login-form {
  display: flex;
  /* Align all child elements in a row */
  justify-content: space-between;
  /* Distribute space between items */
  gap: 10px;
  /* Space between the form elements */
  flex-wrap: nowrap;
  /* Prevent wrapping, all elements stay in a row */
}

.input-field {
  flex: 1 1 22%;
  /* Make each input take up 22% of the width to fit 4 items */
  padding: 12px;
  margin: 10px 0;
  border-radius: 5px;
  border: 1px solid #ccc;
  box-sizing: border-box;
  font-size: 16px;
}

.input-field:focus {
  border-color: #000;
  outline: none;
}

.button.register {
  flex: 1 1 22%;
  /* Make the button take up 22% of the width, same as inputs */
  padding: 12px;
  background-color: #333;
  color: white;
  border-radius: 5px;
  border: none;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.button.register:hover {
  background-color: #000;
}
</style>