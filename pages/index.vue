<template>
  <div>
    <!-- 상단 네비 -->
    <b-navbar toggleable type="dark" variant="dark" sticky>
      <b-navbar-brand href="#home">HOME</b-navbar-brand>
      <b-navbar-brand href="#photo">PHOTO</b-navbar-brand>
      <b-navbar-brand href="#map">MAP</b-navbar-brand>
      <b-navbar-brand href="#message">MESSAGE</b-navbar-brand>
    </b-navbar>
    <!-- 상단 네비 -->

    <!-- 사진 -->
    <div id="home">
      <b-carousel id="carousel1"
                  style="text-shadow: 1px 1px 2px #333;"
                  controls
                  background="#ababab"
                  :interval="1500"
                  img-width="1024"
                  img-height="580"
                  v-model="slide"
                  @sliding-start="onSlideStart"
                  @sliding-end="onSlideEnd">

        <b-carousel-slide img-src="http://www.hawaiisnap.com/wp-content/uploads/ka_beach_22.jpg"></b-carousel-slide>
        <b-carousel-slide img-src="http://www.hawaiisnap.com/wp-content/uploads/ka_beach_12.jpg"></b-carousel-slide>
        <b-carousel-slide img-src="http://www.hawaiisnap.com/wp-content/uploads/ma_beach_41.jpg"></b-carousel-slide>
        <b-carousel-slide img-src="http://www.hawaiisnap.com/wp-content/uploads/ma_beach_31.jpg"></b-carousel-slide>
      </b-carousel>
      <!-- 상단 네비 -->

      <div class="w-card">
        <!-- 인사말 -->
        <div class="title">
          <span class="date">2017년 12월 8일,</span>
          <span class="name">김민준<span class="nlbr"></span>이서연<span class="nlbr"></span><span class="welcome">결혼합니다!</span></span>
        </div>
        <div class="desc">
          아름다운 가정을 이루어 <span class="nlbr"></span>
          서로 사랑하고 이웃을 섬기며 <span class="nlbr"></span>
          사랑을 나누는 행복한 부부가 되도록 <span class="nlbr"></span>
          기도해주시길 소망합니다. <span class="nlbr"></span>
        </div>
        <!-- 인사말 -->

        <!--전화걸기, 문자 보내기 서브 팝업 -->
        <table cellspacing="0" cellpadding="0" width="314" align="center">
          <tbody><tr>
            <td>
              <div v-if="showBtn.call" class="detail-show-btn">
                <div style="left:6px;">
                  <table cellspacing="0" cellpadding="0" height="76" border="0" style="background-image:url(http://bojagicard.com/g/img/140109_01_03.gif); background-size:145px 76px; background-repeat:no-repeat;">
                    <tbody><tr>
                      <td valign="top" style="padding-left:6px; padding-top:6px;  ">
                        <a href="tel:010-1566-2334" onclick=""><img src="http://bojagicard.com/g/img/131101_02_01_f.gif" height="48"></a></td>
                      <td valign="top" style="padding-left:6px; padding-top:6px;background-image:url(http://bojagicard.com/g/img/140109_01_02.gif); background-size:1px 76px; background-repeat:repeat-x;">
                        <a href="tel:010-2334-1566" onclick=""><img src="http://bojagicard.com/g/img/131101_02_01_m.gif" height="48"></a></td>
                      <td><img src="http://bojagicard.com/g/img/140109_01_01.gif" height="76"></td>
                    </tr></tbody>
                  </table>
                </div>
              </div>
              <div v-if="showBtn.sms" class="detail-show-btn">
                <div style="left:8px;">
                  <table cellspacing="0" cellpadding="0" height="76" border="0" style="background-image:url(http://bojagicard.com/g/img/140109_02_01.gif); background-size:145px 76px; background-repeat:no-repeat;">
                    <tbody><tr>
                      <td valign="top" style="padding-left:6px; padding-top:6px;">
                        <a target="_blank" href="sms:010-1566-2334" onclick=""><img src="http://bojagicard.com/g/img/140109_02_01_f.gif" height="48"></a></td>
                      <td valign="top" style="padding-left:6px; padding-top:6px;background-image:url(http://bojagicard.com/g/img/140109_01_02.gif); background-size:1px 76px; background-repeat:repeat-x;">
                        <a target="_blank" href="sms:010-2334-1566" onclick=""><img src="http://bojagicard.com/g/img/140109_02_01_m.gif" height="48"></a></td>
                      <td><img src="http://bojagicard.com/g/img/140109_01_01.gif" height="76"></td>
                    </tr></tbody>
                  </table>
                </div>
              </div>
            </td>
          </tr></tbody>
        </table>
        <!--전화걸기, 문자 보내기 서브 팝업 -->

        <!-- 연락하기 -->
        <table align="center" class="contact">
          <tbody>
            <tr>
              <td>
                <img class="btnsns" align="absmiddle" src="http://bojagicard.com/g/img/160926_02_01.png" width="36" height="36" v-on:click="onShowBtn('call')">
              </td>
              <td>
                <img class="btnsns" align="absmiddle" src="http://bojagicard.com/g/img/160926_02_02.png" width="36" height="36" v-on:click="onShowBtn('sms')">
              </td>
              <td>
                <img class="btnsns" align="absmiddle" src="http://bojagicard.com/g/img/160926_02_03.png" width="36" height="36" v-on:click="onShowBtnAction('kakao')">
              </td>
              <td>
                <img class="btnsns" align="absmiddle" src="http://bojagicard.com/g/img/160926_02_04.png" width="36" height="36" v-on:click="onShowBtnAction('story')">
              </td>
              <td>
                <img class="btnsns" align="absmiddle" src="http://bojagicard.com/g/img/160926_02_05.png" width="36" height="36" v-on:click="onShowBtnAction('fb')">
              </td>
            </tr>
          </tbody>
        </table>
        <!-- 연락하기 -->
      </div>


      <div id="photo">
        <photo></photo>
      </div>

    </div>

    <b-modal ref="myModalRef" hide-header hide-footer>
      <div class="d-block text-center">
        <h3>모바일에서만 가능합니다</h3>
      </div>
      <b-btn class="mt-3" variant="outline-danger" block v-on:click="hideModal()">Close</b-btn>
    </b-modal>
  </div>
