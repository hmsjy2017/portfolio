<template>
  <div class="container">
    <h1>👓</h1>
    <h1>About</h1>
    <p>这人是谁啊，这么牛逼哄哄的？</p>

    <hr id="top-hr" />
    <div class="article">
      <p>
        某无聊中学生。
      </p>

      <h2>我的项目</h2>
      <p>
        我所做过的项目几乎都开源于
        <a href="https://github.com/spencerwooo">GitHub</a> 上面，欢迎大家 Star + Fork，笔芯 (✿◡‿◡)
      </p>

      <GitHubCard
        title="Tony’s Blog"
        link="https://github.com/hmsjy2017/hmsjy2017.github.io"
        :info="dowwwInfo"
        :loading="loading"
      >
        <p>
          我的博客
        </p
      </GitHubCard>

      <GitHubCard
        title="📈 Substats：快速统计你在各个平台的关注者"
        link="https://github.com/spencerwooo/Substats"
        :info="substatsInfo"
        :loading="loading"
      >
        <p>
          Substats 是一个非常方便易用的请求订阅者、粉丝、关注用户数量 API 服务，支持了包括
          Feedly、GitHub、Twitter、知乎和少数派等 10 余个网站和服务，并用 Cloudflare 全球部署，飞速响应。少数派介绍：<a
            href="https://sspai.com/post/59593"
            >《做一个好看的数据展示「小标签」，在个人网站实时展示你的粉丝数》</a
          >
        </p>
      </GitHubCard>

      <GitHubCard
        title="🥇 The Fully Anonymous Teaching Evaluation System"
        link="https://github.com/SecureCats/Evaluation_BackEnd"
        :info="fatesInfo"
        :loading="loading"
      >
        <p>
          Secure Cats 团队作品：基于零知识证明和 CL 签名的匿名课程评价系统。这一评教系统参加了「2019
          年大学生信息安全竞赛 —— 作品赛」，荣获国家级二等奖。推荐阅读：
          <a href="https://medium.com/spencerweekly/recap-on-fates-d9d17a6a7827"
            >什么时候「匿名」才是合理的？| 匿名评教平台复盘</a
          >
        </p>
      </GitHubCard>

      <GitHubCard
        title="🎫 少数派作者名片 | 一个 JSBox 小组件"
        link="https://github.com/spencerwooo/jsbox-sspai-namecard"
        :info="sspaiCardInfo"
        :loading="loading"
      >
        <p>
          适合新版本少数派的作者名片，搭建在 JSBox 上。推荐阅读：
          <a href="https://sspai.com/post/55562">新版少数派网站的作者成就墙好好看啊，于是我用它写了一个 JSBox 小插件</a>
        </p>
      </GitHubCard>

      <GitHubCard
        title="🎃 我的 dotfiles"
        link="https://github.com/spencerwooo/dotfiles"
        :info="dotfilesInfo"
        :loading="loading"
      >
        <p>我的各种配置清单。从终端到 Vim，从 macOS 到 Windows，应有尽有。</p>
      </GitHubCard>

      <h2>我的设备</h2>
      <ul>
        <li>
          主力台式机：Intel® NUC Kit NUC8I5BEK
          <ul>
            <li>
              配置清单：
              <ul>
                <li>CPU: Intel® Core™ i5-8295U</li>
                <li>RAM: ADATA 16GB (8GB×2) DDR4 2666MHz</li>
                <li>M.2 SSD: SAMSUNG PM981 M.2 NVME 256GB</li>
              </ul>
            </li>
            <li>
              介绍：
              <a href="https://sspai.com/post/54788">性能强劲的「迷你台式机」，Intel NUC 一周使用体验</a>
            </li>
          </ul>
        </li>
        <li>
          ThinkPad X1 Yoga (1st Gen)：
          <ul>
            <li>
              介绍：
              <a href="https://sspai.com/post/45742">迁移到 Windows 后，我如何找回熟悉的 macOS 体验</a>
            </li>
          </ul>
        </li>
        <li>12-inch MacBook：观赏性质 > 实用价值</li>
        <li>
          Sony 1000XM3：
          <ul>
            <li>
              介绍：
              <a href="https://sspai.com/post/47794">降噪、音质、续航一网打尽：索尼 1000XM3 降噪耳机体验</a>
            </li>
          </ul>
        </li>
        <li>iPhone XR</li>
        <li>iPad Air 3rd Gen</li>
        <li>Apple Watch Series 3</li>
        <li>AirPods Pro</li>
      </ul>

      <h2>联系我</h2>
      <p>
        欢迎大家直接订阅我的发布，详情请参考：
        <router-link to="/subscribe">Spencer Woo - Subscribe</router-link>
      </p>
      <p>我的联系方式：</p>
      <ul>
        <li>
          📫 邮箱：
          <a href="mailto:spencerwoo98@gmail.com">spencerwoo98#gmail.com</a>
        </li>
        <li>
          ✈ Telegram：
          <a href="https://t.me/SpencerWoo">t.me/SpencerWoo</a>
        </li>
        <li>📍 Beijing Institute of Technology, Beijing, China</li>
      </ul>
    </div>
  </div>
</template>

<script>
import GitHubCard from '@/components/GitHubCard.vue'

export default {
  components: {
    GitHubCard,
  },
  data() {
    return {
      loading: true,
      dowwwInfo: {
        stargazers_count: 0,
        forks_count: 0,
      },
      substatsInfo: {
        stargazers_count: 0,
        forks_count: 0,
      },
      fatesInfo: {
        stargazers_count: 0,
        forks_count: 0,
      },
      sspaiCardInfo: {
        stargazers_count: 0,
        forks_count: 0,
      },
      dotfilesInfo: {
        stargazers_count: 0,
        forks_count: 0,
      },
    }
  },
  mounted() {
    const githubApiUrl = 'https://api.github.com/repos'

    const dowwwAxios = this.axios.get(`${githubApiUrl}/hmsjy2017/hmsjy2017.github.io`)
    const substatsAxios = this.axios.get(`${githubApiUrl}/spencerwooo/Substats`)
    const fatesAxios = this.axios.get(`${githubApiUrl}/SecureCats/Evaluation_BackEnd`)
    const sspaiCardAxios = this.axios.get(`${githubApiUrl}/spencerwooo/jsbox-sspai-namecard`)
    const dotfilesAxios = this.axios.get(`${githubApiUrl}/spencerwooo/dotfiles`)

    this.axios
      .all([dowwwAxios, substatsAxios, fatesAxios, sspaiCardAxios, dotfilesAxios])
      .then(
        this.axios.spread((...resp) => {
          this.loading = false
          this.dowwwInfo = resp[0].data
          this.substatsInfo = resp[1].data
          this.fatesInfo = resp[2].data
          this.sspaiCardInfo = resp[3].data
          this.dotfilesInfo = resp[4].data
        }),
      )
      .catch(err => {
        this.loading = false
        // eslint-disable-next-line no-console
        console.error(err)
      })
  },
}
</script>

<style lang="css" scoped>
h2 {
  font-weight: 700;
  font-size: 20px;
  padding: 10px 0;
}

ul {
  padding-left: 15px;
  line-height: 30px;
  margin: 0;
}

p {
  line-height: 30px;
}
</style>
