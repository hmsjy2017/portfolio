<template>
  <div class="container">
    <h1>📈</h1>
    <h1>Stats</h1>
    <p>各项指标，实时监控！</p>

    <hr id="top-hr" />
    <div class="col-container">
      <div class="row-container">
      </div>
      <div class="row-container">
        <statCard
          statTitle="少数派"
          :followers="sspai"
          suffix="关注"
          icon="sspai.png"
          :loading="loading"
          link="https://sspai.com/u/ofzy2vd8/posts"
        />
        <statCard
          statTitle="微博"
          :followers="weibo"
          suffix="粉丝"
          icon="weibo.png"
          :loading="loading"
          link="https://weibo.com/hmsjy"
        />
      </div>
      <div class="row-container">
        <statCard
          statTitle="知乎"
          :followers="zhihu"
          suffix="关注"
          icon="zhihu.png"
          :loading="loading"
          link="https://www.zhihu.com/people/tony-15-37-99"
        />
        <statCard
          statTitle="Twitter"
          :followers="twitter"
          suffix="followers"
          icon="twitter.png"
          :loading="loading"
          link="https://twitter.com/hmsjy2017"
        />
      </div>
      <div class="row-container">
        <statCard
          statTitle="GitHub"
          :followers="github"
          suffix="followers"
          icon="github.png"
          :loading="loading"
          link="https://github.com/hmsjy2017"
        />
      </div>
    </div>

    <div id="substats-footer">
      * Follower statistics powered by:
      <a href="https://api.spencerwoo.com/substats">Substats</a>.
    </div>
  </div>
</template>

<script>
import statCard from '@/components/StatCard.vue'

export default {
  components: {
    statCard,
  },
  data() {
    return {
      rss: 0,
      sspai: 0,
      zhihu: 0,
      weibo: 0,
      twitter: 0,
      medium: 0,
      github: 0,
      steamGames: 0,
      steamFriends: 0,
      telegram: 0,
      loading: true,
    }
  },
  mounted() {
    const apiUrl = 'https://api.spencerwoo.com/
    const sspaiAxios = this.axios.get(`${apiUrl}/?source=sspai&queryKey=ofzy2vd8`)
    const zhihuAxios = this.axios.get(`${apiUrl}/?source=zhihu&queryKey=tony-15-37-99`)
    const weiboAxios = this.axios.get(`${apiUrl}/?source=weibo&queryKey=hmsjy`)
    const twitterAxios = this.axios.get(`${apiUrl}/?source=twitter&queryKey=hmsjy2017`)
    const githubAxios = this.axios.get(`${apiUrl}/?source=github&queryKey=hmsjy2017`)
  

    this.axios
      .all([
        rssAxios,
        sspaiAxios,
        zhihuAxios,
        weiboAxios,
        twitterAxios,
        mediumAxios,
        githubAxios,
        steamGamesAxios,
        steamFriendsAxios,
        telegramAxios,
      ])
      .then(
        this.axios.spread((...responses) => {
          this.loading = false
          this.rss = responses[0].data.data.totalSubs
          this.sspai = responses[1].data.data.totalSubs
          this.zhihu = responses[2].data.data.totalSubs
          this.weibo = responses[3].data.data.totalSubs
          this.twitter = responses[4].data.data.totalSubs
          this.medium = responses[5].data.data.totalSubs
          this.github = responses[6].data.data.totalSubs
          this.steamGames = responses[7].data.data.totalSubs
          this.steamFriends = responses[8].data.data.totalSubs
          this.telegram = responses[9].data.data.totalSubs
        }),
      )
      .catch(errs => {
        this.loading = false
        // eslint-disable-next-line no-console
        console.error(errs)
      })
  },
}
</script>

<style lang="css" scoped>
.col-container {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: stretch;
  align-content: center;
}

.row-container {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: stretch;
  align-content: stretch;
}

@media screen and (max-width: 760px) {
  .row-container {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: stretch;
    align-content: center;
  }
}

a {
  text-decoration: none;
}

#substats-footer {
  color: #666666;
  text-align: left;
  margin: 60px 0 0 0;
}
</style>
