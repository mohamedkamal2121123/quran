<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>القرآن الكريم — قارئ سهل</title>
<style>
  :root{--accent:#2e7d32;--bg:#f7f7f7}
  body{font-family: "Segoe UI", Tahoma, Arial, 'Amiri', serif; margin:0; background:var(--bg); color:#111}
  header{background:var(--accent); color:#fff; padding:14px 18px; text-align:center}
  .wrap{max-width:1100px;margin:18px auto;padding:12px}
  .controls{display:flex;gap:10px;flex-wrap:wrap;align-items:center;justify-content:center;margin-bottom:12px}
  select,button{padding:10px;border-radius:8px;border:1px solid #ddd;background:#fff}
  button{background:var(--accent);color:#fff;border:none;cursor:pointer}
  .content{display:flex;gap:14px}
  .left{width:320px;background:#fff;border-radius:8px;padding:12px;box-shadow:0 6px 18px rgba(0,0,0,.06);overflow:auto;max-height:64vh}
  .right{flex:1;background:#fff;border-radius:8px;padding:16px;box-shadow:0 6px 18px rgba(0,0,0,.06);overflow:auto;max-height:64vh}
  .surah-item{padding:8px;border-radius:6px;cursor:pointer;border-bottom:1px solid #f0f0f0;text-align:right}
  .surah-item:hover{background:#f0fff0}
  .surah-item.active{background:#e8f5e9;font-weight:700}
  .surah-image{width:160px;height:160px;border-radius:8px;object-fit:cover;margin:8px auto;display:block}
  audio{width:100%;margin-top:10px}
  .small{font-size:13px;color:#666}
  @media(max-width:900px){.content{flex-direction:column}.left{width:100%;max-height:220px}.right{max-height:50vh}}
</style>
</head>
<body>
<header>
  <h1>📖 برنامج القرآن — استمع لسورة كاملة بدون تقطيع</h1>
</header>
<div class="wrap">
  <div class="controls">
    <label class="small">اختر القارئ:</label>
    <select id="reciterSelect"></select>
    <label class="small">ابحث باسم السورة:</label>
    <input id="searchInput" placeholder="مثال: البقرة أو 2" style="padding:10px;border-radius:8px;border:1px solid #ddd;width:260px" />
    <button id="refreshBtn">إعادة تحميل قائمة السور</button>
  </div>

  <div class="content">
    <aside class="left">
      <div id="surahList"></div>
    </aside>

    <main class="right">
      <div style="text-align:center">
        <img id="surahImage" class="surah-image" src="" alt="صورة السورة" onerror="this.style.display='none'" />
        <div style="margin-top:6px" class="small">السورة: <strong id="currentSurahName">لم يتم الاختيار</strong></div>
        <div class="small" style="margin-top:6px">المصدر: قوائم صوتية من الإنترنت · إذا لم يعمل صوت قارئ معين حاول تغيير القارئ أو جرّب المصادر الاحتياطية.</div>
      </div>

      <div style="margin-top:12px">
        <button id="playBtn" disabled>▶ تشغيل السورة كاملة</button>
        <button id="stopBtn" disabled style="background:#b71c1c">■ إيقاف</button>
      </div>

      <div id="ayahs" style="margin-top:16px;text-align:right"></div>

      <div style="margin-top:12px" id="playerWrap" hidden>
        <div class="small">مشغل الصوت:</div>
        <audio id="audioPlayer" controls></audio>
        <div id="status" class="small" style="margin-top:6px"></div>
      </div>
    </main>
  </div>
</div>

<script>
/*
  فايل HTML كامل — يعمل محليًا.
  مميزات الكود:
  - يحتوي على 114 سورة في القائمة (أسماء عربية).
  - اختيار قارئ له قائمة من مصادر (base URLs) ويجرب الروابط بالترتيب حتى يجد ملف MP3 صالح.
  - كل ملف صوت لسورة مفترض أن يكون ملفًا واحدًا (مقطع كامل) مثل: base + "001.mp3".
  - يظهر نص الآيات من API (api.alquran.cloud) — نص فقط للقراءة.
  ملاحظة: بعض مزوّدي الصوت قد يمنعون التشغيل عبر CORS أو يستخدمون مسارات مختلفة؛ الكود يحاول التبديل بين قواعد URLs احتياطية.
*/

const surahNames = [
  "الفاتحة","البقرة","آل عمران","النساء","المائدة","الأنعام","الأعراف","الأنفال","التوبة","يونس",
  "هود","يوسف","الرعد","إبراهيم","الحجر","النحل","الإسراء","الكهف","مريم","طه",
  "الأنبياء","الحج","المؤمنون","النّور","الفرقان","الشعراء","النمل","القصص","العنكبوت","الروم",
  "لقمان","السجدة","الأحزاب","سبأ","فاطر","يس","الصافات","ص","الزمر","غافر",
  "فصلت","الشورى","الزخرف","الدخان","الجاثية","الأحقاف","محمد","الفتح","الحجرات","ق",
  "الذاريات","الطور","النجم","القمر","الرحمن","الواقعة","الحديد","المجادلة","الحشر","الممتحنة",
  "الصف","الجمعة","المنافقون","التغابن","الطلاق","التحريم","الملك","القلم","الحاقة","المعارج",
  "نوح","الجن","المزّمّل","المدّثر","القيامة","الإنسان","المرسلات","النبأ","النازعات","عبس",
  "التكوير","الإنفطار","المطفّفين","الإنشقاق","البروج","الطارق","الأعلى","الغاشية","الفجر","البلد",
  "الشمس","الليل","الضحى","الشرح","التين","العلق","القدر","البينة","الزلزلة","العاديات",
  "القارعة","التكاثر","العصر","الهمزة","الفيل","قريش","الماعون","الكوثر","الكافرون","النصر",
  "المسد","الإخلاص","الفلق","الناس"
];

// قائمة القرّاء — كل قارئ يملك مصفوفة من قواعد URL (ترتيبات احتياطية)
const reciters = {
  "مشاري العفاسي": [
    "https://server8.mp3quran.net/afs/",
    "https://verses.quran.com/Alafasy/mp3/"
  ],
  "عبد الباسط": [
    "https://server7.mp3quran.net/basit/",
    "https://verses.quran.com/AbdulBaset/Mujawwad/mp3/"
  ],
  "ماهر المعيقلي": [
    "https://server6.mp3quran.net/maher/",
    "https://verses.quran.com/MaherAlMuaiqly/mp3/"
  ],
  "سعود الشريم": [
    "https://server4.mp3quran.net/shuraym/",
    "https://verses.quran.com/Shuraym/mp3/"
  ],
  "سعد الغامدي": [
    "https://server10.mp3quran.net/ghamdi/",
    "https://verses.quran.com/SaadGhamdi/mp3/"
  ]
};

const reciterSelect = document.getElementById('reciterSelect');
const surahListEl = document.getElementById('surahList');
const searchInput = document.getElementById('searchInput');
const refreshBtn = document.getElementById('refreshBtn');
const currentSurahName = document.getElementById('currentSurahName');
const surahImage = document.getElementById('surahImage');
const playBtn = document.getElementById('playBtn');
const stopBtn = document.getElementById('stopBtn');
const playerWrap = document.getElementById('playerWrap');
const audioPlayer = document.getElementById('audioPlayer');
const ayahsDiv = document.getElementById('ayahs');
const statusDiv = document.getElementById('status');

// ملء قائمة القرّاء
function populateReciters(){
  reciterSelect.innerHTML = '';
  for(const name in reciters){
    const opt = document.createElement('option');
    opt.value = name;
    opt.textContent = name;
    reciterSelect.appendChild(opt);
  }
}

// ملء قائمة السور كاملة
function populateSurahList(){
  surahListEl.innerHTML = '';
  surahNames.forEach((name, idx)=>{
    const number = String(idx+1).padStart(3,'0');
    const div = document.createElement('div');
    div.className = 'surah-item';
    div.dataset.num = number;
    div.innerHTML = `<div style="display:flex;justify-content:space-between;align-items:center"><div style="text-align:right">${number}. <strong>${name}</strong></div><div class="small">اضغط للعرض والاستماع</div></div>`;
    div.onclick = ()=> selectSurah(number, name, div);
    surahListEl.appendChild(div);
  });
}

let selectedDiv = null;
let currentSurahNumber = null;

function selectSurah(number, name, divEl){
  if(selectedDiv) selectedDiv.classList.remove('active');
  selectedDiv = divEl; selectedDiv.classList.add('active');
  currentSurahNumber = number;
  currentSurahName.textContent = `${name} — ${Number(number)} (${number})`;
  // صورة السورة (مصدر إنترنت). إذا لم تُعرض ستخفي الصورة.
  surahImage.style.display = 'block';
  surahImage.src = `https://www.searchtruth.org/images/quran/${number}.png`;
  // جلب نص السورة
  loadSurahText(Number(number));
  playBtn.disabled = false;
}

async function loadSurahText(num){
  ayahsDiv.innerHTML = '<div class="small">...جاري تحميل نص السورة</div>';
  try{
    const res = await fetch(`https://api.alquran.cloud/v1/surah/${num}`);
    const data = await res.json();
    if(data && data.data && data.data.ayahs){
      const ay = data.data.ayahs.map(a=>`<div style="margin-bottom:8px"><span style="font-size:20px">${a.text}</span><div class=\"small\">(${a.numberInSurah})</div></div>`).join('');
      ayahsDiv.innerHTML = ay;
    } else {
      ayahsDiv.innerHTML = '<div class="small">لم أتمكن من جلب النص الآن.</div>';
    }
  } catch(err){
    ayahsDiv.innerHTML = `<div class="small">خطأ في جلب النص: ${err.message}</div>`;
    console.error(err);
  }
}

// تجربة تحميل ملف صوتي من قائمة قواعد URLs بالتتابع
async function tryPlayFromBases(bases, surahNum){
  statusDiv.textContent = '';
  playerWrap.hidden = false;
  let tried = 0;
  return new Promise((resolve,reject)=>{
    function tryNext(){
      if(tried >= bases.length){
        statusDiv.textContent = 'لم يتم العثور على ملف صوت صالح من المصادر المتاحة.';
        return reject(new Error('No audio source available'));
      }
      const base = bases[tried++];
      const url = `${base}${surahNum}.mp3`;
      statusDiv.textContent = `محاولة تحميل الصوت من: ${url}`;
      // إعداد المكرر للتجربة: عند خطأ ننتقل للمصدر التالي
      audioPlayer.pause();
      audioPlayer.src = url;
      // محاولة تشغيل بعد تحميل metadata
      const onCan = ()=>{
        audioPlayer.removeEventListener('canplay', onCan);
        audioPlayer.removeEventListener('error', onErr);
        statusDiv.textContent = `يتم التشغيل من: ${url}`;
        audioPlayer.play().catch(e=>{
          // قد يمنع المتصفح التشغيل التلقائي؛ لا يزال يعتبر صالحًا
          statusDiv.textContent = `تم تحميل الملف، اضغط تشغيل إذا لم يبدأ تلقائياً.`;
        });
        resolve(url);
      };
      const onErr = ()=>{
        audioPlayer.removeEventListener('canplay', onCan);
        audioPlayer.removeEventListener('error', onErr);
        // جرب التالي
        statusDiv.textContent = `فشل تحميل من: ${url} — تجربة مصدر آخر...`;
        setTimeout(tryNext, 300);
      };
      audioPlayer.addEventListener('canplay', onCan);
      audioPlayer.addEventListener('error', onErr);
      // قم بتحميل الملف (بداية الطلب)
      audioPlayer.load();
    }
    tryNext();
  });
}

playBtn.addEventListener('click', async ()=>{
  if(!currentSurahNumber){ alert('اختر سورة أولاً'); return; }
  playBtn.disabled = true; stopBtn.disabled = false;
  const reciterName = reciterSelect.value;
  const bases = reciters[reciterName] || [];
  try{
    await tryPlayFromBases(bases, currentSurahNumber);
  } catch(err){
    console.warn('No audio source worked for this reciter', err);
    statusDiv.textContent = 'لم يعمل هذا القارئ مع هذه السورة. جرّب قارئاً آخر.';
  } finally{
    playBtn.disabled = false;
  }
});

stopBtn.addEventListener('click', ()=>{
  audioPlayer.pause(); audioPlayer.currentTime = 0; stopBtn.disabled = true; statusDiv.textContent = 'تم الإيقاف.';
});

// بحث في أسماء السور
searchInput.addEventListener('input', ()=>{
  const q = searchInput.value.trim().toLowerCase();
  const items = document.querySelectorAll('.surah-item');
  items.forEach(it=>{
    const txt = it.textContent.toLowerCase();
    it.style.display = (txt.includes(q) || it.dataset.num.includes(q)) ? '' : 'none';
  });
});

refreshBtn.addEventListener('click', ()=>{ populateSurahList(); statusDiv.textContent = 'قائمة السور أعيد تحميلها.' });

// تهيئة أولية
populateReciters(); populateSurahList();

// اختياري: اختيار افتراضي
reciterSelect.value = 'مشاري العفاسي';
</script>
</body>
</html>
