<script>
  import FaArrowLeft from "svelte-icons/fa/FaArrowLeft.svelte";
  import { Router, Link, Route, navigate } from "svelte-routing";
  import IoIosCloud from "svelte-icons/io/IoIosCloud.svelte";
  import FaServer from "svelte-icons/fa/FaServer.svelte";
  import IoIosBrowsers from "svelte-icons/io/IoIosBrowsers.svelte";
  import jsVanillaDark from "../../assets/brand-js-svgrepo-com (1).svg";
  import jsVanillaLight from "../../assets/brand-js-svgrepo-com (2).svg";
  import reactLight from '../../assets/react-svgrepo-com.svg'
  import reactDark from '../../assets/react-svgrepo-com (1).svg'
  import angLight from '../../assets/angular-svgrepo-com.svg'
  import angDark from '../../assets/angular-svgrepo-com (1).svg'
  import svelteLight from '../../assets/Svelte_Logo.svg';
  import svelteDark from '../../assets/Svelte_Logo (1).svg';
  import nodeDark from '../../assets/node-svgrepo-com (2).svg'
  import nodeLight from '../../assets/node-svgrepo-com (3).svg'
  import flaskDark from '../../assets/flask-svgrepo-com.svg'
  import flaskLight from '../../assets/flask-svgrepo-com (1).svg'
  import { afterUpdate } from "svelte";
  export let theme;

  let frontOpt = "Angular";
  let frontImg = theme? angDark : angLight;
  let frontDesc = "Angular es una tecnología que fue rediseñada a partir de uno de los primeros Frameworks que fue AngularJS, es un framework que utiliza TypeScript y que se encarga de renderizar únicamente lo que se ha cambiado por medio de Observables";

  let backOpt = "ExpressJS";
  let backImg = theme? nodeDark: nodeLight;
  let backDesc = "NodeJS es un entorno que permite desarrollar el Backend en el lado de un servidor ya sea local, o extranjero. A partir de esto podemos crear servicios que sirvan a nuestras aplicaciones en el Frontend por medio de API's y demás, en este caso, he usado ExpressJS"

  let skill = "Frontend";

  function goBack() {
    navigate("/", { replace: true });
  }

  function setSkill(event) {
    skill = event.target.id;
  }

  function setFront(event) {
    frontOpt = event.target.id;
    if (frontOpt === "Vanilla") {
      if (theme) {
        frontImg = jsVanillaLight;
      } else {
        frontImg = jsVanillaDark;
      }
      frontDesc = "JavaScript Vanilla refiere al uso de JavaScript sin librerías ni frameworks agregados, esto quiere decir que es posible utilizarse shadowDom, o manejarse el Dom directamente desde JavaScript, sin necesidad de intermediarios"
    } else if(frontOpt === 'React') {
        if (theme) {
        frontImg = reactDark;
      } else {
        frontImg = reactLight;
      }
      frontDesc = "React es una librería orientada a componentes, útil para aplicaciones web de alta envergadura que requieran reutilización y refinamiento de los recursos con el fin de ofrecer una aplicación rápida, además de emular reactividad por medio de su Virtual DOM"
    } else if(frontOpt === 'Angular') {
        if (theme) {
        frontImg = angDark;
      } else {
        frontImg = angLight;
      }
      frontDesc = "Angular es una tecnología que fue rediseñada a partir de uno de los primeros Frameworks que fue AngularJS, es un framework que utiliza TypeScript y que se encarga de renderizar únicamente lo que se ha cambiado por medio de Observables"
    } else if(frontOpt === 'Svelte') {
        if (theme) {
        frontImg = svelteDark;
      } else {
        frontImg = svelteLight;
      }
      frontDesc = "Svelte es un framework relativamente nuevo que no utiliza un Virtual DOM, lo que quiere decir que es más rápido a la hora de renderizar, además utiliza una sintaxis primitiva que se explica por sí misma, debido a que se parece mucho a Vanilla HTML, CSS y JS"
    }
  }

  function setBack(event) {
    backOpt = event.target.id;
    if (backOpt === "ExpressJS") {
      if (theme) {
        backImg = nodeDark;
      } else {
        backImg = nodeLight;
      }
      backDesc = "NodeJS es un entorno que permite desarrollar el Backend en el lado de un servidor ya sea local, o extranjero. A partir de esto podemos crear servicios que sirvan a nuestras aplicaciones en el Frontend por medio de API's y demás, en este caso, he usado ExpressJS"
    } else if (backOpt === 'Flask'){
        if (theme) {
        backImg = flaskLight;
      } else {
        backImg = flaskDark;
      }
      backDesc = "Flask es una librería orientada al Backend en Python. Es considerada una versión mucho más ligera que DJango, sin embargo, puede conectarse a bases de datos, manejar routing de forma fácil además de ofrecer buena rapidez de desarrollo y respuesta."
    }
  }
</script>

