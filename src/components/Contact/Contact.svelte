<script>
  import { Router, Link, Route, navigate } from "svelte-routing";
  import FaArrowLeft from "svelte-icons/fa/FaArrowLeft.svelte";
  import FaPhoneAlt from "svelte-icons/fa/FaPhoneAlt.svelte";
  import IoIosMail from 'svelte-icons/io/IoIosMail.svelte';
  import MdLocalPhone from 'svelte-icons/md/MdLocalPhone.svelte'
  import MdEmail from 'svelte-icons/md/MdEmail.svelte'
  import FaLinkedin from 'svelte-icons/fa/FaLinkedin.svelte'
  function goBack() {
    navigate("/", { replace: true });
  }

  export let theme;
</script>

<div class="Contact">
  <div class={"contactCard " + (theme ? "dark" : "light")}>
    <div class={"contactHeader " + (theme ? "dark" : "light")}>
      <button on:click={goBack} class={theme ? "dark" : "light"}>
        <div class={"icon " + (theme ? "dark" : "light")}>
          <FaArrowLeft />
        </div>
      </button>
      <h1>Contacto</h1>
    </div>

    <div class="contactContent">
      <div class="contactSelector">
        <div class="opt">
          <div class={"icon " + (theme ? "dark" : "light")}>
            <MdLocalPhone />
          </div>
        </div>
      </div>
      <div class="contactContainer"><h3>+502 30457189</h3></div>
    </div>
    <div class="contactContent">
        <div class="contactSelector">
          <div class="opt">
            <div class={"icon " + (theme ? "dark" : "light")}>
              <MdEmail/>
            </div>
          </div>
        </div>
        <div class="contactContainer"><h3>hm.sebastiansilva@gmail.com</h3></div>
      </div>
      <div class="contactContent">
        <div class="contactSelector">
          <div class="opt">
            <div class={"icon " + (theme ? "dark" : "light")}>
              <FaLinkedin/>
            </div>
          </div>
        </div>
        <div class="contactContainer"><a href="https://www.linkedin.com/in/hsilv/"><h3>LinkedIn</h3></a></div>
      </div>
  </div>
</div>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;
  $dark-hover: #404040;
  $light-hover: #bbbbbb;

  h3{
    font-size: calc(3vw);
  }

  a{
    text-decoration: none;
    color: inherit;
    &:visited{
        color: inherit;
    }
  }
  .contactContent {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 10px;
    padding-bottom: 10px;
    margin-top: 2vh;
  }

  .contactSelector {
    width: 40%;
    height: 100%;
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: repeat(1, 1fr);
    overflow-wrap: break-word;
    .opt{
        display: flex;
        align-items: center;
        justify-content: center;
    }
  }

  .contactContainer {
    width: 60%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .Contact {
    margin-top: 20px;
    margin-bottom: 20px;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .contactCard {
    padding: 20px;
    border-radius: 10px;
    margin-inline: 15px;
    margin-left: 15px;
    width: 75%;

    .contactHeader {
      display: flex;
      flex-direction: row;
      align-items: center;
      button {
        margin-right: 20px;
      }
    }

    .contactHeader.light {
      border-bottom: 1px solid $dark-color;
    }

    .contactHeader.dark {
      border-bottom: 1px solid $light-color;
    }
  }

  .contactCard.light {
    border: 1px solid $dark-color;
  }

  .contactCard.dark {
    border: 1px solid $light-color;
  }

  button {
    margin: 0;
    padding: 0;
    border: 0px;
    max-height: 45px;
  }
  .icon {
    max-width: 40px;
  }

  .icon.dark {
    background-color: $dark-color;
    color: $light-color;
  }

  .icon.light {
    background-color: $light-color;
    color: $dark-color;
  }

  @media (min-width: 745px) {
    h3{
    font-size: large;
  }
    .contactCard {
      max-width: 715px;
      .contactContainer {
        width: 75%;
      }
    }

    .contactSelector {
      width: 25%;
    }
  }
</style>
