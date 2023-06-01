<script>
  export let theme;
  import Img from "../../assets/sun-svgrepo-com.svg";
  import AboutMe from "../../assets/about-svgrepo-com.svg";
  import Skills from "../../assets/know-svgrepo-com.svg";
  import Projects from "../../assets/project-svgrepo-com.svg";
  import Social from "../../assets/social-contact-svgrepo-com.svg";
  import { afterUpdate } from "svelte";
  import { Router, Link, Route, navigate } from "svelte-routing";

  let imgLoaded = false;

  let img = AboutMe;

  function handleHover(event) {
    imgLoaded = false;
    if (event.target.id === "menu1") {
      img = AboutMe;
    } else if (event.target.id === "menu2") {
      img = Skills;
    } else if (event.target.id === "menu3") {
      img = Projects;
    } else if (event.target.id === "menu4") {
      img = Social;
    }
  }

  function handleRedir(event) {
    let item = event.target.id;
    if(item === 'menu1'){
        navigate('/about', {replace: false})
    }else if(item === 'menu2'){
        navigate('/skills', {replace: false})
    }else if(item === 'menu3'){
        navigate('/projects', {replace: false})
    }else if(item === 'menu4'){
        navigate('/contact', {replace: false})
    }
  }

  afterUpdate(() => {
    imgLoaded = true;
  });
</script>

<div class="menu">
  <div class={"menuCard " + (theme ? "dark" : "light")}>
    <h1>Bienvenido!</h1>
    <div class="optionsContainer">
      <img src={img} alt="" class={"fade " + (imgLoaded ? "loaded" : "")} />
      <div class="options">
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div
          class={"option " + (theme ? "dark" : "light")}
          on:mouseenter={handleHover} on:click={handleRedir}
          id="menu1">
          <h1 id="menu1">Acerca de mí</h1>
        </div>
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div
          class={"option " + (theme ? "dark" : "light")}
          on:mouseenter={handleHover} on:click={handleRedir}
          id="menu2"
        >
          <h1 id="menu2">Habilidades</h1>
        </div>
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div
          class={"option " + (theme ? "dark" : "light")}
          on:mouseenter={handleHover} on:click={handleRedir}
          id="menu3"
        >
          <h1 id="menu3">Proyectos</h1>
        </div>
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div
          class={"option last " + (theme ? "dark" : "light")}
          on:mouseenter={handleHover} on:click={handleRedir}
          id="menu4"
        >
          <h1 id="menu4">Contacto</h1>
        </div>
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;

  .fade {
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .fade.loaded {
    opacity: 1;
  }

  .option {
    display: flex;
    top: 50%;
    left: 50%;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    h1 {
      padding: 0;
    }
  }

  .option.last.light {
    border-bottom: 0px;
  }

  .option.last.dark {
    border-bottom: 0px;
  }
  .option.light {
    width: 100%;
    height: 100%;
    border-bottom: 1px solid $dark-color;

    &:hover {
      background-color: #bbbbbb;
    }
  }

  .option.dark {
    width: 100%;
    height: 100%;
    border-bottom: 1px solid $light-color;

    &:hover {
      background-color: #404040;
    }
  }

  .optionsContainer {
    display: flex;
    flex-direction: row;
    img {
      max-width: 30vw;
    }
  }

  .options {
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: repeat(4, 1fr);
    align-items: center;
    width: 100%;
  }

  .menu {
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

    h1 {
      padding-inline: 2vw;
    }

    .menuCard.dark {
      border: 1px solid $light-color;
      border-radius: 10px;
      background-color: $dark-color;
      padding-top: 10px;
      .options {
        border-top: 1px solid $light-color;
      }
      img {
        border-right: 1px solid $light-color;
        border-top: 1px solid $light-color;
      }
    }

    .menuCard.light {
      border: 1px solid $dark-color;
      border-radius: 10px;
      background-color: $light-color;
      padding-top: 10px;
      .options {
        border-top: 1px solid $dark-color;
      }
      img {
        border-right: 1px solid $dark-color;
        border-top: 1px solid $dark-color;
      }
    }
  }
</style>
