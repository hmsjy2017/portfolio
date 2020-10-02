<template>
  <div class="container">
    <img id="avatar" alt="avatar" src="https://camo.githubusercontent.com/c8b70970f3c08bd95ad0c0771fe7021d06fba6e4/68747470733a2f2f69616d736a792e6f73732d636e2d7368616e676861692e616c6979756e63732e636f6d2f69636f6e2e6a7067" />
    <h1>Tony</h1>
    <h2>👨‍🎨 👨‍💻 🙋‍♂️</h2>

    <p>学生 / 树莓派爱好者</p>

    <hr id="top-hr" />
    <h3>🎉 Where to find me:</h3>
    <div id="card-container">
      <Card
        msg="少数派 sspai"
        backgroundColor="#ca2c2a"
        description="✏️ 主要输出战场！"
        textColor="#FFFFFF"
        icon="sspai.png"
        link="https://sspai.com/u/spencerwoo/posts"
      />
      <Card
        msg="博客 Blog"
        backgroundColor="#0083c0"
        description="📒 从头开始（咕咕咕）"
        textColor="#FFFFFF"
        icon="netlify.png"
        link="https://blog.spencerwoo.com"
      />
      <Card
        msg="GitHub"
        backgroundColor="#24292E"
        description="📦 我做过的项目都在这里"
        textColor="#FFFFFF"
        icon="github.png"
        link="https://github.com/hmsjy2017"
      />
    </div>



      </div>

      <hr />

      </a>
    </div>
  </div>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
  components: {
    Card,
  },
}
</script>
