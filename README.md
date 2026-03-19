<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>全网资源分享</title>
<style>
*{margin:0;padding:0;box-sizing:border-box}
body{
  font-family: "PingFang SC", "Microsoft YaHei", sans-serif;
  background: linear-gradient(135deg, #fff5fa 0%, #eef5ff 100%);
  min-height: 100vh;
  padding: 15px;
  padding-top: 100px;
  padding-bottom: 50px;
}

.fixed-left, .fixed-right {
  position: fixed;
  top: 12px;
  z-index: 999;
  width: 70px;
  height: 70px;
  background: #fff;
  border-radius: 14px;
  padding: 4px;
  box-shadow: 0 6px 16px rgba(0,0,0,0.1);
  cursor: pointer;
}
.fixed-left  { left: 12px; }
.fixed-right { right: 12px; }
.fixed-left img, .fixed-right img {
  width: 100%;
  height: 100%;
  border-radius: 10px;
  object-fit: cover;
}

.img-modal {
  position: fixed;
  top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(0,0,0,0.8);
  display: flex; align-items: center; justify-content: center;
  z-index: 9999;
  display: none;
  padding: 20px;
}
.img-modal.show { display: flex; }
.img-modal img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 12px;
  box-shadow: 0 0 20px rgba(255,255,255,0.3);
}

.search-box {
  background: #fff;
  border-radius: 18px;
  padding: 12px 16px;
  margin-bottom: 20px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}
.search-input {
  width: 100%;
  border: none; outline: none;
  background: #f6f9ff;
  padding: 12px 16px;
  border-radius: 12px;
  font-size: 14px;
  color: #333;
}
.search-input::placeholder {
  color: #b0b8cc;
}

.head {
  background: #fff;
  border-radius: 20px;
  padding: 20px;
  text-align: center;
  margin-bottom: 20px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}
h1 {
  font-size: 22px;
  background: linear-gradient(90deg, #83aaff, #ff96cc);
  -webkit-background-clip: text;
  color: transparent;
}
.head p {
  color: #999;
  font-size: 13px;
  margin-top: 4px;
}

.faq {
  background: #fff;
  border-radius: 18px;
  margin-bottom: 12px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0,0,0,0.04);
}
.faq-title {
  width: 100%;
  padding: 18px 20px;
  background: #fff;
  border: none; outline: none;
  text-align: left;
  font-size: 15px;
  font-weight: 500;
  color: #333;
  cursor: pointer;
  position: relative;
}
.faq-title::after {
  content: "+";
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 18px;
  color: #83aaff;
}
.faq.active .faq-title::after { content: "−"; color: #ff96cc; }

.faq-content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s ease;
  padding: 0 20px;
  font-size: 14px;
  line-height: 1.8;
  color: #555;
}
.faq.active .faq-content {
  max-height: 5000px;
  padding: 15px 20px 25px;
}

a {
  display: inline-block;
  background: #ff96cc;
  color: #fff;
  padding: 7px 13px;
  border-radius: 10px;
  text-decoration: none;
  margin: 5px 5px 5px 0;
  font-size: 13px;
  transition: all 0.2s;
}
a:hover {
  transform: scale(1.05);
  box-shadow: 0 3px 8px rgba(255,150,204,0.2);
}
a.blue { 
  background: #83aaff; 
}
a.blue:hover {
  box-shadow: 0 3px 8px rgba(131,170,255,0.2);
}

p { margin: 10px 0; }

.week {
  color: #ff96cc;
  font-weight: bold;
  margin-top: 15px;
  margin-bottom: 8px;
  font-size: 15px;
}

.highlight {
  background: #fff5ba;
  color: #d97706;
  padding: 2px 5px;
  border-radius: 4px;
  font-weight: 500;
}

.copyright {
  text-align: center;
  font-size: 12px;
  color: #999;
  margin-top: 30px;
  line-height: 1.5;
}
</style>
</head>

<body>

<div class="fixed-left" onclick="showImg('https://ftp.mioz.cn/test/2026/03/19/1773912806.JPG')">
  <img src="https://ftp.mioz.cn/test/2026/03/19/1773912806.JPG" alt="扫码备注拉群">
</div>