<div class="Skills">
  <div class={"skillCard " + (theme ? "dark" : "light")}>
    <div class={"cardHeader " + (theme ? "dark" : "light")}>
      <button on:click={goBack} class={theme ? "dark" : "light"}>
        <div class={"icon " + (theme ? "dark" : "light")}>
          <FaArrowLeft />
        </div>
      </button>
      <h1>Habilidades que poseo</h1>
    </div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class={"skillSelector " + (theme ? "dark" : "light")}>
      <div
        class={"option " + (theme ? "dark" : "light")}
        id="Frontend"
        on:mouseenter={setSkill}
      >
        <div
          class={"icon " + (theme ? "dark" : "light")}
          id="Frontend"
          on:mouseenter={setSkill}
        >
          <IoIosBrowsers id="Frontend" on:mouseenter={setSkill}/>
        </div>
        <span id="Frontend" on:mouseenter={setSkill}>Frontend</span>
      </div>
      <div
        class={"option last " + (theme ? "dark" : "light")}
        id="Backend"
        on:mouseenter={setSkill}
      >
        <div
          class={"icon " + (theme ? "dark" : "light")}
          id="Backend"
          on:mouseenter={setSkill}
        >
          <FaServer id="Backend" on:mouseenter={setSkill} />
        </div>
        <span id="Backend" on:mouseenter={setSkill}>Backend</span>
      </div>
    </div>
    <div class="skillContent">

      <div class={"skill front " + (skill === "Frontend" ? "" : "shadow")}>
        <div class="aboutSkill">
          <h1>Frontend</h1>
          <div class={"icon" + (theme ? "dark" : "light")} />
            <div class="skillImg">
                <img src={frontImg} alt="imagen" />
                {frontOpt}
            </div>

          <br>
          {frontDesc}
        </div>
        <div class={"skillList " + (theme ? "dark" : "light")}>
          <!-- svelte-ignore a11y-click-events-have-key-events -->
          <div
            class={"opt " + (theme ? "dark" : "light")}
            id="Angular"
            on:mouseenter={setFront}
          >
            <h2 id="Angular" on:mouseenter={setFront}>Angular</h2>
          </div>
          <!-- svelte-ignore a11y-click-events-have-key-events -->
          <div
            class={"opt " + (theme ? "dark" : "light")}
            id="React"
            on:mouseenter={setFront}
          >
            <h2 id="React" on:mouseenter={setFront}>React</h2>
          </div>
          <!-- svelte-ignore a11y-click-events-have-key-events -->
          <div
            class={"opt " + (theme ? "dark" : "light")}
            id="Svelte"
            on:mouseenter={setFront}
          >
            <h2 id="Svelte" on:mouseenter={setFront}>Svelte</h2>
          </div>
          <!-- svelte-ignore a11y-click-events-have-key-events -->
          <div
            class={"opt " + (theme ? "dark" : "light")}
            id="Vanilla"
            on:mouseenter={setFront}
          >
            <h2 id="Vanilla" on:mouseenter={setFront}>Vanilla</h2>
          </div>
        </div>
      </div>

      <div class={"skill back " + (skill === "Backend" ? "" : "shadow")}>
        <div class="aboutSkill">
          <h1>Backend</h1>
          <div class={"icon" + (theme ? "dark" : "light")} />
            <div class="skillImg">
                <img src={backImg} alt="imagen" />
                {backOpt}
            </div>

          <br>
          {backDesc}
        </div>
        <div class={"skillList " + (theme ? "dark" : "light")}>
          <!-- svelte-ignore a11y-click-events-have-key-events -->
          <div
            class={"opt " + (theme ? "dark" : "light")}
            id="ExpressJS"
            on:mouseenter={setBack}
          >
            <h2 id="ExpressJS" on:mouseenter={setBack}>ExpressJS</h2>
          </div>
          <!-- svelte-ignore a11y-click-events-have-key-events -->
          <div
            class={"opt " + (theme ? "dark" : "light")}
            id="Flask"
            on:mouseenter={setBack}
          >
            <h2 id="Flask" on:mouseenter={setBack}>Flask</h2>
          </div>
        </div>
      </div>

    </div>
  </div>
</div>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;
  $dark-hover: #404040;
  $light-hover: #bbbbbb;

  .skillImg{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .aboutSkill {
    width: 60%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    img{
        max-width: 5vw;
        width: 5vw;
        margin-block: 1vh;
    }
  }

  .skillList {
    width: 40%;
    height: 100%;
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: repeat(1, 1fr);
    margin-top: 2vh;

    .opt {
      display: flex;
      top: 50%;
      left: 50%;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      h2 {
        padding: 0;
      }
    }

    .opt.dark {
      &:hover {
        background-color: $dark-hover;
      }
    }

    .opt.light {
      &:hover {
        background-color: $light-hover;
      }
    }
  }

  .skillList.dark {
    border-left: 1px solid $light-color;
  }

  .skillList.light {
    border-left: 1px solid $dark-color;
  }

  .skillSelector {
    margin-top: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 10px;

    .option {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      width: 100%;
      cursor: pointer;
    }

    .option.last.dark {
      border-right: 1px solid $light-color;
    }

    .option.last.light {
      border-right: 1px solid $dark-color;
    }

    .option.light {
      border-left: 1px solid $dark-color;
      &:hover {
        background-color: #bbbbbb;
        .icon {
          background-color: #bbbbbb;
        }
      }
    }

    .option.dark {
      border-left: 1px solid $light-color;
      &:hover {
        background-color: #404040;
        .icon {
          background-color: #404040;
        }
      }
    }
  }

  .skillSelector.light {
    border-bottom: 1px solid $dark-color;
  }

  .skillSelector.dark {
    border-bottom: 1px solid $light-color;
  }

  .skillCard {
    padding: 20px;
    border-radius: 10px;
    margin-inline: 15px;
    margin-left: 15px;
    width: 75%;

    .cardHeader {
      display: flex;
      flex-direction: row;
      align-items: center;
      button {
        margin-right: 20px;
      }
    }

    .cardHeader.light {
      border-bottom: 1px solid $dark-color;
    }

    .cardHeader.dark {
      border-bottom: 1px solid $light-color;
    }
  }

  .skillCard.light {
    border: 1px solid $dark-color;
  }

  .skillCard.dark {
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

  .Skills {
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

  .skill {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: row;
  }

  @media (min-width: 745px) {
    .skillCard {
      max-width: 715px;
    }

    .aboutSkill {
      width: 75%;
    }

    .skillList {
      width: 25%;
    }
  }

  .shadow {
    display: none;
  }
</style>
