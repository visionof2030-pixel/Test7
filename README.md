<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>أداة إصدار التقارير والشواهد</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap');
*{margin:0;padding:0;box-sizing:border-box;}
html,body{font-family:'Cairo',sans-serif;background:#ffffff;direction:rtl;overflow-x:hidden;}
.container{max-width:950px;margin:auto;padding:15px;}

.input-section {
background: #f8fdfb;padding: 15px;border-radius: 10px;margin-top: 10px;border: 1px solid #e0f0ea;
}
label{font-size:15px;font-weight:700;margin-top:15px;display:block;color:#083024;}
input,select,textarea{
width:100%;padding:12px;margin-top:6px;border:2px solid #066d4d;border-radius:8px;font-size:15px;background:#ffffff;
}
textarea{height:85px;resize:none;font-size: 16px !important;line-height: 1.7;}

.auto-buttons{display:flex;gap:8px;margin-top:8px;flex-wrap:wrap;}
.auto-buttons button{
padding:8px 12px;background:#066d4d;border:none;color:#fff;cursor:pointer;border-radius:5px;
font-size:13px;font-weight:bold;flex:1;min-width:60px;
}

.btn-container{
text-align:center;padding:12px;background:#f5f5f5;position:fixed;top:0;left:0;width:100%;z-index:20;
display:flex;gap:10px;justify-content:center;flex-wrap:wrap;box-shadow:0 3px 6px rgba(0,0,0,0.25);
}
button.main-btn{
background:#066d4d;color:#fff;border:none;padding:12px 25px;font-size:15px;border-radius:8px;cursor:pointer;
flex:1;min-width:140px;max-width:200px;
}
#report-content{margin-top:90px;width:100%;}

.header{
width:100%;height:135px;margin-top:20px;position:relative;overflow:hidden;background:#083024;
display:flex;align-items:center;justify-content:center;
}
.header img{width:180px;opacity:.95;}
.header-right-top,.header-right-bottom,.header-left-bottom{
position:absolute;color:#ffffff;font-weight:700;
}
.header-right-top{top:6px;right:12px;font-size:13px;}
.header-right-bottom{bottom:6px;right:12px;font-size:12px;font-weight:600;}
.header-left-bottom{
bottom:6px;left:12px;font-size:12px;font-weight:600;direction:ltr;
text-align:center;display:flex;flex-direction:column;
}

.page{width:100%;max-width:830px;padding:10px;margin:auto;}

.info-grid{
display:grid;grid-template-columns:repeat(4,1fr);gap:4px;margin-bottom:4px;
}
.info-grid2{
display:grid;grid-template-columns:repeat(3,1fr);gap:4px;margin-bottom:8px;
}

.info-box{
background:#e8f2ee;border-radius:6px;height:32px;overflow:hidden;
box-shadow:0 2px 4px rgba(6,109,77,0.2);border:1px solid rgba(6,109,77,0.3);
display:flex;flex-direction:column;justify-content:center;align-items:center;
padding:1px;
}
.info-title{font-size:9px;font-weight:700;color:#083024;margin-bottom:0;text-align:center;line-height:1;}
.info-value{font-size:10px;font-weight:700;color:#000000;text-align:center;white-space:nowrap;line-height:1;}

.objective-box{
background:#f3f9f6;border:1px solid rgba(6,109,77,0.35);padding:6px 10px;border-radius:8px;margin-bottom:10px;
height:110px;overflow:hidden;box-shadow:0 3px 6px rgba(6,109,77,0.28);}
.objective-title{font-size:14px;font-weight:700;color:#083024;text-align:center;border-bottom:1px solid #066d4d;margin-bottom:3px;}
.objective-content{font-size:16px;line-height:1.7;color:#000000;overflow:hidden;}

.report-row{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px;}
.report-box{
background:#ffffff;border-radius:8px;padding:6px;border:1px solid rgba(6,109,77,0.35);
height:115px;overflow:hidden;box-shadow:0 3px 6px rgba(6,109,77,0.28);}
.report-box-title{font-size:13px;font-weight:700;text-align:center;color:#083024;border-bottom:1px solid #ccd9d0;margin-bottom:4px;}
.report-box-content{font-size:15px;line-height:1.6;overflow:hidden;}

.image-evidence-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:8px;}
.image-box{
min-height:140px;max-height:140px;border:1px dashed #066d4d;border-radius:8px;
display:flex;align-items:center;justify-content:center;background:#ffffff;overflow:hidden;padding:4px;
}
.image-box img{max-width:100%;max-height:100%;object-fit:contain;}

.signature-section{margin-top:20px;display:grid;grid-template-columns:1fr 1fr;gap:20px;}
.signature-box{text-align:center;font-size:12px;color:#083024;font-weight:700;}
.signature-line{margin-top:8px;border-top:1px solid #083024;width:80%;margin:auto;margin-bottom:4px;}

.footer{text-align:center;font-size:10px;padding:4px 0;margin-top:18px;background:#083024;color:#fff;}
</style>
</head>

<body>
<div class="btn-container">
<button class="main-btn" onclick="downloadPDF()">تنزيل PDF</button>
<button class="main-btn" onclick="sharePDFWhatsApp()">مشاركة واتساب</button>
</div>

<div class="container">
<div class="input-section">

<div class="input-group">
<label>إدارة التعليم</label>
<select id="education" oninput="updateReport()">
<option value="">اختر الإدارة</option>
<option>الإدارة العامة للتعليم بمنطقة مكة المكرمة</option>
<option>الإدارة العامة للتعليم بمحافظة جدة</option>
</select>

<label>الفصل الدراسي</label>
<select id="term" oninput="updateReport()">
<option value="">اختر الفصل</option>
<option>الفصل الدراسي الأول</option>
<option>الفصل الدراسي الثاني</option>
</select>
</div>

<div class="input-group">
<label>اسم التقرير</label>
<select id="reportType" oninput="updateReport()">
<option>تقرير نشاط إثرائي</option>
</select>

<label>الصف</label>
<input id="grade" oninput="updateReport()" placeholder="مثال: 5/3">
</div>

<div class="input-group">
<label>المادة</label>
<input id="subject" oninput="updateReport()">

<label>المستهدفون</label>
<input id="target" oninput="updateReport()">
</div>

<div class="input-group">
<label>عدد الحضور</label>
<input id="count" oninput="updateReport()">

<label>مكان التنفيذ</label>
<input id="place" oninput="updateReport()">
</div>

<label>اسم المعلم</label>
<input id="teacher" oninput="updateReport()" placeholder="مثال: فهد الخالدي">

<label>اسم المدير</label>
<input id="principal" oninput="updateReport()" placeholder="مثال: نايف اللحياني">

<script>
const autoTexts={
goal:[
"تنمية مهارات الطلاب من خلال أنشطة تعليمية عملية تعزز التفكير.",
"تعزيز تفاعل الطلاب والمشاركة الإيجابية داخل الدرس.",
"رفع مستوى التحصيل باستخدام إستراتيجيات حديثة.",
"تنمية مهارات التعاون والعمل الجماعي.",
"دعم السلوك الإيجابي وتحفيز التعلم الذاتي."
],
summary:[
"تم تنفيذ النشاط داخل الصف بمشاركة الطلاب بكامل الحماس.",
"استخدمت وسائل تعليمية جذبت انتباه الطلاب.",
"كان التفاعل ممتازاً وتم فهم المفهوم بشكل واضح.",
"تنوعت أساليب الشرح والتطبيق مما أثرى الدرس.",
"أظهر الطلاب تحسناً واضحاً في مفهوم الدرس."
],
steps:[
"شرح المفهوم الرئيسي للنشاط.",
"تقسيم الطلاب إلى مجموعات للعمل التعاوني.",
"تنفيذ نشاط تطبيقي لتعميق الفهم.",
"مناقشة نتائج الطلاب وتقديم التغذية الراجعة.",
"توظيف التقنية في تعزيز المفهوم."
],
strategies:[
"التعلم النشط والاستقصاء الذاتي.",
"التعلم التعاوني والعمل الجماعي.",
"العصف الذهني وتوليد الأفكار.",
"استخدام بطاقات تعليمية محفزة.",
"تنويع طرق التدريس لمراعاة الفروق الفردية."
],
strengths:[
"تفاعل عالٍ من الطلاب.",
"تحقيق أهداف الدرس بنجاح.",
"تنوع في الأساليب المستخدمة.",
"انضباط داخل الصف.",
"تحسن ملحوظ لدى الطلاب."
],
improve:[
"زيادة استخدام الأنشطة الرقمية.",
"إعطاء وقت أطول للمناقشة.",
"تقديم دعم إضافي للطلاب المحتاجين.",
"تطوير أدوات التقويم المستخدمة.",
"تعزيز دور الطلاب في التعلم الذاتي."
],
recomm:[
"الاستمرار في تطبيق الأنشطة التفاعلية.",
"توظيف التقنية بشكل أكبر في الدروس القادمة.",
"إتاحة فرص مشاركة أكثر لجميع الطلاب.",
"تعزيز التواصل بين الطلاب داخل المجموعات.",
"المتابعة الدقيقة للتحصيل الدراسي."
]
};
function autoFill(field,i){
document.getElementById(field).value=autoTexts[field][i-1];
updateReport();
}
</script>

<label>الهدف التربوي</label>
<textarea id="goal" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('goal',1)">نص 1</button>
<button onclick="autoFill('goal',2)">نص 2</button>
<button onclick="autoFill('goal',3)">نص 3</button>
<button onclick="autoFill('goal',4)">نص 4</button>
<button onclick="autoFill('goal',5)">نص 5</button>
</div>

<label>نبذة مختصرة</label>
<textarea id="summary" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('summary',1)">نص 1</button>
<button onclick="autoFill('summary',2)">نص 2</button>
<button onclick="autoFill('summary',3)">نص 3</button>
<button onclick="autoFill('summary',4)">نص 4</button>
<button onclick="autoFill('summary',5)">نص 5</button>
</div>

<label>إجراءات التنفيذ</label>
<textarea id="steps" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('steps',1)">نص 1</button>
<button onclick="autoFill('steps',2)">نص 2</button>
<button onclick="autoFill('steps',3)">نص 3</button>
<button onclick="autoFill('steps',4)">نص 4</button>
<button onclick="autoFill('steps',5)">نص 5</button>
</div>

<label>الاستراتيجيات</label>
<textarea id="strategies" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('strategies',1)">نص 1</button>
<button onclick="autoFill('strategies',2)">نص 2</button>
<button onclick="autoFill('strategies',3)">نص 3</button>
<button onclick="autoFill('strategies',4)">نص 4</button>
<button onclick="autoFill('strategies',5)">نص 5</button>
</div>

<label>نقاط القوة</label>
<textarea id="strengths" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('strengths',1)">نص 1</button>
<button onclick="autoFill('strengths',2)">نص 2</button>
<button onclick="autoFill('strengths',3)">نص 3</button>
<button onclick="autoFill('strengths',4)">نص 4</button>
<button onclick="autoFill('strengths',5)">نص 5</button>
</div>

<label>نقاط التحسين</label>
<textarea id="improve" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('improve',1)">نص 1</button>
<button onclick="autoFill('improve',2)">نص 2</button>
<button onclick="autoFill('improve',3)">نص 3</button>
<button onclick="autoFill('improve',4)">نص 4</button>
<button onclick="autoFill('improve',5)">نص 5</button>
</div>

<label>التوصيات</label>
<textarea id="recomm" oninput="updateReport()"></textarea>
<div class="auto-buttons">
<button onclick="autoFill('recomm',1)">نص 1</button>
<button onclick="autoFill('recomm',2)">نص 2</button>
<button onclick="autoFill('recomm',3)">نص 3</button>
<button onclick="autoFill('recomm',4)">نص 4</button>
<button onclick="autoFill('recomm',5)">نص 5</button>
</div>

<label>الصورة 1</label>
<input type="file" accept="image/*" onchange="loadImage(this,'imgBox1')">
<label>الصورة 2</label>
<input type="file" accept="image/*" onchange="loadImage(this,'imgBox2')">

</div>
</div>

<div id="report-content">

<div class="header">
<img src="https://i.ibb.co/1fc5gB6v/9-C92-E57-B-23-FA-479-D-A024-1-D5-F871-B4-F8-D.png">
<div class="header-right-top" id="educationBox"></div>
<div class="header-right-bottom">مدرسة سعيد بن العاص</div>
<div class="header-left-bottom">
<span id="hDate"></span>
<span id="gDate"></span>
</div>
</div>

<div class="page">

<div class="info-grid">
<div class="info-box"><div class="info-title">الفصل</div><div class="info-value" id="termBox"></div></div>
<div class="info-box"><div class="info-title">الصف</div><div class="info-value" id="gradeBox"></div></div>
<div class="info-box"><div class="info-title">المادة</div><div class="info-value" id="subjectBox"></div></div>
<div class="info-box"><div class="info-title">اسم التقرير</div><div class="info-value" id="reportTypeBox"></div></div>
</div>

<div class="info-grid2">
<div class="info-box"><div class="info-title">المستهدفون</div><div class="info-value" id="targetBox"></div></div>
<div class="info-box"><div class="info-title">العدد</div><div class="info-value" id="countBox"></div></div>
<div class="info-box"><div class="info-title">مكان التنفيذ</div><div class="info-value" id="placeBox"></div></div>
</div>

<div class="objective-box"><div class="objective-title">الهدف التربوي</div><div class="objective-content" id="goalBox"></div></div>

<div class="report-row">
<div class="report-box"><div class="report-box-title">نبذة مختصرة</div><div class="report-box-content" id="summaryBox"></div></div>
<div class="report-box"><div class="report-box-title">إجراءات التنفيذ</div><div class="report-box-content" id="stepsBox"></div></div>
</div>

<div class="report-row">
<div class="report-box"><div class="report-box-title">الاستراتيجيات</div><div class="report-box-content" id="strategiesBox"></div></div>
<div class="report-box"><div class="report-box-title">نقاط القوة</div><div class="report-box-content" id="strengthsBox"></div></div>
</div>

<div class="report-row">
<div class="report-box"><div class="report-box-title">نقاط التحسين</div><div class="report-box-content" id="improveBox"></div></div>
<div class="report-box"><div class="report-box-title">التوصيات</div><div class="report-box-content" id="recommBox"></div></div>
</div>

<div class="image-evidence-grid">
<div class="image-box" id="imgBox1">صورة توثيقية 1</div>
<div class="image-box" id="imgBox2">صورة توثيقية 2</div>
</div>

<div class="signature-section">
<div class="signature-box">
<span id="teacherBox"></span>
<div class="signature-line"></div>
توقيع المعلم
</div>
<div class="signature-box">
<span id="principalBox"></span>
<div class="signature-line"></div>
توقيع المدير
</div>
</div>

<div class="footer">وزارة التعليم – المملكة العربية السعودية</div>

</div></div>

<script>
function updateReport(){
educationBox.innerText=education.value;
termBox.innerText=term.value;
reportTypeBox.innerText=reportType.value;
gradeBox.innerText=grade.value;
subjectBox.innerText=subject.value;
targetBox.innerText=target.value;
countBox.innerText=count.value;
placeBox.innerText=place.value;
teacherBox.innerText=teacher.value;
principalBox.innerText=principal.value;
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
let reader=new FileReader();
reader.onload=()=>document.getElementById(target).innerHTML=
`<img src="${reader.result}">`;
reader.readAsDataURL(file);
}

function downloadPDF(){
html2pdf().set({
margin:0,
filename:"report.pdf",
image:{type:"jpeg",quality:1},
html2canvas:{scale:3,scrollY:0,useCORS:true},
jsPDF:{unit:"mm",format:"a4",orientation:"portrait"}
}).from(document.getElementById("report-content")).save();
}

async function sharePDFWhatsApp(){
let blob=await html2pdf().from(document.getElementById("report-content")).set({
margin:0,image:{type:"jpeg",quality:1},
html2canvas:{scale:3,scrollY:0,useCORS:true},
jsPDF:{unit:"mm",format:"a4",orientation:"portrait"}
}).outputPdf("blob");
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
let gd=`${g.getDate()}-${g.getMonth()+1}-${g.getFullYear()}`;
gDate.innerText=gd;
let r=await fetch(`https://api.aladhan.com/v1/gToH?date=${gd}`);
let d=await r.json();
hDate.innerText=`${d.data.hijri.day}-${d.data.hijri.month.number}-${d.data.hijri.year} هـ`;
}
loadDates();
</script>

</body>
</html>