</template>



<script>
import Photo from '~/components/Photo.vue'

export default {
  components: {
    Photo
  },
  data () {
    return {
      slide: 0,
      sliding: null,
      showBtn: {call: false, sms: false}
    }
  },
  methods: {
    onSlideStart (slide) {
      this.sliding = true
    },
    onSlideEnd (slide) {
      this.sliding = false
    },
    onShowBtn (type) {
      const already = this.showBtn[type]
      this.showBtn = {call: false, sms: false}
      if (!already) {
        this.showBtn[type] = !this.showBtn[type]
      }
    },
    onShowBtnAction (type) {
      this.showBtn = {call: false, sms: false}
      if (type === 'fb') {
        window.open('http://m.facebook.com/sharer.php?u=http://bojagicard.com/g/home.php?ecard=sample101')
      } else {
        this.$refs.myModalRef.show()
      }
    },
    hideModal () {
      this.$refs.myModalRef.hide()
    }

  }
}
</script>

<style>
  .w-card {
    margin: 0 auto;
    background: rgb(233, 233, 233);
  }

  .w-card > div {
    padding: 40px 40px 20px;
  }

  .w-card > div ~ div {
    padding-top: 20px;
  }

  .title {
    color: #4a4a4a;
    font-size: 30px;
    font-weight: bold;
    letter-spacing: -0.05em;
    line-height: 1.3;
  }

  .title .date {
    color: #695b1d;
  }

  .title .name {
    display: block;
    font-size: 24px;
  }

  .desc {
    line-height: 1.85;
    font-size: 13px;
    word-break: keep-all;
    color: #7a6d61;
  }

  .nlbr {
    display: block;
  }

  .btnsns {
    margin: 0px 10px 10px 10px;
  }

  .detail-show-btn {
    position: relative;
  }

  .detail-show-btn > div {
    position:absolute;
    top:-86px;
    z-index:3;
    width:100%;
  }

</style>
