<template>
  <div>
    <div class="photo_nav" v-if="!isDetailShow"><b-badge variant="secondary">All Photo</b-badge></div>
    <b-container class="photo-list" v-if="!isDetailShow">
      <b-row class="img_row" v-for="(k,i) in imgList">
        <b-col class="img_col" v-for="(img,i2) in k" v-on:click="onShowDetailPhoto(img, i, i2)">
          <img class="photo_image" v-bind:src="'http://1.223.87.53/thm/?w=300&h=300&zc=t&q=98&src=/ecard/photo/s/sample101/'+img+'.jpg'" width="100%">
        </b-col>
      </b-row>
    </b-container>
    <div v-if="isDetailShow">
      <div class="photo_nav">
        <b-badge variant="secondary" v-on:click="onShowDetailPhoto()" style="cursor: pointer;">< Back</b-badge>

        <b-badge class="arrow" variant="secondary" v-on:click="onChangeDetailPhoto('next')" style="cursor: pointer;">next ></b-badge>
        <b-badge class="arrow" variant="secondary" v-on:click="onChangeDetailPhoto('pre')" style="cursor: pointer;">< pre</b-badge>
      </div>
      <img class="photo_image" v-bind:src="'http://1.223.87.53/thm/?w=300&h=300&zc=t&q=98&src=/ecard/photo/s/sample101/'+detailPhotoSrc+'.jpg'" width="100%">
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        imgList: [
          ['e822400b0ce09c518ffddc8e8a1fe376', '639dab6ad8d0a3742368560b9dc491f3', 'c121009ad1bb9bb88b95509532236b66'],
          ['1a0be4b86fe76a8bb349a6ccaacdde33', 'c6a4b10ecc515bf48046b26d39ddc3a1', 'c0d75501b9077fb096ac3860dd3007fd'],
          ['4896c8f0fa3453621405ecb1b44a8ff7', '6f81a0ea962d21d8a7de4c756757acc5', '55746144d7caf601af1a0967caa08563']
        ],
        currentPhotoIdx: {r: 0, c: 0},
        isDetailShow: false,
        detailPhotoSrc: ''
      }
    },
    methods: {
      onShowDetailPhoto (img, i, i2) {
        if (img) {
          this.detailPhotoSrc = img
          this.isDetailShow = true
          this.currentPhotoIdx = {r: i, c: i2}
        } else {
          this.isDetailShow = false
        }
      },
      onChangeDetailPhoto (type) {
        let r = 0
        let c = 0
        if (type === 'pre') {
          if (this.currentPhotoIdx.r !== 0 && this.currentPhotoIdx.c === 0) {
            r = this.currentPhotoIdx.r - 1
            c = this.imgList[this.currentPhotoIdx.r].length - 1
          } else if (this.currentPhotoIdx.r === 0 && this.currentPhotoIdx.c === 0) {
            r = this.imgList.length - 1
            c = this.imgList[this.currentPhotoIdx.r].length - 1
          } else {
            r = this.currentPhotoIdx.r
            c = this.currentPhotoIdx.c - 1
          }
        } else {
          if (this.currentPhotoIdx.r !== this.imgList.length - 1 && this.currentPhotoIdx.c === this.imgList[this.currentPhotoIdx.r].length - 1) {
            r = this.currentPhotoIdx.r + 1
            c = 0
          } else if (this.currentPhotoIdx.r === this.imgList.length - 1 && this.currentPhotoIdx.c === this.imgList[this.currentPhotoIdx.r].length - 1) {
            r = 0
            c = 0
          } else {
            r = this.currentPhotoIdx.r
            c = this.currentPhotoIdx.c + 1
          }
        }
        this.currentPhotoIdx = {r: r, c: c}
        this.detailPhotoSrc = this.imgList[r][c]
      }
    }
  }
</script>
<style>
  .photo-list{
    padding-top: 5px !important;
    padding-bottom: 5px !important;
  }
  .img_row{
    padding: 0px 5px 0px 5px !important;
  }
  .img_col{
    padding: 5px !important;
  }
  .photo_nav{
    background: #bfbfbff0;
    height: 40px;
    line-height: 40px;
    padding-left: 20px;
    font-size: 14px;
  }
  .photo_nav > .arrow{
    float:right;
    margin: 12px 2px;
  }
</style>