<div class="fixed-right" onclick="showImg('https://ftp.mioz.cn/test/2026/03/19/1773912894.JPG')">
  <img src="https://ftp.mioz.cn/test/2026/03/19/1773912894.JPG" alt="赞赏码">
</div>

<div class="img-modal" id="imgModal" onclick="closeImg()">
  <img id="bigImg" src="">
</div>

<div class="head">
  <h1>全网资源分享</h1>
  <p>点击板块展开 / 收起 | 搜索框可直接搜剧名/综艺名</p>
</div>

<div class="search-box">
  <input type="text" class="search-input" id="searchInput" placeholder="🔍 例：大侦探、剑来、后来的我们...">
</div>

<div class="faq">
  <div class="faq-title">🧧 每日优惠合集</div>
  <div class="faq-content">
    <p>优惠链接需复制到浏览器打开</p>
  </div>
</div>

<div class="faq">
  <div class="faq-title">📁 其他分类资源合集</div>
  <div class="faq-content">
    <p>动画片完结合集</p><a class="blue" href="https://pan.quark.cn/s/1256f2c00e65" target="_blank">夸克</a>
    <p>欧美剧完结合集</p><a class="blue" href="https://pan.quark.cn/s/e4357671b0ac" target="_blank">夸克</a>
    <p>韩剧综完结合集</p><a class="blue" href="https://pan.quark.cn/s/c5f34295de9c" target="_blank">夸克</a>
    <p>学习资料合集</p><a class="blue" href="https://pan.quark.cn/s/20a8ee20dd01" target="_blank">夸克</a>
    <p>全网恐怖片电影合集</p><a class="blue" href="https://pan.quark.cn/s/3dcc5d2c9eb0" target="_blank">夸克</a>
    <p>健身塑形合集</p><a class="blue" href="https://pan.quark.cn/s/bbac5a33e4b2" target="_blank">夸克</a>
    <p>纪录片合集</p><a class="blue" href="https://pan.quark.cn/s/94f0d7db7a83" target="_blank">夸克</a>
    <p>全球电影票房top10</p><a class="blue" href="https://pan.quark.cn/s/eb4c994a3bad" target="_blank">夸克</a>
    <p>编程开发自媒体运营合集</p><a class="blue" href="https://pan.quark.cn/s/179debf6d11f" target="_blank">夸克</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">📺 电视剧</div>
  <div class="faq-content">
    <p class="week">❤️每日更新</p>
    <p>正义女神 佘诗曼</p>
    <a class="blue" href="https://pan.quark.cn/s/a4194f83b53f" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1gaq_bb8cXEsvMWmjHJDzwQ?pwd=2580" target="_blank">度</a>

    <p>你好1983 周也 翟潇闻</p>
    <a class="blue" href="https://pan.quark.cn/s/54c145979dc3" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1l0uGgu8rj7PdLdNml9Kmzw?pwd=2580" target="_blank">度</a>

    <p>逐玉 田曦薇 张凌赫</p>
    <a class="blue" href="https://pan.quark.cn/s/22e9dbadcdec" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1ISdKKH1EPClScrCxmOsyVw?pwd=2580" target="_blank">度</a>

    <p>我的山与海 谭松韵 董晴 奚望 高至霆</p>
    <a class="blue" href="https://pan.quark.cn/s/6b9d1b704476" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1QG1JWwHAK7TrC4X5G-BE4Q?pwd=2580" target="_blank">度</a>

    <p>她的盛宴 马思纯 宁理 袁姗姗 翟子路</p>
    <a class="blue" href="https://pan.quark.cn/s/007dc3b6e73b" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1zTdn1wIM21BcXD-AT1gukA?pwd=2580" target="_blank">度</a>

    <p>好好的时光</p>
    <a class="blue" href="https://pan.quark.cn/s/b09f41c2f8cd" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/11fFcccV_uWOIz98mURC-Gw?pwd=2580" target="_blank">度</a>

    <p>隐身的名字 倪妮 闫妮</p>
    <a class="blue" href="https://pan.quark.cn/s/2f95cf5a05a6" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1u_mS9A3qqkcPnJzzTL3dLQ?pwd=2580" target="_blank">度</a>

    <p class="week">❤️周日 周一</p>
    <p>韩剧《未婚男女的效率恋爱》第05集</p>
    <a class="blue" href="https://pan.quark.cn/s/d0d6ba73e0f2" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/14jPc-gPElN38tUfizkXTpg?pwd=2580" target="_blank">度</a>

    <p class="week">❤️周五</p>
    <p>初三的六一儿童节</p>
    <a class="blue" href="https://pan.quark.cn/s/35b28e80f874" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1RhPBT_bEAeObhnVj6hojFw?pwd=2580" target="_blank">度</a>

    <p class="week">❤️周六、周日</p>
    <p>韩剧 在你灿烂的季节 李圣经 蔡钟协</p>
    <a class="blue" href="https://pan.quark.cn/s/d09dce765419" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/19H6XLTei4T1Tmx5iQx8HCA?pwd=2580" target="_blank">度</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">🎙️ 综艺</div>
  <div class="faq-content">
    <p class="week">🔥周二</p>
    <p>名侦探学院第九季</p><a class="blue" href="https://pan.quark.cn/s/703ff863d2a6" target="_blank">夸</a>
    <p>我家那小子</p>
    <a class="blue" href="https://pan.quark.cn/s/18f99312eeb0" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1DSVfcKnvrG-xDo4bq1K64g?pwd=2580" target="_blank">度</a>

    <p class="week">🔥周三</p>
    <p>大侦探第十一季</p>
    <a class="blue" href="https://pan.quark.cn/s/d769fed30bdf" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1o0njrx-dcumI2__qr5s3HA?pwd=2580" target="_blank">度</a>
    <p>开始捉迷藏第二季</p><a class="blue" href="https://pan.quark.cn/s/a4fe2d07adee" target="_blank">夸</a>

    <p class="week">🔥周五</p>
    <p>今夜喜友秀</p><a class="blue" href="https://pan.quark.cn/s/5949dcc9c9e5" target="_blank">夸</a>
    <p>亲爱的客栈2026 补</p><a class="blue" href="https://pan.quark.cn/s/0c544beb6182" target="_blank">夸</a>
    <p>主咖和Ta的朋友们</p><a href="https://pan.baidu.com/s/1xSvf6y559nv51D59oKzMsg?pwd=2580" target="_blank">度</a>

    <p class="week">🔥周六、周日</p>
    <p>宇宙闪烁请注意</p>
    <a class="blue" href="https://pan.quark.cn/s/ac03b97c4100" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/14NX8yX4MgU6q4D3Aim0BlQ?pwd=2580" target="_blank">度</a>
    <p>你好星期六 20:50</p>
    <a class="blue" href="https://pan.quark.cn/s/68c38fe1b459" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1fu8nLkjPvuFXbzKGRs1phg?pwd=2580" target="_blank">度</a>
    <p>守护解放西 探案季</p>
    <a class="blue" href="https://pan.quark.cn/s/98eff4fb99f5" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1iBfbNqKxBAhKSpDGy2PIgA?pwd=2580" target="_blank">度</a>
    <p>主咖和Ta的朋友们</p><a href="https://pan.baidu.com/s/1xSvf6y559nv51D59oKzMsg?pwd=2580" target="_blank">度</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">🎬 动漫</div>
  <div class="faq-content">
    <p class="week">🌀周三</p>
    <p>剑来 第二季附一</p>
    <a class="blue" href="https://pan.quark.cn/s/b0eddbb82fa1" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1Cnbq3IFM0XMzWMHtrATrdQ?pwd=2580" target="_blank">度</a>

    <p class="week">🌀周五</p>
    <p>一人之下 第六季</p><a class="blue" href="https://pan.quark.cn/s/5c7149ee0f6f" target="_blank">夸</a>

    <p class="week">🌀周日</p>
    <p>牧神记</p>
    <a class="blue" href="https://pan.quark.cn/s/379e7b1b4baa" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1ezbqLm9daiVhBEeySgFL7w?pwd=2580" target="_blank">度</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">🎥 电影</div>
  <div class="faq-content">
    <p>电影🎬韩国爱情《后来的我们》2025 中字</p>
    <p>主演: 具教焕 / 文佳煐 / 姜末琴</p>
    <a class="blue" href="https://pan.quark.cn/s/8d32bcfdcb17" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1_hyW3J0zO1eSSL4hgjFn6Q?pwd=2580" target="_blank">度</a>

    <p>电影🎬夜王 粤语 ct1080P</p>
    <a class="blue" href="https://pan.quark.cn/s/620cf1690829" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1SKs19e-NGuJsCDtZzl6c7A?pwd=2580" target="_blank">度</a>

    <p>电影🎬版惊蛰无声[TC】尝鲜</p>
    <p>(易烊千玺/朱一龙/宋佳/雷佳音/杨幂/张译/刘诗诗/刘耀文)</p>
    <a class="blue" href="https://pan.quark.cn/s/0fc2f34527ca" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1jgBqxBAXmsEaQJuWsSOwUw?pwd=2580" target="_blank">度</a>

    <p>🎬飞驰人生1-3</p>
    <a class="blue" href="https://pan.quark.cn/s/c456a0ca06e5" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1g1r1S21n0qIN1sjLy6mnPA?pwd=2580" target="_blank">度</a>

    <p>🎬熊出没 年年有熊 附往年大电影合集</p>
    <a class="blue" href="https://pan.quark.cn/s/a107ccdd1bb4" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1ZWv8lzwTBfuHCew73U7-jg?pwd=2580" target="_blank">度</a>

    <p>🎬2025豆瓣年度电影榜单</p>
    <a class="blue" href="https://pan.quark.cn/s/ef5575ea5113" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1IESqF5tLSo9aKUGOJXGiug?pwd=2580" target="_blank">度</a>

    <p>🎬熊猫计划之部落奇遇记（TC尝鲜版）【成龙/马丽】</p>
    <a class="blue" href="https://pan.quark.cn/s/a43bbda35e34" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/181rFlRPNXzsEP1eUxxIc2Q?pwd=2580" target="_blank">度</a>

    <p>电影🎬镖人 吴京 谢霆锋 于适 陈丽君 孙艺洲 此沙 TC版 1080</p>
    <a class="blue" href="https://pan.quark.cn/s/dc4f97403aa1" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1fThq_tnmr7wuk9bS3V7r_w?pwd=2580" target="_blank">度</a>

    <p>得闲谨制（4K）【肖战/彭昱畅/周依然】【剧情/战争】</p>
    <a class="blue" href="https://pan.quark.cn/s/76ac738d138f" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1C7cILniJhS_SgmdnlH1fxw?pwd=2580" target="_blank">度</a>

    <p>爆水管（4K）【彭于晏/艾伦/周游】【喜剧/犯罪】</p>
    <a href="https://pan.baidu.com/s/1xZyzNk6-Jx9UIB4Zxuu8bg?pwd=2580" target="_blank">度</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">📚 每日小说</div>
  <div class="faq-content">
    <p>📚【小说日更】</p>
    <a class="blue" href="https://pan.quark.cn/s/8c49086f89bb" target="_blank">夸</a>
    <a href="https://pan.baidu.com/s/1Ym-Jiero4qiGP6NxwRf5rQ?pwd=2580" target="_blank">度</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">💣 每日短剧</div>
  <div class="faq-content">
    <p>💣短剧合集</p>
    <a class="blue" href="https://pan.quark.cn/s/b519ae7b914c" target="_blank">夸</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">🎮 软件游戏</div>
  <div class="faq-content">
    <p>软件/游戏合集</p>
    <a class="blue" href="https://pan.quark.cn/s/8bddcb98fb8e" target="_blank">夸</a>
  </div>
</div>

<div class="faq">
  <div class="faq-title">🎬 完结剧综合集</div>
  <div class="faq-content">
    <p>待更新</p>
  </div>
</div>

<div class="copyright">
  本站所有素材均来自于互联网，版权属原著所有<br>
  如有需要请购买正版。如有侵权，请联系我们立即删除。
</div>

<script>
document.querySelectorAll('.faq-title').forEach(title => {
  title.addEventListener('click', function() {
    const faq = this.parentElement;
    faq.classList.toggle('active');
  });
});

function showImg(url) {
  const modal = document.getElementById('imgModal');
  const bigImg = document.getElementById('bigImg');
  bigImg.src = url;
  modal.classList.add('show');
}

function closeImg() {
  document.getElementById('imgModal').classList.remove('show');
}
</script>

</body>
</html>
