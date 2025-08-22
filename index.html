<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8" />
<title>給料計算ツール / Salary Calculator</title>
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no" />
<style>
  :root{
    --bg:#f2f5f9; --card:#fff; --ink:#0b1020;
    --muted:#334155; --line:#e8eef7; --pill:#f7f9fc;
    --ok:#059669; --warn:#dc2626; --act:#2563eb; --act2:#0ea5e9; --exp:#7c3aed;
  }
  *{box-sizing:border-box}
  body{margin:0;font-family:system-ui, -apple-system, Segoe UI, Roboto, "Noto Sans JP", sans-serif;background:var(--bg);display:flex;justify-content:center}
  .card{width:min(96vw,820px);background:var(--card);border-radius:14px;box-shadow:0 8px 24px rgba(0,0,0,.1);padding:20px;margin:20px}
  h1{margin:0 0 6px;text-align:center}
  .sub{margin:0 0 16px;text-align:center;color:#64748b;font-size:13px}
  .toolbar{display:flex;gap:10px;flex-wrap:wrap;justify-content:center;margin:8px 0 16px}
  .toolbar .group{display:flex;gap:8px;align-items:center;background:var(--pill);border:1px solid var(--line);padding:6px 10px;border-radius:12px}
  .toolbar label{font-size:13px;color:var(--muted)}
  select,input[type="number"]{height:36px;padding:0 10px;border-radius:10px;border:1px solid var(--line);background:#fff}
  .status,.salary,.total{padding:10px 12px;background:var(--pill);border:1px solid var(--line);border-radius:12px;margin:10px 0;font-weight:700}
  .salary,.total{background:var(--ink);color:#fff;text-align:center}
  button{padding:10px 14px;border:none;border-radius:10px;color:#fff;font-size:15px;cursor:pointer}
  .reset{background:var(--warn)} .save-btn{background:var(--ok)} .export-btn{background:var(--exp)}
  .plus{background:var(--act)} .minus{background:var(--act2)}
  .row{display:grid;gap:10px}
  @media (min-width:560px){ .row{ grid-template-columns:1fr auto } }
  .control-block{display:grid;gap:8px;margin:10px 0}
  .months{margin-top:20px}
  .months-grid{display:grid;gap:8px}
  .month-item{display:flex;justify-content:space-between;align-items:center;padding:8px 10px;border:1px solid var(--line);border-radius:10px;background:#fbfdff}
  .month-label{font-weight:600;color:var(--muted)}
  .month-value{display:flex;gap:6px;align-items:center}
  .month-input{width:160px;text-align:right;border:none;background:transparent;font-size:15px;padding:4px 6px;border-radius:6px}
  .month-unit{font-size:14px;color:var(--muted)}
  .month-days{color:#64748b;font-size:13px}
  .btns{display:flex;gap:10px;margin-top:10px;flex-wrap:wrap}
</style>
</head>
<body>
<div class="card">
  <h1 id="title">給料計算ツール</h1>
  <p class="sub" id="todayLabel"></p>

  <!-- 言語/通貨ツールバー -->
  <div class="toolbar">
    <div class="group">
      <label for="langSelect">Language</label>
      <select id="langSelect">
        <option value="ja">日本語</option>
        <option value="en">English</option>
      </select>
    </div>
    <div class="group">
      <label for="currencySelect" id="currencyLabel">通貨</label>
      <select id="currencySelect">
        <option value="JPY">JPY (¥)</option>
        <option value="USD">USD ($)</option>
      </select>
    </div>
    <div class="group" id="rateGroup">
      <label for="rateInput" id="rateLabel">レート(USD→JPY)</label>
      <input id="rateInput" type="number" step="0.01" min="0.01" style="width:110px" />
      <button id="rateApplyBtn" class="plus" type="button">適用</button>
    </div>
  </div>

  <!-- 勤務日数 -->
  <div class="control-block">
    <label for="daysSelect" id="daysLabel">勤務日数:</label>
    <select id="daysSelect"></select>
  </div>

  <!-- 勤務時間 -->
  <div class="control-block">
    <label for="hoursSelect" id="hoursLabel">勤務時間（時間/日）:</label>
    <select id="hoursSelect"></select>
  </div>

  <!-- 追加金額 -->
  <div class="control-block">
    <label for="stepSelect" id="extraLabel">追加金額:</label>
    <div style="display:flex;gap:8px;flex-wrap:wrap">
      <select id="stepSelect"></select>
      <button class="plus"  onclick="addMoneyByStep()" id="plusBtn">＋</button>
      <button class="minus" onclick="removeMoneyByStep()" id="minusBtn">−</button>
      <div class="status" id="wageInfo" style="margin:0 0 0 8px; font-weight:600;"></div>
    </div>
  </div>

  <div class="control-block">
    <button class="reset" onclick="resetData()" id="resetBtn">リセット</button>
  </div>

  <div class="salary" id="salary">給料：0 円</div>

  <div class="row">
    <select id="monthSelect"></select>
    <button class="save-btn" onclick="saveToSelectedMonth()" id="saveBtn">この金額を保存</button>
  </div>

  <section class="months">
    <h2 id="monthSectionTitle">月別データ</h2>
    <div class="months-grid" id="monthsGrid"></div>
    <div class="total" id="totalYear">年間合計：0 円</div>
  </section>

  <div class="btns">
    <button class="export-btn" onclick="printView()" id="printBtn">印刷 / PDF保存</button>
    <button class="export-btn" onclick="exportCSV()" id="csvBtn">CSVダウンロード</button>
  </div>
</div>

<script>
/* ====== 設定・状態（内部は JPY 基準） ====== */
const WAGE_JPY = 1300;                      // 時給（JPY固定・内部基準）
const STORAGE_MONTHS = 'salaryMonths_v9';   // { [m]: {amountJPY, days} }
const STORAGE_STATE  = 'salaryState_v8';    // { days,hours,extraJPY,stepJPY,lang,currency,rate }

let days = 0, hours = 8, extraJPY = 0, stepJPY = 1300;
let months = {};
let lang = 'ja';            // 'ja' | 'en'
let currency = 'JPY';       // 'JPY' | 'USD'
let usdJpyRate = 155;       // 1 USD = X JPY

/* ====== i18n ====== */
const I18N = {
  ja: {
    title: '給料計算ツール',
    today: (d,w)=> `本日: ${d}（${w}）`,
    days: '勤務日数:',
    hours: '勤務時間（時間/日）:',
    hoursOpt: (h)=> `${h} 時間/日`,
    extra: '追加金額:',
    reset: 'リセット',
    save: 'この金額を保存',
    monthSection: '月別データ',
    yearTotal: '年間合計',
    print: '印刷 / PDF保存',
    csv: 'CSVダウンロード',
    currency: '通貨',
    rate: 'レート(USD→JPY)',
    wageInfo: (w, cur) => `時給: ${fmtCurrency(w, cur)}`,
    salaryLabel: '給料：',
    monthUnit: (cur)=> cur==='JPY'?'円':'$',
    daySuffix: (n)=> `${n}日`,
    csvHeader: ['項目','値'],
    csvWage: '時給',
    csvHours: '勤務時間(時間/日)',
    csvDays: '勤務日数',
    csvExtra: '現在の追加金額',
    csvNow: '現在の給料',
    csvMonthHead: ['月','金額','日数'],
    csvYear: '年間合計',
  },
  en: {
    title: 'Salary Calculator',
    today: (d,w)=> `Today: ${w}, ${d}`,
    days: 'Working days:',
    hours: 'Working hours (hours/day):',
    hoursOpt: (h)=> `${h} h/day`,
    extra: 'Additional payment:',
    reset: 'Reset',
    save: 'Save this amount',
    monthSection: 'Monthly Data',
    yearTotal: 'Annual Total',
    print: 'Print / Save PDF',
    csv: 'Download CSV',
    currency: 'Currency',
    rate: 'Rate (USD→JPY)',
    wageInfo: (w, cur) => `Wage: ${fmtCurrency(w, cur)}`,
    salaryLabel: 'Salary: ',
    monthUnit: (cur)=> cur==='JPY'?'JPY':'USD',
    daySuffix: (n)=> `${n} days`,
    csvHeader: ['Item','Value'],
    csvWage: 'Hourly wage',
    csvHours: 'Working hours (per day)',
    csvDays: 'Working days',
    csvExtra: 'Current extra',
    csvNow: 'Current salary',
    csvMonthHead: ['Month','Amount','Days'],
    csvYear: 'Annual total',
  }
};
const t = (k)=> I18N[lang][k];

/* ====== 月名 & 曜日名 ====== */
const MONTH_NAMES = {
  ja: ['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'],
  en: ['January','February','March','April','May','June','July','August','September','October','November','December']
};
const WEEKDAY_NAMES = {
  ja: ['日','月','火','水','木','金','土'],
  en: ['Sun','Mon','Tue','Wed','Thu','Fri','Sat']
};

/* ====== 通貨/数値フォーマット ====== */
function fmtCurrencyJPY(n){
  return new Intl.NumberFormat(lang==='ja'?'ja-JP':'en-US',{style:'currency',currency:'JPY',maximumFractionDigits:0}).format(Number(n||0));
}
function fmtCurrencyUSD(n){
  return new Intl.NumberFormat(lang==='ja'?'ja-JP':'en-US',{style:'currency',currency:'USD'}).format(Number(n||0));
}
function fmtCurrency(amount, cur){ return cur==='USD' ? fmtCurrencyUSD(amount) : fmtCurrencyJPY(amount); }
const onlyDigits = s => (s||'').replace(/[^\d.]/g,'');

/* ====== 日付フォーマッタ（見出し用：月名/曜日を言語に合わせる） ====== */
function formatTodayLabel(){
  const d = new Date();
  const y = d.getFullYear();
  const m = d.getMonth(); // 0-based
  const day = d.getDate();
  const wd = d.getDay();
  if(lang==='ja'){
    return t('today')(`${y}年${m+1}月${day}日`, WEEKDAY_NAMES.ja[wd]);
  }else{
    const dateStr = `${MONTH_NAMES.en[m]} ${day}, ${y}`;
    return t('today')(dateStr, WEEKDAY_NAMES.en[wd]);
  }
}

/* ====== 換算（内部はJPY） ====== */
const toDisplay = jpy => currency==='USD' ? (Number(jpy||0) / usdJpyRate) : Number(jpy||0);
const fromDisplayToJPY = disp => currency==='USD' ? Number(disp||0) * usdJpyRate : Number(disp||0);

/* ====== 計算（内部JPY） ====== */
const currentTotalJPY = () => (WAGE_JPY * hours * days) + extraJPY;

/* ====== UI反映 ====== */
function renderTexts(){
  document.title = `${t('title')} / Salary Calculator`;
  document.getElementById('title').textContent = t('title');
  document.getElementById('todayLabel').textContent = formatTodayLabel();

  document.getElementById('daysLabel').textContent = t('days');
  document.getElementById('hoursLabel').textContent = t('hours');
  document.getElementById('extraLabel').textContent = t('extra');
  document.getElementById('resetBtn').textContent = t('reset');
  document.getElementById('saveBtn').textContent = t('save');
  document.getElementById('monthSectionTitle').textContent = t('monthSection');
  document.getElementById('printBtn').textContent = t('print');
  document.getElementById('csvBtn').textContent = t('csv');
  document.getElementById('currencyLabel').textContent = t('currency');
  document.getElementById('rateLabel').textContent = t('rate');

  document.getElementById('wageInfo').textContent = t('wageInfo')( toDisplay(WAGE_JPY), currency );
}

function renderMain(){
  const disp = toDisplay(currentTotalJPY());
  document.getElementById('salary').textContent = t('salaryLabel') + fmtCurrency(disp, currency);

  document.getElementById('daysSelect').value = String(days);
  document.getElementById('hoursSelect').value = String(hours);

  buildStepOptions(); 
  document.getElementById('stepSelect').value = String(stepJPY); // 内部はJPYのまま保持
}

/* ====== 金額操作 ====== */
function getStepJPY(){ 
  stepJPY = Number(document.getElementById('stepSelect').value)||1300; 
  saveState(); 
  return stepJPY; 
}
function addMoneyByStep(){ extraJPY += getStepJPY(); saveState(); renderMain(); }
function removeMoneyByStep(){ extraJPY = Math.max(0, extraJPY - getStepJPY()); saveState(); renderMain(); }

/* ====== リセット ====== */
function resetData(){
  days=0; hours=8; extraJPY=0; stepJPY=1300;
  document.getElementById('daysSelect').value = '0';
  document.getElementById('hoursSelect').value = '8';
  document.getElementById('stepSelect').value  = '1300';
  saveState(); renderMain(); buildMonthsGrid();
}

/* ====== 月保存（内部JPY） ====== */
function saveToSelectedMonth(){
  const sel=String(document.getElementById('monthSelect').value);
  months[sel]={ amountJPY: currentTotalJPY(), days: days };
  saveMonths(); buildMonthsGrid();
}

/* ====== 月一覧 ====== */
function buildMonthsGrid(){
  const grid=document.getElementById('monthsGrid'); grid.innerHTML='';
  let totalJPY=0;
  for(let m=1;m<=12;m++){
    const k=String(m);
    const data=months[k]||{amountJPY:0,days:0};
    totalJPY += data.amountJPY||0;

    const wrap=document.createElement('div'); wrap.className='month-item';
    const label=document.createElement('div'); label.className='month-label'; label.textContent=MONTH_NAMES[lang][m-1];
    const valueWrap=document.createElement('div'); valueWrap.className='month-value';

    const input=document.createElement('input'); 
    input.className='month-input'; 
    input.setAttribute('data-month',k);
    input.value = data.amountJPY ? fmtCurrency( toDisplay(data.amountJPY), currency ) : '';

    input.addEventListener('focus',e=>{
      const amt = toDisplay(months[k]?.amountJPY||0);
      e.target.value = amt? String(+amt.toFixed(currency==='USD'?2:0)) : '';
    });
    input.addEventListener('input',e=>{
      const raw=onlyDigits(e.target.value);
      e.target.value=raw;
      const jpy = fromDisplayToJPY(raw===''?0:Number(raw));
      months[k]={ amountJPY: jpy, days:(months[k]?.days||0) };
      saveMonths(); updateTotal();
    });
    input.addEventListener('blur',e=>{
      const disp = toDisplay(months[k]?.amountJPY||0);
      e.target.value = disp? fmtCurrency(disp, currency) : '';
    });

    const unit=document.createElement('div'); unit.className='month-unit'; unit.textContent = '(' + I18N[lang].monthUnit(currency) + ')';
    const daySpan=document.createElement('div'); daySpan.className='month-days'; daySpan.textContent= `(${I18N[lang].daySuffix(data.days||0)})`;

    valueWrap.appendChild(input); valueWrap.appendChild(unit); valueWrap.appendChild(daySpan);
    wrap.appendChild(label); wrap.appendChild(valueWrap);
    grid.appendChild(wrap);
  }
  document.getElementById('totalYear').textContent = `${t('yearTotal')}：` + fmtCurrency( toDisplay(totalJPY), currency );
}
function updateTotal(){
  let sumJPY=0; for(let m=1;m<=12;m++){ sumJPY += (months[String(m)]?.amountJPY||0); }
  document.getElementById('totalYear').textContent = `${t('yearTotal')}：` + fmtCurrency( toDisplay(sumJPY), currency );
}

/* ====== 保存 ====== */
function saveMonths(){ localStorage.setItem(STORAGE_MONTHS,JSON.stringify(months)); }
function loadMonths(){ try{ const raw=localStorage.getItem(STORAGE_MONTHS); months=raw?JSON.parse(raw):{}; }catch{months={};} }
function saveState(){ localStorage.setItem(STORAGE_STATE, JSON.stringify({days,hours,extraJPY,stepJPY,lang,currency,rate:usdJpyRate})); }
function loadState(){ 
  try{ 
    const raw=localStorage.getItem(STORAGE_STATE); if(!raw) return; 
    const s=JSON.parse(raw)||{}; 
    if(typeof s.days==='number')days=s.days; 
    if(typeof s.hours==='number')hours=s.hours; 
    if(typeof s.extraJPY==='number')extraJPY=s.extraJPY; 
    if(typeof s.stepJPY==='number')stepJPY=s.stepJPY; 
    if(typeof s.lang==='string')lang=s.lang;
    if(typeof s.currency==='string')currency=s.currency;
    if(typeof s.rate==='number')usdJpyRate=s.rate;
  }catch{} 
}

/* ====== 印刷 / CSV ====== */
function printView(){ window.print(); }
function exportCSV(){
  const H = I18N[lang];
  const rows=[[H.csvHeader[0],H.csvHeader[1]]];

  // 先頭に「日付（本日の表示）」を追加（曜日・月名は言語に合わせる）
  rows.push([lang==='ja'?'本日':'Today', document.getElementById('todayLabel').textContent]);

  rows.push([H.csvWage, fmtCurrency(toDisplay(WAGE_JPY), currency)]);
  rows.push([H.csvHours, hours]);
  rows.push([H.csvDays, days]);
  rows.push([H.csvExtra, fmtCurrency(toDisplay(extraJPY), currency)]);
  rows.push([H.csvNow,  fmtCurrency(toDisplay(currentTotalJPY()), currency)]);
  rows.push([]);

  rows.push([H.csvMonthHead[0], H.csvMonthHead[1] + ` (${currency})`, H.csvMonthHead[2]]);
  let sumJPY=0; 
  for(let m=1;m<=12;m++){
    const d=months[String(m)]||{amountJPY:0,days:0};
    const monthName = MONTH_NAMES[lang][m-1]; // 月名を言語で出力
    const amountDisp = Number(toDisplay(d.amountJPY)).toFixed(currency==='USD'?2:0);
    rows.push([monthName, amountDisp, lang==='ja' ? `${d.days||0}` : `${d.days||0}`]);
    sumJPY+=d.amountJPY||0; 
  }
  rows.push([]); 
  rows.push([H.csvYear, Number(toDisplay(sumJPY)).toFixed(currency==='USD'?2:0)]);

  const csv=rows.map(r=>r.map(x=>{
    const s=String(x??''); return /[",\n]/.test(s) ? `"${s.replace(/"/g,'""')}"` : s;
  }).join(',')).join('\n');

  const a=document.createElement('a'); 
  a.href=URL.createObjectURL(new Blob([csv],{type:'text/csv;charset=utf-8;'}));
  a.download='salary.csv'; 
  document.body.appendChild(a); a.click(); a.remove();
}

/* ====== セレクト構築 ====== */
function buildDaysOptions(){
  const sel=document.getElementById('daysSelect'); sel.innerHTML='';
  for(let i=0;i<=365;i++){ const opt=document.createElement('option'); opt.value=String(i); opt.textContent=String(i); sel.appendChild(opt); }
  sel.addEventListener('change',()=>{ days=Number(sel.value); saveState(); renderMain(); buildMonthsGrid(); });
}
function buildHoursOptions(){
  const sel=document.getElementById('hoursSelect'); sel.innerHTML='';
  for(let h=1;h<=24;h++){ 
    const opt=document.createElement('option'); 
    opt.value=String(h); 
    opt.textContent=I18N[lang].hoursOpt(h);
    sel.appendChild(opt); 
  }
  sel.addEventListener('change',()=>{ hours=Number(sel.value); saveState(); renderMain(); buildMonthsGrid(); });
}
function buildStepOptions(){
  const sel=document.getElementById('stepSelect'); sel.innerHTML='';
  // 内部はJPY 900〜10000を100刻みで保持。表示は選択通貨で換算
  for(let v=900; v<=10000; v+=100){
    const opt=document.createElement('option'); 
    opt.value=String(v); // 内部はJPY
    const disp = toDisplay(v);
    opt.textContent = fmtCurrency(disp, currency);
    sel.appendChild(opt);
  }
}
function buildMonthSelect(){
  const sel = document.getElementById('monthSelect');
  const keep = Number(sel.value) || (new Date().getMonth()+1);
  sel.innerHTML = '';
  for(let m=1;m<=12;m++){
    const opt = document.createElement('option');
    opt.value = String(m);
    opt.textContent = MONTH_NAMES[lang][m-1];
    sel.appendChild(opt);
  }
  sel.value = String(keep);
}

/* ====== 反映まとめ ====== */
function applyLangCurrencyUI(){
  document.getElementById('langSelect').value = lang;
  document.getElementById('currencySelect').value = currency;
  document.getElementById('rateInput').value = String(usdJpyRate);

  renderTexts();
  buildMonthSelect();
  buildHoursOptions();
  renderMain();
  buildMonthsGrid();
}

/* ====== イベント配線 ====== */
document.getElementById('langSelect').addEventListener('change', e=>{
  lang = e.target.value;
  saveState();
  applyLangCurrencyUI();
});
document.getElementById('currencySelect').addEventListener('change', e=>{
  currency = e.target.value;
  saveState();
  renderTexts();
  renderMain();
  buildMonthsGrid();
});
document.getElementById('rateApplyBtn').addEventListener('click', ()=>{
  const v = Number(document.getElementById('rateInput').value);
  if(v>0){ usdJpyRate = v; saveState(); renderTexts(); renderMain(); buildMonthsGrid(); }
});

/* ====== 起動 ====== */
(function init(){
  loadMonths(); loadState();
  buildDaysOptions(); buildHoursOptions(); buildStepOptions(); buildMonthSelect();

  // 復元
  document.getElementById('daysSelect').value = String(days||0);
  document.getElementById('hoursSelect').value = String(hours||8);
  document.getElementById('stepSelect').value  = String(stepJPY||1300);
  if(!document.getElementById('monthSelect').value){
    document.getElementById('monthSelect').value = String(new Date().getMonth()+1);
  }
  applyLangCurrencyUI();
})();
</script>
</body>
</html>
