<script>
  export let position;
</script>

<style>

.boxflex {
  display: flex;
  justify-content: center;
  align-items: center;
}
.boxflex.full {
  position:absolute;
  top:0;
  left:0;
  width: 100vw;
  height:100vh;

}
  .loader {
    width: 130px;
    height: 170px;
    position: relative;
  }
  .loader::before,
  .loader::after {
    content: "";
    width: 0;
    height: 0;
    position: absolute;
    bottom: 30px;
    left: 15px;
    z-index: 1;
    transform: scale(0);
    transition: all 0.2s ease;
  }
  .loader .txt {
    width: 120%;
    text-align: center;
    position: absolute;
    bottom: -30px;
    left: -7%;
    font-family: "Abel", sans-serif;
    font-size: 12px;
    letter-spacing: 2px;
    color: white;
  }
  .loader .code {
    position: absolute;
    z-index: 99;
    bottom: -3px;
    -webkit-animation-name: spaceboots;
    -webkit-animation-duration: 0.8s;
    -webkit-transform-origin: 50% 50%;
    -webkit-animation-iteration-count: infinite;
    -webkit-animation-timing-function: linear;
  }
  .loader .box {
    width: 100%;
    height: 140px;
    display: block;
    color: white;
    position: absolute;
    top: -70px;
    left: -18px;
    z-index: 2;
    overflow: hidden;
  }
  .loader .box::before,
  .loader .box::after {
    display: inline-block;
    font: normal normal normal 14px/1 FontAwesome;
    font-size: inherit;
    text-rendering: auto;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
  }
  .loader .box:nth-child(1)::before {
    font-size: 20px;
    content: "\f13b";
    animation: a 1.1s linear infinite;
  }
  .loader .box:nth-child(1)::after {
    content: "\f13c";
    animation: b 1.3s linear infinite;
  }
  .loader .box:nth-child(2)::before {
    content: "\f121";
    font-size: 25px;
    animation: c 0.9s linear infinite;
  }
  .loader .box:nth-child(2)::after {
    content: "\f19a ";
    animation: d 0.7s linear infinite;
  }
  .loader.amit::before,
  .loader.amit::after {
    transform: scale(1);
  }

  @keyframes a {
    0% {
      transform: translate(30px, 0) rotate(30deg);
      opacity: 0;
    }
    100% {
      transform: translate(30px, 150px) rotate(-50deg);
      opacity: 1;
    }
  }
  @keyframes b {
    0% {
      transform: translate(50px, 0) rotate(-40deg);
      opacity: 0;
    }
    100% {
      transform: translate(40px, 150px) rotate(80deg);
      opacity: 1;
    }
  }
  @keyframes c {
    0% {
      transform: translate(70px, 0) rotate(10deg);
      opacity: 0;
    }
    100% {
      transform: translate(60px, 150px) rotate(70deg);
      opacity: 1;
    }
  }
  @keyframes d {
    0% {
      transform: translate(30px, 0) rotate(-50deg);
      opacity: 0;
    }
    100% {
      transform: translate(45px, 150px) rotate(30deg);
      opacity: 1;
    }
  }
  @-webkit-keyframes spaceboots {
    0% {
      -webkit-transform: translate(2px, 1px) rotate(0deg);
    }
    10% {
      -webkit-transform: translate(-1px, -2px) rotate(-1deg);
    }
    20% {
      -webkit-transform: translate(-3px, 0px) rotate(1deg);
    }
    30% {
      -webkit-transform: translate(0px, 2px) rotate(0deg);
    }
    40% {
      -webkit-transform: translate(1px, -1px) rotate(1deg);
    }
    50% {
      -webkit-transform: translate(-1px, 2px) rotate(-1deg);
    }
    60% {
      -webkit-transform: translate(-3px, 1px) rotate(0deg);
    }
    70% {
      -webkit-transform: translate(2px, 1px) rotate(-1deg);
    }
    80% {
      -webkit-transform: translate(-1px, -1px) rotate(1deg);
    }
    90% {
      -webkit-transform: translate(2px, 2px) rotate(0deg);
    }
    100% {
      -webkit-transform: translate(1px, -2px) rotate(-1deg);
    }
  }
</style>

