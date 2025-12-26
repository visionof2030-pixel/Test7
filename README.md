
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>أداة إصدار التقارير والشواهد</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap');

*{margin:0;padding:0;box-sizing:border-box;}
html,body{
font-family:'Cairo',sans-serif;background:#ffffff;direction:rtl;
overflow-x:hidden;
}

/* Improved Input Tool */
.container{
max-width:900px;margin:auto;padding:15px;
background:#f7fdf9;border-radius:12px;margin-top:80px;
box-shadow:0 4px 10px rgba(0,0,0,.12);
}
label{font-size:15px;font-weight:700;margin-top:12px;display:block;color:#083024;}
input,select,textarea{
width:100%;padding:12px;margin-top:6px;
border:2px solid #066d4d;border-radius:8px;font-size:15px;
background:#ffffff;
}
textarea{height:120px;resize:none;}

.auto-buttons{
display:flex;gap:6px;margin-top:6px;flex-wrap:wrap;
}
.auto-buttons button{
padding:6px 10px;background:#066d4d;border:none;
color:#fff;cursor:pointer;border-radius:4px;font-size:12px;font-weight:bold;
}

/* Fixed Buttons */
.btn-container{
text-align:center;padding:10px;background:#f5f5f5;
position:fixed;top:0;left:0;width:100%;z-index:20;
display:flex;gap:10px;justify-content:center;
box-shadow:0 3px 6px rgba(0,0,0,0.25);
}
button.main-btn{
background:#066d4d;color:#fff;border:none;
padding:12px 26px;font-size:15px;border-radius:7px;cursor:pointer;
}

/* Report Section */
#report-content{
margin-top:40px;width:100%;
}

.header{
width:100%;height:135px;margin-top:20px;position:relative;overflow:hidden;
background:#083024;display:flex;align-items:center;justify-content:center;
}
.header img{
width:180px;opacity:.95;
}
.header-right-top,.header-right-bottom,.header-left-bottom{
position:absolute;color:#ffffff;font-weight:700;
}
.header-right-top{top:6px;right:12px;font-size:15px;}
.header-right-bottom{bottom:6px;right:12px;font-size:14px;font-weight:600;}
.header-left-bottom{bottom:6px;left:12px;font-size:14px;font-weight:600;direction:ltr;text-align:left;}

.page{
width:100%;max-width:830px;padding:15px;margin:auto;
}

.info-grid{
display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
gap:6px;margin-bottom:12px;
}
.info-box{
background:#e8f2ee;border-radius:8px;
font-size:14px;font-weight:600;
color:#083024;text-align:center;height:42px;
display:flex;align-items:center;justify-content:center;
box-shadow:0 3px 6px rgba(6,109,77,0.28);
border:2px solid rgba(6,109,77,0.35);
}

/* Report Content Boxes Large Font */
.objective-box,.report-box{
background:#ffffff;border-radius:10px;
padding:10px;border:2px solid rgba(6,109,77,0.35);
height:140px;overflow:auto;
box-shadow:0 3px 6px rgba(6,109,77,0.28);
}
.objective-title,.report-box-title{
font-size:15px;font-weight:700;text-align:center;color:#083024;
border-bottom:2px solid #ccd9d0;margin-bottom:6px;padding-bottom:4px;
}
.report-box-content{
font-size:15px;line-height:1.6;color:#000;
}

.report-row{
display:grid;grid-template-columns:1fr 1fr;
gap:12px;margin-bottom:12px;
}

/* Images */
.image-evidence-grid{
display:grid;grid-template-columns:1fr 1fr;
gap:10px;margin-top:8px;
}
.image-box{
height:130px;border:2px dashed #066d4d;border-radius:10px;
display:flex;align-items:center;justify-content:center;
color:#066d4d;font-size:12px;overflow:hidden;
}

