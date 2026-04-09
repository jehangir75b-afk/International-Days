# International-Days
International Days Celebrated All over the world
Author Jehangir Khan
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>International Days Calendar</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif; background: #f5f5f3; color: #1a1a1a; min-height: 100vh; padding: 2rem 1rem; }
  .container { max-width: 860px; margin: 0 auto; }
  h1 { font-size: 24px; font-weight: 600; margin-bottom: 0.25rem; color: #1a1a1a; }
  .subtitle { font-size: 14px; color: #6b7280; margin-bottom: 1.5rem; }
  .top-bar { display: flex; align-items: center; gap: 12px; margin-bottom: 1.25rem; flex-wrap: wrap; }
  .top-bar h2 { font-size: 18px; font-weight: 500; color: #1a1a1a; flex: 1; }
  .search-box { padding: 8px 14px; font-size: 14px; border: 1px solid #d1d5db; border-radius: 8px; width: 220px; background: #fff; color: #1a1a1a; outline: none; transition: border-color 0.15s; }
  .search-box:focus { border-color: #185FA5; box-shadow: 0 0 0 3px rgba(24,95,165,0.1); }
  .month-tabs { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 1.25rem; }
  .tab { padding: 5px 13px; font-size: 13px; border: 1px solid #d1d5db; border-radius: 8px; cursor: pointer; background: #fff; color: #6b7280; transition: all 0.15s; font-family: inherit; }
  .tab:hover { background: #f3f4f6; }
  .tab.active { background: #185FA5; color: #E6F1FB; border-color: #185FA5; }
  .cat-filters { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 1rem; }
  .cat-btn { padding: 4px 11px; font-size: 12px; border: 1px solid #e5e7eb; border-radius: 20px; cursor: pointer; background: #f3f4f6; color: #6b7280; transition: all 0.12s; font-family: inherit; }
  .cat-btn.on { color: #fff; border-color: transparent; }
  .cat-btn.on.health { background: #1D9E75; }
  .cat-btn.on.environment { background: #3B6D11; }
  .cat-btn.on.human-rights { background: #185FA5; }
  .cat-btn.on.culture { background: #7F77DD; }
  .cat-btn.on.science { background: #BA7517; }
  .cat-btn.on.peace { background: #D4537E; }
  .cat-btn.on.other { background: #5F5E5A; }
  .stats { display: flex; gap: 12px; flex-wrap: wrap; margin-bottom: 1.25rem; }
  .stat-card { background: #fff; border: 1px solid #e5e7eb; border-radius: 8px; padding: 10px 16px; flex: 1; min-width: 100px; text-align: center; }
  .stat-num { font-size: 22px; font-weight: 600; color: #185FA5; }
  .stat-label { font-size: 11px; color: #6b7280; margin-top: 2px; }
  .filter-row { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; margin-bottom: 1rem; }
  .filter-row-label { font-size: 12px; color: #9ca3af; white-space: nowrap; }
  .un-btn { display: inline-flex; align-items: center; gap: 7px; padding: 7px 16px; font-size: 13px; font-weight: 500; border: 2px solid #185FA5; border-radius: 8px; cursor: pointer; background: #fff; color: #185FA5; transition: all 0.15s; font-family: inherit; }
  .un-btn:hover { background: #EBF3FB; }
  .un-btn.active { background: #185FA5; color: #fff; border-color: #185FA5; }
  .un-btn .un-icon { display: inline-flex; align-items: center; justify-content: center; width: 18px; height: 18px; border-radius: 50%; font-size: 10px; font-weight: 700; background: #185FA5; color: #fff; flex-shrink: 0; }
  .un-btn.active .un-icon { background: #fff; color: #185FA5; }
  .un-btn .un-count { font-size: 11px; opacity: 0.75; margin-left: 2px; }
  .count-label { font-size: 13px; color: #6b7280; margin-bottom: 0.75rem; }
  .day-list { display: flex; flex-direction: column; gap: 6px; }
  .day-card { display: flex; align-items: flex-start; gap: 12px; padding: 11px 16px; border-radius: 8px; border: 1px solid #e5e7eb; background: #fff; transition: border-color 0.12s; }
  .day-card:hover { border-color: #b5d4f4; }
  .day-date { font-size: 12px; font-weight: 500; color: #6b7280; min-width: 68px; padding-top: 2px; }
  .day-dot { width: 8px; height: 8px; border-radius: 50%; margin-top: 5px; flex-shrink: 0; }
  .dot-health { background: #1D9E75; }
  .dot-environment { background: #3B6D11; }
  .dot-human-rights { background: #185FA5; }
  .dot-culture { background: #7F77DD; }
  .dot-science { background: #BA7517; }
  .dot-peace { background: #D4537E; }
  .dot-other { background: #888780; }
  .day-name { font-size: 14px; font-weight: 500; color: #1a1a1a; }
  .day-cat { font-size: 11px; color: #9ca3af; margin-top: 2px; }
  .badge { display: inline-block; font-size: 10px; padding: 1px 7px; border-radius: 10px; margin-left: 8px; background: #B5D4F4; color: #0C447C; vertical-align: middle; }
  .no-results { text-align: center; padding: 2.5rem; color: #9ca3af; font-size: 14px; background: #fff; border-radius: 8px; border: 1px solid #e5e7eb; }
  .legend { display: flex; gap: 14px; flex-wrap: wrap; margin-bottom: 1.25rem; }
  .legend-item { display: flex; align-items: center; gap: 6px; font-size: 12px; color: #6b7280; }
  .legend-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
  footer { margin-top: 2rem; text-align: center; font-size: 12px; color: #9ca3af; }
</style>
</head>
<body>
<div class="container">
  <h1>International Days Calendar</h1>
  <p class="subtitle">200+ internationally observed days — filterable by month, category, and keyword</p>

  <div class="stats">
    <div class="stat-card"><div class="stat-num" id="total-count"></div><div class="stat-label">Total Days</div></div>
    <div class="stat-card"><div class="stat-num" id="un-count"></div><div class="stat-label">UN Recognized</div></div>
    <div class="stat-card"><div class="stat-num">7</div><div class="stat-label">Categories</div></div>
    <div class="stat-card"><div class="stat-num">12</div><div class="stat-label">Months</div></div>
  </div>

  <div class="top-bar">
    <span style="font-size:15px;font-weight:500;color:#1a1a1a;">Filter &amp; Search</span>
    <input class="search-box" type="text" placeholder="Search days..." id="search" />
  </div>

  <div class="month-tabs" id="month-tabs"></div>

  <div class="cat-filters" id="cat-filters"></div>

  <div class="filter-row">
    <span class="filter-row-label">Quick filter:</span>
    <button class="un-btn" id="un-btn" onclick="toggleUN()">
      <span class="un-icon">UN</span>
      UN Recognized Days Only
      <span class="un-count" id="un-btn-count"></span>
    </button>
  </div>

  <div class="legend" id="legend"></div>

  <div class="count-label" id="count-label"></div>
  <div class="day-list" id="day-list"></div>

  <footer>Data compiled from United Nations, WHO, UNESCO and international observance registries &nbsp;·&nbsp; UN = officially recognized by the United Nations</footer>
</div>

<script>
const DAYS = [
  {date:"Jan 1",name:"New Year's Day",cat:"culture"},{date:"Jan 4",name:"World Braille Day",cat:"human-rights"},{date:"Jan 6",name:"World Day of War Orphans",cat:"human-rights"},{date:"Jan 10",name:"World Hindi Day",cat:"culture"},{date:"Jan 11",name:"International Thank-You Day",cat:"culture"},{date:"Jan 13",name:"World Disability Day (Intl)",cat:"human-rights"},{date:"Jan 24",name:"International Day of Education",cat:"human-rights",un:true},{date:"Jan 25",name:"International Customs Day",cat:"other"},{date:"Jan 26",name:"International Day of Clean Energy",cat:"environment",un:true},{date:"Jan 27",name:"International Holocaust Remembrance Day",cat:"human-rights",un:true},{date:"Jan 28",name:"World Leprosy Day",cat:"health"},
  {date:"Feb 2",name:"World Wetlands Day",cat:"environment"},{date:"Feb 4",name:"World Cancer Day",cat:"health"},{date:"Feb 6",name:"International Day of Zero Tolerance to FGM",cat:"human-rights",un:true},{date:"Feb 11",name:"International Day of Women & Girls in Science",cat:"science",un:true},{date:"Feb 13",name:"World Radio Day",cat:"culture",un:true},{date:"Feb 14",name:"Valentine's Day",cat:"culture"},{date:"Feb 20",name:"World Day of Social Justice",cat:"human-rights",un:true},{date:"Feb 21",name:"International Mother Language Day",cat:"culture",un:true},{date:"Feb 22",name:"World Scout Day",cat:"culture"},{date:"Feb 28",name:"Rare Disease Day",cat:"health"},
  {date:"Mar 1",name:"Zero Discrimination Day",cat:"human-rights"},{date:"Mar 3",name:"World Wildlife Day",cat:"environment",un:true},{date:"Mar 4",name:"World Obesity Day",cat:"health"},{date:"Mar 8",name:"International Women's Day",cat:"human-rights",un:true},{date:"Mar 10",name:"World Kidney Day",cat:"health"},{date:"Mar 15",name:"World Consumer Rights Day",cat:"human-rights"},{date:"Mar 20",name:"International Day of Happiness",cat:"culture",un:true},{date:"Mar 20",name:"World Sparrow Day",cat:"environment"},{date:"Mar 21",name:"World Down Syndrome Day",cat:"health",un:true},{date:"Mar 21",name:"International Day for Elimination of Racial Discrimination",cat:"human-rights",un:true},{date:"Mar 21",name:"World Poetry Day",cat:"culture",un:true},{date:"Mar 21",name:"International Nowruz Day",cat:"culture",un:true},{date:"Mar 21",name:"World Forestry Day",cat:"environment"},{date:"Mar 22",name:"World Water Day",cat:"environment",un:true},{date:"Mar 23",name:"World Meteorological Day",cat:"environment"},{date:"Mar 24",name:"World Tuberculosis Day",cat:"health"},{date:"Mar 25",name:"International Day of Remembrance of Slavery Victims",cat:"human-rights",un:true},{date:"Mar 27",name:"World Theatre Day",cat:"culture"},
  {date:"Apr 2",name:"World Autism Awareness Day",cat:"health",un:true},{date:"Apr 4",name:"International Day for Mine Awareness",cat:"peace",un:true},{date:"Apr 6",name:"International Day of Sport for Development and Peace",cat:"peace",un:true},{date:"Apr 7",name:"World Health Day",cat:"health",un:true},{date:"Apr 12",name:"International Day of Human Space Flight",cat:"science",un:true},{date:"Apr 15",name:"World Art Day",cat:"culture"},{date:"Apr 16",name:"World Voice Day",cat:"culture"},{date:"Apr 18",name:"World Heritage Day",cat:"culture"},{date:"Apr 20",name:"Chinese Language Day",cat:"culture",un:true},{date:"Apr 22",name:"Earth Day",cat:"environment"},{date:"Apr 23",name:"World Book Day",cat:"culture",un:true},{date:"Apr 23",name:"World English Language Day",cat:"culture",un:true},{date:"Apr 25",name:"World Malaria Day",cat:"health"},{date:"Apr 26",name:"World Intellectual Property Day",cat:"other"},{date:"Apr 28",name:"World Day for Safety and Health at Work",cat:"human-rights"},{date:"Apr 29",name:"International Dance Day",cat:"culture"},{date:"Apr 30",name:"International Jazz Day",cat:"culture",un:true},
  {date:"May 1",name:"International Workers' Day (Labour Day)",cat:"human-rights"},{date:"May 2",name:"World Tuna Day",cat:"environment",un:true},{date:"May 3",name:"World Press Freedom Day",cat:"human-rights",un:true},{date:"May 5",name:"World Hand Hygiene Day",cat:"health"},{date:"May 8",name:"World Red Cross & Red Crescent Day",cat:"peace"},{date:"May 9",name:"World Migratory Bird Day",cat:"environment"},{date:"May 10",name:"World Lupus Day",cat:"health"},{date:"May 12",name:"International Nurses Day",cat:"health"},{date:"May 15",name:"International Day of Families",cat:"human-rights",un:true},{date:"May 16",name:"International Day of Living Together in Peace",cat:"peace",un:true},{date:"May 16",name:"International Day of Light",cat:"science",un:true},{date:"May 17",name:"World Hypertension Day",cat:"health"},{date:"May 17",name:"World Telecommunication Day",cat:"science"},{date:"May 17",name:"International Day Against Homophobia, Biphobia & Transphobia",cat:"human-rights"},{date:"May 18",name:"International Museum Day",cat:"culture"},{date:"May 20",name:"World Bee Day",cat:"environment",un:true},{date:"May 20",name:"World Metrology Day",cat:"science"},{date:"May 21",name:"World Cultural Diversity for Dialogue and Development Day",cat:"culture",un:true},{date:"May 22",name:"International Day for Biological Diversity",cat:"environment",un:true},{date:"May 23",name:"World Turtle Day",cat:"environment"},{date:"May 25",name:"Africa Day",cat:"culture"},{date:"May 25",name:"World Thyroid Day",cat:"health"},{date:"May 28",name:"World Hunger Day",cat:"human-rights"},{date:"May 31",name:"World No Tobacco Day",cat:"health",un:true},
  {date:"Jun 1",name:"International Children's Day",cat:"human-rights"},{date:"Jun 4",name:"International Day of Innocent Children Victims",cat:"human-rights",un:true},{date:"Jun 5",name:"World Environment Day",cat:"environment",un:true},{date:"Jun 7",name:"World Food Safety Day",cat:"health",un:true},{date:"Jun 8",name:"World Oceans Day",cat:"environment",un:true},{date:"Jun 12",name:"World Day Against Child Labour",cat:"human-rights",un:true},{date:"Jun 13",name:"International Albinism Awareness Day",cat:"human-rights",un:true},{date:"Jun 14",name:"World Blood Donor Day",cat:"health"},{date:"Jun 15",name:"World Elder Abuse Awareness Day",cat:"human-rights",un:true},{date:"Jun 17",name:"World Day to Combat Desertification",cat:"environment",un:true},{date:"Jun 19",name:"International Day for Elimination of Sexual Violence in Conflict",cat:"human-rights",un:true},{date:"Jun 20",name:"World Refugee Day",cat:"human-rights",un:true},{date:"Jun 21",name:"World Music Day",cat:"culture"},{date:"Jun 21",name:"International Yoga Day",cat:"health",un:true},{date:"Jun 23",name:"United Nations Public Service Day",cat:"other",un:true},{date:"Jun 23",name:"International Olympic Day",cat:"culture"},{date:"Jun 26",name:"International Day Against Drug Abuse",cat:"health",un:true},{date:"Jun 26",name:"International Day in Support of Victims of Torture",cat:"human-rights",un:true},{date:"Jun 29",name:"International Day of the Tropics",cat:"environment",un:true},{date:"Jun 30",name:"International Asteroid Day",cat:"science"},
  {date:"Jul 6",name:"World Zoonoses Day",cat:"health"},{date:"Jul 11",name:"World Population Day",cat:"human-rights",un:true},{date:"Jul 15",name:"World Youth Skills Day",cat:"human-rights",un:true},{date:"Jul 18",name:"Nelson Mandela International Day",cat:"human-rights",un:true},{date:"Jul 20",name:"World Chess Day",cat:"culture"},{date:"Jul 22",name:"World Brain Day",cat:"health"},{date:"Jul 25",name:"World Drowning Prevention Day",cat:"health",un:true},{date:"Jul 26",name:"International Day for Conservation of the Mangrove Ecosystem",cat:"environment",un:true},{date:"Jul 28",name:"World Hepatitis Day",cat:"health"},{date:"Jul 29",name:"International Tiger Day",cat:"environment"},{date:"Jul 30",name:"International Day of Friendship",cat:"culture",un:true},{date:"Jul 30",name:"World Day Against Trafficking in Persons",cat:"human-rights",un:true},
  {date:"Aug 6",name:"Hiroshima Day",cat:"peace"},{date:"Aug 9",name:"International Day of the World's Indigenous Peoples",cat:"human-rights",un:true},{date:"Aug 12",name:"International Youth Day",cat:"human-rights",un:true},{date:"Aug 12",name:"World Elephant Day",cat:"environment"},{date:"Aug 13",name:"International Left-Handers Day",cat:"culture"},{date:"Aug 19",name:"World Humanitarian Day",cat:"human-rights",un:true},{date:"Aug 19",name:"World Photography Day",cat:"culture"},{date:"Aug 20",name:"World Mosquito Day",cat:"health"},{date:"Aug 23",name:"International Day for Remembrance of the Slave Trade",cat:"human-rights",un:true},{date:"Aug 26",name:"Women's Equality Day",cat:"human-rights"},{date:"Aug 29",name:"International Day Against Nuclear Tests",cat:"peace",un:true},{date:"Aug 30",name:"International Day of Victims of Enforced Disappearances",cat:"human-rights",un:true},
  {date:"Sep 1",name:"World Letter Writing Day",cat:"culture"},{date:"Sep 5",name:"International Day of Charity",cat:"human-rights",un:true},{date:"Sep 7",name:"International Day of Clean Air",cat:"environment",un:true},{date:"Sep 8",name:"International Literacy Day",cat:"human-rights",un:true},{date:"Sep 10",name:"World Suicide Prevention Day",cat:"health"},{date:"Sep 13",name:"International Programmers' Day",cat:"science"},{date:"Sep 15",name:"International Day of Democracy",cat:"human-rights",un:true},{date:"Sep 16",name:"International Day for Preservation of the Ozone Layer",cat:"environment",un:true},{date:"Sep 17",name:"World Patient Safety Day",cat:"health",un:true},{date:"Sep 18",name:"International Equal Pay Day",cat:"human-rights",un:true},{date:"Sep 20",name:"World Cleanup Day",cat:"environment"},{date:"Sep 21",name:"International Day of Peace",cat:"peace",un:true},{date:"Sep 22",name:"World Car Free Day",cat:"environment"},{date:"Sep 23",name:"International Day of Sign Languages",cat:"human-rights",un:true},{date:"Sep 25",name:"World Pharmacists Day",cat:"health"},{date:"Sep 26",name:"International Day for Total Elimination of Nuclear Weapons",cat:"peace",un:true},{date:"Sep 27",name:"World Tourism Day",cat:"culture"},{date:"Sep 28",name:"World Rabies Day",cat:"health"},{date:"Sep 29",name:"World Heart Day",cat:"health"},{date:"Sep 30",name:"International Translation Day",cat:"culture",un:true},
  {date:"Oct 1",name:"International Day of Older Persons",cat:"human-rights",un:true},{date:"Oct 2",name:"International Day of Non-Violence (Gandhi's Birthday)",cat:"peace",un:true},{date:"Oct 4",name:"World Animal Day",cat:"environment"},{date:"Oct 5",name:"World Teachers' Day",cat:"human-rights",un:true},{date:"Oct 9",name:"World Post Day",cat:"other"},{date:"Oct 10",name:"World Mental Health Day",cat:"health"},{date:"Oct 11",name:"International Day of the Girl Child",cat:"human-rights",un:true},{date:"Oct 12",name:"World Arthritis Day",cat:"health"},{date:"Oct 13",name:"International Day for Disaster Risk Reduction",cat:"other",un:true},{date:"Oct 15",name:"International Day of Rural Women",cat:"human-rights",un:true},{date:"Oct 16",name:"World Food Day",cat:"human-rights",un:true},{date:"Oct 17",name:"International Day for Eradication of Poverty",cat:"human-rights",un:true},{date:"Oct 18",name:"World Menopause Day",cat:"health"},{date:"Oct 20",name:"World Statistics Day",cat:"science",un:true},{date:"Oct 20",name:"World Osteoporosis Day",cat:"health"},{date:"Oct 24",name:"United Nations Day",cat:"other",un:true},{date:"Oct 24",name:"World Polio Day",cat:"health"},{date:"Oct 27",name:"World Day for Audiovisual Heritage",cat:"culture",un:true},{date:"Oct 28",name:"International Animation Day",cat:"culture"},{date:"Oct 29",name:"World Stroke Day",cat:"health"},{date:"Oct 31",name:"World Cities Day",cat:"other",un:true},{date:"Oct 31",name:"Halloween",cat:"culture"},
  {date:"Nov 1",name:"World Vegan Day",cat:"environment"},{date:"Nov 2",name:"International Day to End Impunity for Crimes Against Journalists",cat:"human-rights",un:true},{date:"Nov 5",name:"World Tsunami Awareness Day",cat:"other",un:true},{date:"Nov 6",name:"International Day for Preventing Exploitation of Environment in War",cat:"environment",un:true},{date:"Nov 8",name:"International Radiology Day",cat:"health"},{date:"Nov 10",name:"World Science Day for Peace and Development",cat:"science",un:true},{date:"Nov 11",name:"Remembrance Day / Armistice Day",cat:"peace"},{date:"Nov 13",name:"World Kindness Day",cat:"culture"},{date:"Nov 14",name:"World Diabetes Day",cat:"health"},{date:"Nov 15",name:"World Recycling Day",cat:"environment"},{date:"Nov 16",name:"International Day for Tolerance",cat:"human-rights",un:true},{date:"Nov 17",name:"International Students Day",cat:"human-rights"},{date:"Nov 19",name:"World Toilet Day",cat:"environment",un:true},{date:"Nov 19",name:"International Men's Day",cat:"human-rights"},{date:"Nov 20",name:"Universal Children's Day",cat:"human-rights",un:true},{date:"Nov 20",name:"World Philosophy Day",cat:"culture",un:true},{date:"Nov 21",name:"World Television Day",cat:"culture",un:true},{date:"Nov 21",name:"World Fisheries Day",cat:"environment"},{date:"Nov 25",name:"International Day for Elimination of Violence Against Women",cat:"human-rights",un:true},{date:"Nov 26",name:"World Sustainable Transport Day",cat:"environment",un:true},{date:"Nov 30",name:"Computer Security Day",cat:"science"},
  {date:"Dec 1",name:"World AIDS Day",cat:"health"},{date:"Dec 2",name:"International Day for the Abolition of Slavery",cat:"human-rights",un:true},{date:"Dec 3",name:"International Day of Persons with Disabilities",cat:"human-rights",un:true},{date:"Dec 5",name:"International Volunteer Day",cat:"human-rights",un:true},{date:"Dec 5",name:"World Soil Day",cat:"environment"},{date:"Dec 9",name:"International Anti-Corruption Day",cat:"human-rights",un:true},{date:"Dec 10",name:"Human Rights Day",cat:"human-rights",un:true},{date:"Dec 11",name:"International Mountain Day",cat:"environment",un:true},{date:"Dec 12",name:"International Day of Neutrality",cat:"peace",un:true},{date:"Dec 12",name:"Universal Health Coverage Day",cat:"health",un:true},{date:"Dec 15",name:"International Tea Day",cat:"culture"},{date:"Dec 18",name:"International Migrants Day",cat:"human-rights",un:true},{date:"Dec 18",name:"Arabic Language Day",cat:"culture",un:true},{date:"Dec 20",name:"International Human Solidarity Day",cat:"human-rights",un:true},{date:"Dec 25",name:"Christmas Day",cat:"culture"}
];

const months = ["All","Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];
const cats = ["health","environment","human-rights","culture","science","peace","other"];
const catLabels = {health:"Health",environment:"Environment","human-rights":"Human Rights",culture:"Culture & Heritage",science:"Science & Tech",peace:"Peace",other:"Other"};

document.getElementById("total-count").textContent = DAYS.length;
document.getElementById("un-count").textContent = DAYS.filter(d=>d.un).length;

let selMonth = "All", selCats = new Set(cats), searchQ = "", unOnly = false;

const unTotal = DAYS.filter(d=>d.un).length;
document.getElementById("un-btn-count").textContent = `(${unTotal})`;

function renderTabs() {
  document.getElementById("month-tabs").innerHTML = months.map(m =>
    `<button class="tab${selMonth===m?' active':''}" onclick="setMonth('${m}')">${m}</button>`).join("");
}

function renderCats() {
  document.getElementById("cat-filters").innerHTML = cats.map(c =>
    `<button class="cat-btn${selCats.has(c)?' on '+c:''}" onclick="toggleCat('${c}')">${catLabels[c]}</button>`).join("");
}

function renderLegend() {
  document.getElementById("legend").innerHTML = cats.map(c =>
    `<span class="legend-item"><span class="legend-dot dot-${c}"></span>${catLabels[c]}</span>`).join("");
}

function renderList() {
  const q = searchQ.toLowerCase();
  const filtered = DAYS.filter(d => {
    return (selMonth==="All" || d.date.startsWith(selMonth)) &&
           selCats.has(d.cat) &&
           (!q || d.name.toLowerCase().includes(q) || d.date.toLowerCase().includes(q)) &&
           (!unOnly || d.un);
  });
  document.getElementById("count-label").textContent = `${filtered.length} day${filtered.length!==1?'s':''} shown${unOnly?' · UN recognized only':''}`;
  const el = document.getElementById("day-list");
  if (!filtered.length) { el.innerHTML = '<div class="no-results">No matching days found.</div>'; return; }
  el.innerHTML = filtered.map(d => `
    <div class="day-card">
      <span class="day-date">${d.date}</span>
      <span class="day-dot dot-${d.cat}"></span>
      <div>
        <span class="day-name">${d.name}${d.un?'<span class="badge">UN</span>':''}</span>
        <div class="day-cat">${catLabels[d.cat]}</div>
      </div>
    </div>`).join("");
}

function setMonth(m) { selMonth = m; renderTabs(); renderList(); }
function toggleCat(c) {
  if (selCats.has(c)) { if (selCats.size > 1) selCats.delete(c); }
  else selCats.add(c);
  renderCats(); renderList();
}
function toggleUN() {
  unOnly = !unOnly;
  const btn = document.getElementById("un-btn");
  btn.classList.toggle("active", unOnly);
  renderList();
}

document.getElementById("search").addEventListener("input", e => { searchQ = e.target.value; renderList(); });

renderTabs(); renderCats(); renderLegend(); renderList();
</script>
</body>
</html>
