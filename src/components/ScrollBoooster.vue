<template>
  <div id="scroll">
    <div class="wrapper">
      <div class="inner">
      <img src="../assets/bread.jpg" />
      </div>
    </div>
  </div>
</template>

<script>
  import ScrollBooster from "scrollbooster";

  export default {
    name: "ScrollBoooster",
    mounted: function () {
      setTimeout(() => {
        // 需要等到图片加载完成后才能正常运行
        const viewportEl = document.querySelector("#scroll .wrapper");
        let sb;

        sb = new ScrollBooster({
          viewport: viewportEl,
          emulateScroll: true,
          onUpdate: function (data) {
            console.log(data.position.y)
            console.log(data.position.x)
            viewportEl.scrollTop = data.position.y;
            viewportEl.scrollLeft = data.position.x;
          }
        });

        console.log(sb)

        sb.setPosition({ x: 200, y: 200 });
      });
    }
  }
</script>

<style lang="less">
  body {
    background-color: #2B2B2B;
  }

  #testapp {
    padding: 50px;
    text-align: center;
  }

  /* .wrapper {
    overflow: hidden;
    margin: auto;
    width: 1400px;
    height: 700px;
    border: 2px solid orange;
  } */

  .inner {
    background: skyblue;
    /* width: 3000px; */
    /* height: 1000px; */
  }

  #scroll .wrapper {
    overflow: scroll;
    width: 1400px;
    height: 700px;

  }
</style>