<div class={`boxflex ${position}`}>
<div class="loader">
  <span class="box" />
  <span class="box" />
  <div class="code">
    <svg width="64" height="64" xmlns="http://www.w3.org/2000/svg">

      <g>
        <title>Layer 1</title>
        <g stroke="null" id="svg_1">
          <path
            stroke="null"
            id="svg_2"
            d="m62.26543,15.33037l0,-9.45795c0,-2.28161 -1.85624,-4.13785
            -4.13785,-4.13785l-52.25516,0c-2.28161,0 -4.13785,1.85624
            -4.13785,4.13785l0,9.45795c0,1.64734 0.96778,3.07253
            2.36449,3.73778l0,32.55709l-0.59112,0c-0.97937,0 -1.77337,0.79399
            -1.77337,1.77337l0,7.09346c0,0.97937 0.79399,1.77337
            1.77337,1.77337l56.98413,0c0.97937,0 1.77337,-0.79399
            1.77337,-1.77337l0,-7.09346c0,-0.97937 -0.79399,-1.77337
            -1.77337,-1.77337l-0.59112,0l0,-32.55709c1.3967,-0.66537
            2.36449,-2.09044
            2.36449,-3.73778zm-3.54673,43.38833l-53.4374,0l0,-3.54673l53.4374,0l0,3.54673zm-43.38833,-28.61029l1.77337,0l0,2.95561c0,0.97937
            0.79399,1.77337 1.77337,1.77337s1.77337,-0.79399
            1.77337,-1.77337l0,-2.95561l1.77337,0c0.97937,0 1.77337,-0.79399
            1.77337,-1.77337l0,-5.3201l0.59112,0c0.76337,0 1.44092,-0.48838
            1.68233,-1.21263l0.77815,-2.3341l9.50252,0l0.77803,2.3341c0.24141,0.72424
            0.91908,1.21263 1.68233,1.21263l0.59112,0l0,5.3201c0,0.97937
            0.79399,1.77337 1.77337,1.77337l1.77337,0l0,2.95561c0,0.97937
            0.79399,1.77337 1.77337,1.77337s1.77337,-0.79399
            1.77337,-1.77337l0,-2.95561l1.77337,0c0.97937,0 1.77337,-0.79399
            1.77337,-1.77337l0,-5.3201l0.59112,0c0.76326,0 1.44092,-0.48838
            1.68233,-1.21263l0.77815,-2.3341l2.85961,0l0,32.15702l-4.26021,0c0.45493,-0.88751
            0.71348,-1.89159 0.71348,-2.95561l0,-7.09346c0,-0.97937
            -0.79399,-1.77337 -1.77337,-1.77337l-11.82243,0c-0.97937,0
            -1.77337,0.79399 -1.77337,1.77337l0,1.77337l-1.77337,0c-0.97937,0
            -1.77337,0.79399 -1.77337,1.77337s0.79399,1.77337
            1.77337,1.77337l1.77337,0l0,1.77337c0,1.06402 0.25856,2.0681
            0.71348,2.95561l-12.30361,0c0.45505,-0.88751 0.71348,-1.89159
            0.71348,-2.95561l0,-1.77337l1.77337,0c0.97937,0 1.77337,-0.79399
            1.77337,-1.77337s-0.79399,-1.77337
            -1.77337,-1.77337l-1.77337,0l0,-1.77337c0,-0.97937 -0.79399,-1.77337
            -1.77337,-1.77337l-11.82243,0c-0.97937,0 -1.77337,0.79399
            -1.77337,1.77337l0,7.09346c0,1.06402 0.25856,2.0681
            0.71348,2.95561l-4.26021,0l0,-32.15702l2.85961,0l0.77815,2.3341c0.24141,0.72424
            0.91896,1.21263 1.68233,1.21263l0.59112,0l0,5.3201c0,0.97937
            0.79399,1.77337
            1.77337,1.77337zm1.77337,-3.54673l0,-3.54673l3.54673,0l0,3.54673l-3.54673,0zm26.2458,0l0,-3.54673l3.54673,0l0,3.54673l-3.54673,0zm5.91122,16.78786l0,5.3201c0,1.62972
            -1.32589,2.95561 -2.95561,2.95561l-2.36449,0c-1.62972,0
            -2.95561,-1.32589
            -2.95561,-2.95561l0,-5.3201l8.2757,0zm-26.2458,0l0,5.3201c0,1.62972
            -1.32589,2.95561 -2.95561,2.95561l-2.36449,0c-1.62972,0
            -2.95561,-1.32589
            -2.95561,-2.95561l0,-5.3201l8.2757,0zm35.70375,-28.01917c0,0.32594
            -0.26518,0.59112 -0.59112,0.59112l-5.91122,0c-0.76326,0
            -1.44092,0.48838
            -1.68233,1.21263l-0.77815,2.3341l-9.26607,0l-0.77803,-2.3341c-0.24141,-0.72424
            -0.91908,-1.21263 -1.68233,-1.21263l-12.05888,0c-0.76337,0
            -1.44092,0.48838
            -1.68233,1.21263l-0.77815,2.3341l-9.26607,0l-0.77815,-2.3341c-0.2413,-0.72424
            -0.91884,-1.21263 -1.68221,-1.21263l-5.91122,0c-0.32594,0
            -0.59112,-0.26518 -0.59112,-0.59112l0,-9.45795c0,-0.32594
            0.26518,-0.59112 0.59112,-0.59112l52.25516,0c0.32594,0
            0.59112,0.26518 0.59112,0.59112l0,9.45795z" />
          <path
            stroke="null"
            id="svg_3"
            d="m27.1528,12.37476l9.6944,0c0.97937,0 1.77337,-0.79399
            1.77337,-1.77337s-0.79399,-1.77337
            -1.77337,-1.77337l-9.6944,0c-0.97937,0 -1.77337,0.79399
            -1.77337,1.77337s0.79399,1.77337 1.77337,1.77337z" />
          <circle
            stroke="null"
            id="svg_4"
            r="1.77337"
            cy="10.60139"
            cx="46.30515" />
          <circle
            stroke="null"
            id="svg_5"
            r="1.77337"
            cy="10.60139"
            cx="53.39861" />
          <circle
            stroke="null"
            id="svg_6"
            r="1.77337"
            cy="10.60139"
            cx="17.69485" />
          <circle
            stroke="null"
            id="svg_7"
            r="1.77337"
            cy="10.60139"
            cx="10.60139" />
        </g>
      </g>
    </svg>
  </div>
  <span class="txt">LOADING CODE...</span>
</div>
</div>
