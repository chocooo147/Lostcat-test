<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>谁家的小毛咪 - 状态机原型</title>
  <style>
    :root{--line:#111;--bg:#fff;--pink:#ffd9e8}
    *{box-sizing:border-box} body{margin:0;font-family:"PingFang SC","Microsoft YaHei",sans-serif;background:#f6f6f6;color:#111}
    .wrap{min-height:100vh;display:grid;grid-template-columns:1fr 320px;gap:16px;padding:16px}
    .stage{display:flex;align-items:center;justify-content:center}
    .phone{width:min(420px,92vw);height:min(820px,92vh);background:var(--bg);border:4px solid var(--line);border-radius:30px;padding:18px;display:flex;flex-direction:column;gap:14px;position:relative}
    .cat{height:240px;border:3px solid var(--line);border-radius:24px;display:flex;align-items:center;justify-content:center;background:repeating-linear-gradient(-45deg,#fff,#fff 8px,#f2f2f2 8px,#f2f2f2 16px);font-size:20px}
    .title{font-size:24px;font-weight:700;line-height:1.35;text-align:center;min-height:70px}
    .opts{display:flex;flex-direction:column;gap:10px}
    button{border:3px solid var(--line);background:#fff;border-radius:999px;padding:12px 14px;font-size:16px;cursor:pointer}
    button.invalid{opacity:.55}
    .toolbar{margin-top:auto;display:flex;gap:8px}
    .toolbar button{flex:1;font-size:14px}
    .panel{background:#fff;border:3px solid #111;border-radius:18px;padding:12px;white-space:pre-wrap;word-break:break-word}
    .modal-mask{position:absolute;inset:0;background:rgba(0,0,0,.3);display:flex;align-items:center;justify-content:center;padding:18px}
    .modal{width:100%;background:#fff;border:3px solid #111;border-radius:24px;padding:16px;display:flex;flex-direction:column;gap:10px;align-items:center;text-align:center}
    .modal.success{outline:6px solid var(--pink)}
    .icon{width:58px;height:58px;border:2px dashed #111;border-radius:12px;display:grid;place-items:center}
    @media (max-width: 980px){.wrap{grid-template-columns:1fr}.panel{order:2}}
  </style>
</head>
<body>
<div class="wrap">
  <div class="stage"><div class="phone" id="app"></div></div>
  <div class="panel">
    <h3>调试面板</h3>
    <div id="debug"></div>
  </div>
</div>
<script>
const N=(id,parentId,nodeType,text,isClickable=true,triggerFeedback={},nextId='',assetNeeds=[])=>({id,parentId,nodeType,text,isClickable,triggerFeedback,nextId,assetNeeds});
const nodes=[
N('SCENE_001','ROOT_000','SCENE','这是谁家的小毛咪在路边？',false),
N('HOME_TOUCH_ENTRY_001','SCENE_001','OPTION_VALID','咪咪咪咪你一个小毛咪在这里',true,{},'TOUCH_000'),
N('HOME_FOOD_ENTRY_002','SCENE_001','OPTION_VALID','咪咪 姐姐这里有好吃的',true,{},'FOOD_000'),
N('HOME_ANGRY_ENTRY_003','SCENE_001','OPTION_VALID','咦 这个小毛咪看起来在生气',true,{},'ANGRY_000'),
N('TOUCH_000','HOME_TOUCH_ENTRY_001','SCENE','咪咪咪咪你一个小毛咪在这里',false),
N('TOUCH_HEAD_100','TOUCH_000','PROMPT','给姐姐摸摸毛脑壳',false),N('TOUCH_HEAD_YES_101','TOUCH_HEAD_100','OPTION_VALID','给',true,{type:'touch-success',sound:'声音素材1'},'TOUCH_HEAD_MODAL_101M'),N('TOUCH_HEAD_NO_102','TOUCH_HEAD_100','OPTION_INVALID','不给',false,{type:'fail'}),
N('TOUCH_HEAD_MODAL_101M','TOUCH_HEAD_YES_101','RESULT_MODAL','被亲了，小毛咪被强制爱啦',false),
N('TOUCH_HAND_200','TOUCH_000','PROMPT','给姐姐摸摸小毛手',false),N('TOUCH_HAND_YES_201','TOUCH_HAND_200','OPTION_VALID','给',true,{type:'touch-success',sound:'声音素材2'},'TOUCH_HAND_MODAL_201M'),N('TOUCH_HAND_NO_202','TOUCH_HAND_200','OPTION_INVALID','不给',false,{type:'fail'}),
N('TOUCH_HAND_MODAL_201M','TOUCH_HAND_YES_201','RESULT_MODAL','被亲了，小毛咪被强制爱啦',false),
N('TOUCH_BELLY_300','TOUCH_000','PROMPT','给姐姐摸摸毛肚肚',false),N('TOUCH_BELLY_YES_301','TOUCH_BELLY_300','OPTION_VALID','给',true,{type:'touch-success',sound:'声音素材3'},'TOUCH_BELLY_MODAL_301M'),N('TOUCH_BELLY_NO_302','TOUCH_BELLY_300','OPTION_INVALID','不给',false,{type:'fail'}),
N('TOUCH_BELLY_MODAL_301M','TOUCH_BELLY_YES_301','RESULT_MODAL','被亲了，小毛咪被强制爱啦',false),
N('FOOD_000','HOME_FOOD_ENTRY_002','SCENE','咪咪 姐姐这里有好吃的',false),
N('HOTPOT_100','FOOD_000','PROMPT','想吃火锅么',false),N('HOTPOT_MEAT_101','HOTPOT_100','OPTION_VALID','好吃的肉肉火锅（吆喝）',true,{type:'food-success',icon:'🍖'},'HOTPOT_MEAT_MODAL_101M'),N('HOTPOT_CHICKEN_102','HOTPOT_100','OPTION_VALID','好吃的烧鸡公火锅（吆喝）',true,{type:'food-success',icon:'🍗'},'HOTPOT_CHICKEN_MODAL_102M'),N('HOTPOT_STARE_103','HOTPOT_100','OPTION_VALID','盯（不理人）',true,{type:'feedback',text:'乖咪！啾咪啾咪！'}),N('HOTPOT_HMPH_104','HOTPOT_100','OPTION_INVALID','哼！',false,{type:'fail'}),
N('HOTPOT_MEAT_MODAL_101M','HOTPOT_MEAT_101','RESULT_MODAL','耶斯！小毛咪不生气啦！',false),N('HOTPOT_CHICKEN_MODAL_102M','HOTPOT_CHICKEN_102','RESULT_MODAL','耶斯！小毛咪不生气啦！',false),
N('DRINK_200','FOOD_000','PROMPT','想喝奶茶么',false),N('DRINK_JUICE_201','DRINK_200','OPTION_VALID','韩国财阀果汁冰',true,{type:'food-success',icon:'🍊'},'DRINK_JUICE_MODAL_201M'),N('DRINK_LEMON_202','DRINK_200','OPTION_VALID','柠檬茶',true,{type:'food-success',icon:'🍋'},'DRINK_LEMON_MODAL_202M'),N('DRINK_STARE_203','DRINK_200','OPTION_VALID','盯（不理人）',true,{type:'feedback',text:'好可爱呀！我抱抱！'}),N('DRINK_HMPH_204','DRINK_200','OPTION_INVALID','哼！',false,{type:'fail'}),
N('DRINK_JUICE_MODAL_201M','DRINK_JUICE_201','RESULT_MODAL','耶斯！小毛咪不生气啦！',false),N('DRINK_LEMON_MODAL_202M','DRINK_LEMON_202','RESULT_MODAL','耶斯！小毛咪不生气啦！',false),
N('SWEET_300','FOOD_000','PROMPT','想吃甜甜的么',false),N('SWEET_TOFU_301','SWEET_300','OPTION_VALID','要姐姐请吃臭豆腐',true,{type:'food-success',icon:'🧊'},'SWEET_TOFU_MODAL_301M'),N('SWEET_ROLL_302','SWEET_300','OPTION_VALID','要姐姐带春卷来',true,{type:'food-success',icon:'🥟'},'SWEET_ROLL_MODAL_302M'),N('SWEET_STARE_303','SWEET_300','OPTION_VALID','盯（不理人）',true,{type:'feedback',text:'好翘的屁股呀，揉揉揉！'}),N('SWEET_HMPH_304','SWEET_300','OPTION_INVALID','哼！',false,{type:'fail'}),
N('SWEET_TOFU_MODAL_301M','SWEET_TOFU_301','RESULT_MODAL','耶斯！小毛咪不生气啦！',false),N('SWEET_ROLL_MODAL_302M','SWEET_ROLL_302','RESULT_MODAL','耶斯！小毛咪不生气啦！',false),
N('ANGRY_000','HOME_ANGRY_ENTRY_003','SCENE','咦 这个小毛咪看起来在生气',false),N('ANGRY_HUM_100','ANGRY_000','PROMPT','哼~',false),N('HMPH_000','ANGRY_000','SCENE','哼！',false),N('BAG_000','ANGRY_000','SCENE','哼。',false),
N('ANGRY_HEIHEI_110','ANGRY_HUM_100','AUDIO_OPTION','嘿嘿（舒服的声音）',true,{type:'audio',sound:'SND_COMFY_HEIHEI'}),N('ANGRY_XIXI_120','ANGRY_HUM_100','AUDIO_OPTION','嘻嘻（得意的声音）',true,{type:'audio',sound:'SND_PROUD_XIXI'}),N('ANGRY_JIEJIE_130','ANGRY_HUM_100','AUDIO_OPTION','桀桀（反派的声音）',true,{type:'audio',sound:'SND_VILLAIN_JIEJIE'}),
N('HMPH_100','HMPH_000','PROMPT','哼哼！',false),N('HMPH_TOUCH_YES_101','HMPH_100','OPTION_VALID','原来是要摸摸',true,{type:'feedback',text:'摸摸我的小咪'}),N('HMPH_TOUCH_NO_102','HMPH_100','OPTION_INVALID','不要',false,{type:'fail'}),
N('HMPH_200','HMPH_000','PROMPT','哼哼哼！',false),N('HMPH_HUG_YES_201','HMPH_200','OPTION_VALID','原来是要抱抱',true,{type:'feedback',text:'原来是要抱抱'}),N('HMPH_HUG_NO_202','HMPH_200','OPTION_INVALID','不要',false,{type:'fail'}),
N('HMPH_300','HMPH_000','PROMPT','哼哼哼哼！',false),N('HMPH_KISS_YES_301','HMPH_300','OPTION_VALID','原来是要亲亲',true,{type:'feedback',text:'原来是要亲亲'}),N('HMPH_KISS_NO_302','HMPH_300','OPTION_INVALID','不要',false,{type:'fail'}),
N('BAG_PINK_101','BAG_000','OPTION_VALID','粉色麻袋',true,{type:'feedback',text:'被亲亲抱抱揉揉'}),N('BAG_BLUE_102','BAG_000','OPTION_VALID','蓝色麻袋',true,{type:'feedback',text:'阿偶 被强制爱了'}),N('BAG_PURPLE_103','BAG_000','OPTION_VALID','紫色麻袋',true,{type:'feedback',text:'被喂了好吃的呀'})
];
const map=Object.fromEntries(nodes.map(n=>[n.id,n]));
let currentId='SCENE_001', navStack=[], lastFeedback='none', modal=null;

function childrenOf(id){return nodes.filter(n=>n.parentId===id)}
function to(id){ if(!map[id]) return render(); if(currentId) navStack.push(currentId); currentId=id; render(); }
function back(){ if(!navStack.length) return; currentId=navStack.pop(); render(); }
function home(){ currentId='SCENE_001'; navStack=[]; modal=null; render(); }

function tap(node){
  if(node.nodeType==='OPTION_INVALID' || node.isClickable===false){
    lastFeedback='invalidTap';
    modal={type:'fail',title:'可恶！',text:'哎呀！被亲亲了！',button:'重选一次吧'};
    return render();
  }
  const fb=node.triggerFeedback||{};
  lastFeedback=fb.type||'next';
  if(fb.type==='touch-success') modal={type:'touch-success',text:'被亲了，小毛咪被强制爱啦',sound:fb.sound};
  else if(fb.type==='food-success') modal={type:'food-success',title:'耶斯！小毛咪不生气啦！',icon:fb.icon};
  else if(fb.type==='feedback') modal={type:'feedback',text:fb.text};
  else if(fb.type==='audio') modal={type:'audio',text:`正在播放：${fb.sound}`};
  if(node.nextId) to(node.nextId); else render();
}

function modalHtml(){
  if(!modal) return '';
  if(modal.type==='fail') return `<div class="modal-mask"><div class="modal"><h3>${modal.title}</h3><p>${modal.text}</p><button onclick="closeModal()">${modal.button}</button></div></div>`;
  if(modal.type==='touch-success') return `<div class="modal-mask"><div class="modal"><p>${modal.text}</p><button onclick="playSound('${modal.sound}')">🔊 喇叭按钮</button><button onclick="closeModal()">关闭</button></div></div>`;
  if(modal.type==='food-success') return `<div class="modal-mask"><div class="modal success"><div class="icon">${modal.icon||'icon'}</div><h3>${modal.title}</h3><button onclick="share()">截图分享给姐姐</button><button onclick="closeModal()">关闭</button></div></div>`;
  return `<div class="modal-mask"><div class="modal"><p>${modal.text}</p><button onclick="closeModal()">关闭</button></div></div>`;
}
function closeModal(){ modal=null; render(); }
function playSound(s){ lastFeedback='playAudio'; alert('正在播放：'+s); }
function share(){ lastFeedback='share'; alert('分享海报功能待接入'); }

function render(){
  const node=map[currentId];
  const opts=childrenOf(currentId);
  const app=document.getElementById('app');
  app.innerHTML=`
    <div class="cat">🐱 小毛咪占位图</div>
    <div class="title">${node?.text||''}</div>
    <div class="opts">${opts.map(o=>`<button class="${o.nodeType==='OPTION_INVALID'?'invalid':''}" data-id="${o.id}">${o.text}</button>`).join('')}</div>
    <div class="toolbar"><button id="backBtn">返回上一步</button><button id="homeBtn">回到首页</button></div>
    ${modalHtml()}
  `;
  app.querySelectorAll('button[data-id]').forEach(b=>b.onclick=()=>tap(map[b.dataset.id]));
  document.getElementById('backBtn').onclick=back;
  document.getElementById('homeBtn').onclick=home;
  document.getElementById('debug').textContent=`currentId: ${currentId}\nparentId: ${node?.parentId}\nnodeType: ${node?.nodeType}\nnavStack: ${JSON.stringify(navStack)}\nlastFeedback: ${lastFeedback}`;
}
render();
</script>
</body>
</html>
