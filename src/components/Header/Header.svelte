<script>
  import DarkLogo from "../../assets/S_Logo_Dark.png";
  import LightLogo from "../../assets/S_Logo_Light.png";
  import NightIcon from "../../assets/moon-svgrepo-com.svg";
  import SunIcon from "../../assets/sun-svgrepo-com.svg";
  export let dark = true;
  import { Router, Link, Route, navigate } from "svelte-routing";
  $: theme = dark ? "dark" : "light";

  function changeTheme() {
    dark = !dark;
  }

  function redir(){
    navigate('/', {replace: true})
  }
</script>

<div class={"Header " + theme}>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="logo" on:click={redir}>
      <img src={dark ? DarkLogo : LightLogo} alt="Imagen" />
      <span>ilva</span>
  </div>
  <div class="toggler">
    <span>{dark? 'Oscuro': 'Claro'}</span>
    <label class="switchTheme">
      <input type="checkbox" on:click={changeTheme}/>
      <span class="slider" />
    </label>
  </div>
</div>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;

  .toggler{
    display: flex;
    flex-direction: row;
    align-items: center;
    span{
        padding-right: 10px;
    }
  }

  .logo {
    padding: 10px;
    cursor: pointer;
    img {
      width: 7vh;
    }
    span {
        margin-left: calc(-0.5vh);
        font-weight: 700;
        font-size: calc(5vh);
      }
  }

  .Header {
    background-color: $light-color;
    transition: 0.4s ease;
    color: $dark-color;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid $dark-color;
  }

  .Header.dark {
    background-color: $dark-color;
    color: $light-color;
    border-bottom: 1px solid $light-color;
  }

  .switchTheme {
    position: relative;
    display: inline-block;
    width: 70px;
    height: 40px;
    margin: 10px 10px;

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: $light-color;
      transition: 0.4s;
      border-radius: 34px;

      &::before {
        position: absolute;
        content: "";
        width: 30px;
        height: 30px;
        left: 5px;
        bottom: 5px;
        background-color: $dark-color;
        transition: 0.4s;
        border-radius: 50px;
      }
    }
    input {
      display: none;

      &:checked + .slider {
        background-color: $dark-color;
      }

      &:checked + .slider::before {
        transform: translate(30px);
        background-color: $light-color;
      }
    }
  }
</style>