/* Signature */
.signature-section{
margin-top:20px;display:grid;grid-template-columns:1fr 1fr;gap:20px;
}
.signature-box{text-align:center;font-size:13px;color:#083024;font-weight:700;}
.signature-line{
margin-top:8px;border-top:2px solid #083024;
width:80%;margin-inline:auto;margin-bottom:4px;
}

/* Footer */
.footer{
width:100%;background:#083024;color:#ffffff;
text-align:center;font-size:12px;padding:6px 0;margin-top:18px;
}

/* Mobile Improvements */
@media(max-width:600px){
textarea{height:160px;}
.report-row{grid-template-columns:1fr;}
}
</style>
</head>

<body>

<div class="btn-container">
<button class="main-btn" onclick="downloadPDF()">تنزيل PDF</button>
<button class="main-btn" onclick="sharePDFWhatsApp()">مشاركة واتساب</button>
</div>

<div class="container">

<label>إدارة التعليم</label>
<select id="education" oninput="updateReport()">
<option value="">اختر الإدارة</option>
<option>الإدارة العامة للتعليم بمنطقة مكة المكرمة</option>
<option>الإدارة العامة للتعليم بمنطقة الرياض</option>
<option>الإدارة العامة للتعليم بمنطقة المدينة المنورة</option>
<option>الإدارة العامة للتعليم بالمنطقة الشرقية</option>
<option>الإدارة العامة للتعليم بمنطقة القصيم</option>
<option>الإدارة العامة للتعليم بمنطقة عسير</option>
<option>الإدارة العامة للتعليم بمنطقة تبوك</option>
<option>الإدارة العامة للتعليم بمنطقة حائل</option>
<option>الإدارة العامة للتعليم بمنطقة الحدود الشمالية</option>
<option>الإدارة العامة للتعليم بمنطقة جازان</option>
<option>الإدارة العامة للتعليم بمنطقة نجران</option>
<option>الإدارة العامة للتعليم بمنطقة الباحة</option>
<option>الإدارة العامة للتعليم بمنطقة الجوف</option>
<option>الإدارة العامة للتعليم بمحافظة الأحساء</option>
<option>الإدارة العامة للتعليم بمحافظة الطائف</option>
<option>الإدارة العامة للتعليم بمحافظة جدة</option>
</select>

<label>الفصل الدراسي</label>
<select id="term" oninput="updateReport()">
<option value="">اختر الفصل</option>
<option>الفصل الدراسي الأول</option>
<option>الفصل الدراسي الثاني</option>
</select>

<label>اسم التقرير</label>
<select id="reportType" oninput="updateReport()">
<option>تقرير نشاط إثرائي</option>
</select>

<label>الصف</label>
<input id="grade" oninput="updateReport()">

<label>المادة</label>
<input id="subject" oninput="updateReport()">

<label>المستهدفون</label>
<input id="target" oninput="updateReport()">

<label>عدد الحضور</label>
<input id="count" oninput="updateReport()">

<label>مكان التنفيذ</label>
<input id="place" oninput="updateReport()">

<script>
const autoTexts={
goal:[
"تنمية مهارات الطلاب من خلال أنشطة تعليمية تفاعلية.",
"تحفيز الطلاب على المشاركة الإيجابية وتعزيز الشعور بالإنجاز.",
"تعزيز السلوك الإيجابي وقيم التعلم التعاوني.",
"تطوير مهارات التفكير الإبداعي لدى الطلاب.",
"رفع دافعية الطلاب من خلال توظيف استراتيجيات حديثة."
],
summary:[
"تم تنفيذ نشاط إثرائي داخل الصف بمشاركة جميع الطلاب.",
"استخدام وسائل تعليمية محفزة عزّزت التعلم.",
"تفاعل الطلاب بشكل ممتاز أثناء النشاط.",
"استخدام أساليب متنوعة لتوضيح المفاهيم.",
"الطلاب أظهروا تفهماً واضحاً للموضوع."
],
steps:[
"شرح الفكرة الأساسية ثم تقسيم الطلاب إلى مجموعات.",
"تطبيق نشاط عملي لتعزيز المفهوم.",
"مناقشة مشاركات الطلاب وتقديم تغذية راجعة.",
"توظيف التقنيات الحديثة أثناء الدرس.",
"تحفيز الطلاب عبر التنافس الإيجابي."
],
strategies:[
"التعلم التعاوني والعمل ضمن مجموعات.",
"العصف الذهني لتوليد الأفكار.",
"التعلم النشط القائم على الطلبة.",
"استخدام الوسائل التعليمية المحفزة.",
"تنويع طرق التدريس بما يناسب الفروق الفردية."
],
strengths:[
"تفاعل ممتاز مع النشاط.",
"تحقيق أهداف الدرس بدقة.",
"تنوع في طرق التدريس.",
"التزام وانضباط داخل الصف.",
"تحسن واضح لدى الطلاب."
],
improve:[
"زيادة الأنشطة الرقمية.",
"إتاحة وقت أكبر للنقاش.",
"دعم الطلاب المحتاجين بشكل إضافي.",
"تنويع أدوات التقويم.",
"تحسين تعزيز السلوك الإيجابي."
],
recomm:[
"الاستمرار في تطبيق الأنشطة الإثرائية.",
"زيادة دمج التقنية في الدروس القادمة.",
"إتاحة فرص مشاركة أكبر لجميع الطلاب.",
"تعزيز التعاون بين الطلاب داخل الصف.",
"استمرار المتابعة الأكاديمية للطلاب."
]
};
</script>

<label>الهدف التربوي</label>
<textarea id="goal" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('goal',1)">1</button>
<button onclick="autoFill('goal',2)">2</button>
<button onclick="autoFill('goal',3)">3</button>
<button onclick="autoFill('goal',4)">4</button>
<button onclick="autoFill('goal',5)">5</button>
</div>

<label>نبذة مختصرة</label>
<textarea id="summary" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('summary',1)">1</button>
<button onclick="autoFill('summary',2)">2</button>
<button onclick="autoFill('summary',3)">3</button>
<button onclick="autoFill('summary',4)">4</button>
<button onclick="autoFill('summary',5)">5</button>
</div>

<label>إجراءات التنفيذ</label>
<textarea id="steps" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('steps',1)">1</button>
<button onclick="autoFill('steps',2)">2</button>
<button onclick="autoFill('steps',3)">3</button>
<button onclick="autoFill('steps',4)">4</button>
<button onclick="autoFill('steps',5)">5</button>
</div>

<label>الاستراتيجيات</label>
<textarea id="strategies" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('strategies',1)">1</button>
<button onclick="autoFill('strategies',2)">2</button>
<button onclick="autoFill('strategies',3)">3</button>
<button onclick="autoFill('strategies',4)">4</button>
<button onclick="autoFill('strategies',5)">5</button>
</div>

<label>نقاط القوة</label>
<textarea id="strengths" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('strengths',1)">1</button>
<button onclick="autoFill('strengths',2)">2</button>
<button onclick="autoFill('strengths',3)">3</button>
<button onclick="autoFill('strengths',4)">4</button>
<button onclick="autoFill('strengths',5)">5</button>
</div>

<label>نقاط التحسين</label>
<textarea id="improve" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('improve',1)">1</button>
<button onclick="autoFill('improve',2)">2</button>
<button onclick="autoFill('improve',3)">3</button>
<button onclick="autoFill('improve',4)">4</button>
<button onclick="autoFill('improve',5)">5</button>
</div>

<label>التوصيات</label>
<textarea id="recomm" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('recomm',1)">1</button>
<button onclick="autoFill('recomm',2)">2</button>
<button onclick="autoFill('recomm',3)">3</button>
<button onclick="autoFill('recomm',4)">4</button>
<button onclick="autoFill('recomm',5)">5</button>
</div>

<label>الصورة 1</label>
<input type="file" accept="image/*" onchange="loadImage(this,'imgBox1')">

<label>الصورة 2</label>
<input type="file" accept="image/*" onchange="loadImage(this,'imgBox2')">

</div>

<div id="report-content">

<div class="header">
<img src="https://i.ibb.co/1fc5gB6v/9-C92-E57-B-23-FA-479-D-A024-1-D5-F871-B4-F8-D.png">
<div class="header-right-top" id="educationBox"></div>
<div class="header-right-bottom">مدرسة سعيد بن العاص</div>
<div class="header-left-bottom"><span id="gDate"></span> | <span id="hDate"></span></div>
</div>

<div class="page">

<div class="info-grid">
<div class="info-box" id="termBox"></div>
<div class="info-box" id="gradeBox"></div>
<div class="info-box" id="subjectBox"></div>
<div class="info-box" id="reportTypeBox"></div>
<div class="info-box" id="targetBox"></div>
<div class="info-box" id="countBox"></div>
<div class="info-box" id="placeBox"></div>
</div>

<div class="objective-box">
<div class="objective-title">الهدف التربوي</div>
<div class="report-box-content" id="goalBox"></div>
</div>

<div class="report-row">
<div class="report-box">
<div class="report-box-title">نبذة مختصرة</div>
<div class="report-box-content" id="summaryBox"></div>
</div>
<div class="report-box">
<div class="report-box-title">إجراءات التنفيذ</div>
<div class="report-box-content" id="stepsBox"></div>
</div>
</div>

<div class="report-row">
<div class="report-box">
<div class="report-box-title">الاستراتيجيات</div>
<div class="report-box-content" id="strategiesBox"></div>
</div>
<div class="report-box">
<div class="report-box-title">نقاط القوة</div>
<div class="report-box-content" id="strengthsBox"></div>
</div>
</div>

<div class="report-row">
<div class="report-box">
<div class="report-box-title">نقاط التحسين</div>
<div class="report-box-content" id="improveBox"></div>
</div>
<div class="report-box">
<div class="report-box-title">التوصيات</div>
<div class="report-box-content" id="recommBox"></div>
</div>
</div>

<div class="image-evidence-grid">
<div class="image-box" id="imgBox1">صورة توثيقية 1</div>
<div class="image-box" id="imgBox2">صورة توثيقية 2</div>
</div>

<div class="signature-section">
<div class="signature-box">
اسم المعلم: فهد الخالدي
<div class="signature-line"></div>
توقيع المعلم
</div>
<div class="signature-box">
مدير المدرسة: نايف اللحياني
<div class="signature-line"></div>
توقيع المدير
</div>
</div>

<div class="footer">وزارة التعليم – المملكة العربية السعودية</div>

</div>
</div>

<script>
function autoFill(field,i){
document.getElementById(field).value=autoTexts[field][i-1];
updateReport();
}

function updateReport(){
educationBox.innerText=education.value;
termBox.innerText=term.value;
reportTypeBox.innerText=reportType.value;
gradeBox.innerText=grade.value;
subjectBox.innerText=subject.value;
targetBox.innerText=target.value;
countBox.innerText=count.value;
placeBox.innerText=place.value;
goalBox.innerText=goal.value;
summaryBox.innerText=summary.value;
stepsBox.innerText=steps.value;
strategiesBox.innerText=strategies.value;
strengthsBox.innerText=strengths.value;
improveBox.innerText=improve.value;
recommBox.innerText=recomm.value;
}

function loadImage(input,target){
let file=input.files[0];
let r=new FileReader();
r.onload=()=>document.getElementById(target).innerHTML=
`<img src="${r.result}" style="width:100%;height:100%;object-fit:cover">`;
r.readAsDataURL(file);
}

function downloadPDF(){
let element=document.getElementById("report-content");
html2pdf().set({
margin:0,
filename:"report.pdf",
image:{type:"jpeg",quality:1},
html2canvas:{scale:3,scrollY:0,useCORS:true},
jsPDF:{unit:"mm",format:"a4",orientation:"portrait"}
}).from(element).save();
}

async function sharePDFWhatsApp(){
let element=document.getElementById("report-content");
let opt={
margin:0,
image:{type:"jpeg",quality:1},
html2canvas:{scale:3,scrollY:0,useCORS:true},
jsPDF:{unit:"mm",format:"a4",orientation:"portrait"}
};
let blob=await html2pdf().from(element).set(opt).outputPdf("blob");
let file=new File([blob],"report.pdf",{type:"application/pdf"});

if(navigator.canShare && navigator.canShare({files:[file]})){
navigator.share({files:[file],title:"تقرير إشرافي"});
}else{
let url=URL.createObjectURL(blob);
window.open(`https://wa.me/?text=${encodeURIComponent(url)}`);
}
}

async function loadDates(){
let g=new Date();
g.findate=`${g.getDate()}-${g.getMonth()+1}-${g.getFullYear()}`;
gDate.innerText=g.findate;
let r=await fetch(`https://api.aladhan.com/v1/gToH?date=${g.findate}`);
let d=await r.json();
hDate.innerText=`${d.data.hijri.day}-${d.data.hijri.month.number}-${d.data.hijri.year}`;
}
loadDates();
</script>

</body>
</html>