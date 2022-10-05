
    <script>
  import api from "../api/index";
  import { user } from "../store/index";
  import { navigate } from "svelte-routing";
  let errors = {
    email: "",
    password: "",
    common: "",
  };
  const signupData = {
    name:"",
    email: "",
    password: "",
  };

  async function handleSubmit() {
    try {
      const account = await api.createAccount(signupData.email, signupData.password, signupData.name);
      await api.createEmailSession(signupData.email, signupData.password);
      user.update(() => account);
    } catch (error) {

    }
  }

  </script>
  

  <div class="circle" />
  <form class="form" on:submit|preventDefault={handleSubmit}>
    <h2 class="form__title">SignUp</h2>
    <div class="form__container">
      <div class="form__group">
        <input
          type="text"
          id="name"
          bind:value={signupData.name}
          class="form__input"
          placeholder=" "
        />
        <label for="name" class="form__label">Name:</label>
        <span class="form__line" />
      </div>
      <div class="form__group">
        <input
          type="text"
          id="email"
          bind:value={signupData.email}
          class="form__input"
          placeholder=" "
        />
        <label for="email" class="form__label">Email:</label>
        <span class="form__line" />
      </div>
      <div class="form__group">
        <input
          type="password"
          id="password"
          class="form__input"
          placeholder=" "
          bind:value={signupData.password}
        />
        <label for="password" class="form__label">Password:</label>
        <span class="form__line" />
      </div>
      {#if errors.common}
        <div class="text-danger">{errors.common}</div>
      {/if}
      <input type="submit" class="form__submit" value="LOG IN" />
    </div>
  </form>
  
  <style>
    .circle {
      width: 50%;
      height: 70%;
      position: absolute;
      background: #3866f2;
      border-radius: 0 0 100% 0;
    }
  
    .form {
      background-color: #fff;
      margin: auto;
      width: 90%;
      max-width: 400px;
      padding: 4.5em 3em;
      border-radius: 10px;
      box-shadow: 0 5px 10px -5px rgb(0 0 0 / 30%);
      text-align: center;
      /* From https://css.glass */
      background: rgba(255, 255, 255, 0.877);
      border-radius: 16px;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(12.2px);
      -webkit-backdrop-filter: blur(12.2px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      transition: 1s;
    }
    .form:hover {
      transform: scale(1.02);
      transition: 1s;
    }
  
    .form__title {
      font-size: 2rem;
      margin-bottom: 0.5em;
    }
    .form__container {
      margin-top: 3em;
      display: grid;
      gap: 2.5em;
    }
    .form__group {
      position: relative;
      color: #5757577e;
    }
    .form__input {
      width: 100%;
      background: none;
      --color: #706c6c;
      font-size: 1rem;
      padding: 0.6em 0.3em;
      border: none;
      outline: none;
      border-bottom: 1px solid var(--color);
      font-family: "Roboto", sans-serif;
    }
    .form__input:not(:placeholder-shown) {
      color: #4d4646;
    }
  
    .form__input:focus + .form__label,
    .form__input:not(:placeholder-shown) + .form__label {
      transform: translateY(-12px) scale(0.7);
      transform-origin: left top;
      color: #3866f2;
    }
    .form__label {
      color: var(--color);
      cursor: pointer;
      position: absolute;
      top: 0;
      left: 5px;
      transform: translateY(10px);
      transition: transform 0.5s, color 0.3s;
    }
    .form__submit {
      background: #3866f2;
      color: #fff;
      font-family: "Roboto", sans-serif;
      font-weight: 300;
      font-size: 1rem;
      padding: 0.8em 0;
      border: none;
      border-radius: 0.5em;
    }
    .form__line {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 1px;
      background-color: #3866f2;
      transform: scale(0);
      transform: left bottom;
      transition: transform 0.4s;
    }
  
    .form__input:focus ~ .form__line,
    .form__input:not(:placeholder-shown) ~ .form__line {
      transform: scale(1);
    }
    @media (max-width: 425px) {
      .form__title {
        font-size: 1.8rem;
      }
    }
  </style>
  
  
  

  