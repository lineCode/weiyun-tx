<template>
  <div>
    <div id="all">
      <div class="all-view">
        <div class="pics_content clearfix">
          <h2>图片({{pictures.length}}) ---^_^----<slot style="padding-left: 10px">友情提示，不要上传大文件哦</slot></h2>
          <div class="divider"></div>
          <div class="content">            
            <ul>
              <li v-for="item in pictures" :class="bView ? 'thum_view' : 'list_view'">
                <img :src="item.url">                                
                <p v-show="!bView">{{item.name}}</p>
                <p class="createdAt" v-show="!bView">{{item.createdAt.split('T')[0]}} {{item.createdAt.split('T')[1].split('.')[0]}}</p>
                <a :href="item.url" :class="bView ? 'cover' : 'rightBtn'" target="_blank">查看大图</a>
              </li>
            </ul>
          </div>
        </div> 
        <div class="videos_content clearfix">
          <h2>视频({{videos.length}})</h2>
          <div class="divider"></div>
          <div class="content">
            <ul>
              <li v-for="item in videos" :class="bView ? 'thum_view' : 'list_view'">
                <video v-show="bView" :src="item.url"></video>
                <p v-show="!bView">{{item.name}}</p>
                <p class="createdAt" v-show="!bView">{{item.createdAt.split('T')[0]}} {{item.createdAt.split('T')[1].split('.')[0]}}</p>
                <a :href="item.url" :class="bView ? 'cover' : 'rightBtn'" target="_blank">播放</a>
              </li>
            </ul>
          </div>
        </div>
        <div class="musics_content clearfix">
          <h2>音乐({{musics.length}})</h2>
          <div class="divider"></div>
          <div class="content">
            <ul>
              <li v-for="item in musics" class="list_view">
                <audio :src="item.url" controls></audio>
                <p>{{item.name}}</p>
                <p class="createdAt">{{item.createdAt.split('T')[0]}} {{item.createdAt.split('T')[1].split('.')[0]}}</p>
                <a :href="item.url" class="rightBtn" target="_blank">下载</a>
              </li>
            </ul>
          </div>
        </div>
        <div class="docs_content clearfix">
          <h2>文档({{pdfs.length}})</h2>
          <div class="divider"></div>
          <div class="content">
            <ul>
              <li v-for="item in pdfs" class="list_view">
                <p><a :href="item.url" target="_blank">{{item.name}}</a></p>
                <p class="createdAt">{{item.createdAt.split('T')[0]}} {{item.createdAt.split('T')[1].split('.')[0]}}</p>
                <a :href="item.url" class="rightBtn" target="_blank">查看</a>
              </li>
            </ul>
          </div>
        </div>
        <div class="others_content clearfix">
          <h2>其他({{others.length}})</h2>
          <div class="divider"></div>
          <div class="content">
            <ul>
              <li v-for="item in others" class="list_view">
                <p><a :href="item.url" target="_blank">{{item.name}}</a></p>
                <p class="createdAt">{{item.createdAt.split('T')[0]}} {{item.createdAt.split('T')[1].split('.')[0]}}</p>
                <a :href="item.url" class="rightBtn" target="_blank">查看</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  computed: {
    ...mapGetters({
      pictures: 'getPictures',
      musics: 'getMusics',
      videos: 'getVideos',
      pdfs: 'getPdfs',
      others: 'getOthers',     

      bView: 'getBview'
    })
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

</style>
