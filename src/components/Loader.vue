<template>
    <div class="loader">
        <div class="lds-css ng-scope">
            <div style="width:100%;height:100%" class="lds-dual-ring">
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Loader',
        };
</script>

<style type="text/css"> 

    @keyframes lds-dual-ring {
  0% {
    -webkit-transform: rotate(0);
    transform: rotate(0);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@-webkit-keyframes lds-dual-ring {
  0% {
    -webkit-transform: rotate(0);
    transform: rotate(0);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
.lds-dual-ring {
  position: relative;
}
.lds-dual-ring {
  position: absolute;
  top: 15%;
  left: 47%;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: 8px solid #000;
  border-color: #28292f transparent #28292f transparent;
  -webkit-animation: lds-dual-ring 1.2s linear infinite;
  animation: lds-dual-ring 1.2s linear infinite;
}
.lds-dual-ring {
  width: 100px !important;
  height: 100px !important;
  -webkit-transform: translate(-100px, -100px) scale(1) translate(100px, 100px);
  transform: translate(-100px, -100px) scale(1) translate(100px, 100px);
}
</style>
