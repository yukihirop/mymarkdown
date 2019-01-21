<template>
  <div id="home">
    <div class="firstView">
      <img class="logo" src="../assets/top_logo.png" alt="MyMarkdown" title="MyMarkdown">
      <p class="copy">{{ msg }}</p>
      <p class="subcopy">最小限の機能に絞ったマークダウンエディタ</p>
      <button class="login" @click="googleLogin">Googleアカウントで5秒で登録</button>
      <div class="notice">
        * 登録の際には
        <router-link :to="{ name: 'terms' }">利用規約とプライバシーポリシー</router-link>に同意したものとします。
      </div>
    </div>
    <div class="about">
      <img class="sample" src="../assets/sample.png" alt="利用例" title="利用例">
      <p>余計な機能がないのでさくっとメモを取るだけに集中できます</p>
      <p>マークダウン記法でかけて、リアルタイムにプレビュー</p>
      <p>ショートカットキーにより、キーボードだけで操作可能</p>
      <div class="shortcuts">
        <p>"Control + s"(Macの場合は"Command + s")ですぐに保存</p>
        <p>"Alt + ↑↓"(Macの場合は"Option + ↑↓")でメモの切り替え</p>
        <p>最後のメモ選択時に"Alt + ↓"(Macの場合は"Option + ↓")でメモの追加</p>
        <p>"Control + Backspace"(Macの場合は"Command + delete")でメモの削除</p>
      </div>
      <p>さぁあなたもすぐに始めてみましょう！</p>
      <button class="login" @click="googleLogin">
        Googleアカウントで5秒で登録
      </button>
    </div>
    <div class="footer">
      <router-link :to="{ name: 'terms' }">利用規約とプライバシーポリシー</router-link>
      <div class="providedby">
        Provived by
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  data(){
    return {
      msg: "かつてないほどのシンプルなメモ帳",
      termsUrl: '/terms'
    }
  },
  methods: {
    googleLogin: function(){
      firebase
      .auth()
      .signInWithRedirect(new firebase.auth.GoogleAuthProvider());
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  padding-top: 100px;
}
.logo {
  height: 100px;
  margin-bottom: 70px;
}
.copy {
  font-size: 50px;
  font-weight: bold;
  margin-bottom: 50px;
}
.subcopy {
  font-size: 30px;
  margin-bottom: 50px;
}
.login {
  font-size: 20px;
  padding: 5px 20px;
  i {
    margin-right: 5px;
  }
}
.notice {
  margin-top: 20px;
}
.about {
  width: 800px;
  margin: 80px auto;
  .sample {
    border-radius: 5px;
    border: 1px solid #eee;
    margin-bottom: 40px;
  }
  p{
    font-size: 20px;
    margin:20px 0;
  }
  .login {
    margin-top: 40px;
  }
}
.shortcuts {
  p {
    font-size: 15px;
    margin: 10px 0;
  }
  background-color: #eee;
  border-radius: 5px;
  padding: 10px 0;
  margin-bottom: 40px;
}
.footer {
  width: 800px;
  margin: 0 auto;
  border-top: 1px solid #ddd;
  padding: 5px 0;
  .providedby {
    margin-top: 10px;
  }
}
</style>