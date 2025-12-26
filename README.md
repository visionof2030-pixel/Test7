<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>أداة إصدار التقارير والشواهد</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap');
*{margin:0;padding:0;box-sizing:border-box;}
html,body{font-family:'Cairo',sans-serif;background:#ffffff;direction:rtl;}
.container{max-width:900px;margin:auto;padding:10px;}

label{font-size:13px;font-weight:700;margin-top:10px;display:block;color:#083024;}
input,select,textarea{
width:100%;padding:7px;margin-top:4px;
border:1px solid #066d4d;border-radius:6px;font-size:12px;
}
textarea{height:75px;resize:none;}

.auto-buttons{display:flex;gap:5px;margin-top:5px;}
.auto-buttons button{
padding:4px 7px;background:#0a5c58;border:none;color:#fff;
cursor:pointer;border-radius:3px;font-size:10px;
}

/* زرار PDF واتساب */
.btn-container{
text-align:center;padding:10px;background:#f5f5f5;
position:sticky;top:0;z-index:10;
display:flex;gap:10px;justify-content:center;
}
button.main-btn{
background:#066d4d;color:#fff;border:none;
padding:10px 16px;font-size:14px;border-radius:6px;cursor:pointer;
}
button.main-btn:hover{background:#05523a;}

/* التقرير */
#report-content{margin-top:25px;}

.header{
width:100%;height:125px;margin-top:15px;
position:relative;background:#083024;
display:flex;align-items:center;justify-content:center;
border-radius:6px;
}
.header img{width:150px;opacity:.95;}
.header-right-top,.header-right-bottom,.header-left-bottom{
position:absolute;color:#ffffff;font-weight:700;
}
.header-right-top{top:6px;right:12px;font-size:12px;}
.header-right-bottom{bottom:6px;right:12px;font-size:11px;}
.header-left-bottom{bottom:6px;left:12px;font-size:11px;}

.page{max-width:830px;padding:10px;margin:auto;}

.info-grid{
display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
gap:6px;margin-bottom:12px;margin-top:10px;
}
.info-box{
background:#e8f2ee;border-radius:8px;
font-size:11px;font-weight:600;
color:#083024;text-align:center;
height:42px;
display:flex;align-items:center;justify-content:center;
border:1px solid rgba(6,109,77,0.35);
}

.objective-box,.report-box{
background:#ffffff;border-radius:8px;
padding:6px;
border:1px solid rgba(6,109,77,0.35);
height:110px;overflow:auto;margin-bottom:8px;
}

.objective-title,.report-box-title{
font-size:12px;font-weight:700;text-align:center;color:#083024;
border-bottom:1px solid #ccd9d0;margin-bottom:4px;padding-bottom:3px;
}

.report-row{
display:grid;grid-template-columns:1fr 1fr;
gap:10px;margin-bottom:8px;
}

.image-evidence-grid{
display:grid;grid-template-columns:1fr 1fr;
gap:8px;margin-top:8px;
}
.image-box{
height:200px;border:1px dashed #066d4d;border-radius:8px;
display:flex;align-items:center;justify-content:center;
color:#066d4d;font-size:10px;overflow:hidden;
}

.signature-section{
margin-top:18px;display:grid;grid-template-columns:1fr 1fr;gap:20px;
}
.signature-box{
text-align:center;font-size:11px;color:#083024;font-weight:600;
}
.signature-line{
margin-top:8px;border-top:1px solid #083024;
width:80%;margin-inline:auto;margin-bottom:4px;
}

.footer{
width:100%;background:#083024;color:#ffffff;
text-align:center;font-size:10px;padding:4px 0;margin-top:18px;
}
</style>
</head>

<body>

<div class="container">
<div class="btn-container">
<button class="main-btn" onclick="downloadPDF()">تنزيل ملف PDF</button>
<button class="main-btn" onclick="sharePDFWhatsApp()">مشاركة واتساب</button>
</div>

<!-- أداة الإدخال -->
<label>إدارة التعليم</label>
<select id="education" onchange="updateReport()">
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
<select id="term" onchange="updateReport()">
<option value="">اختر الفصل</option>
<option>الفصل الدراسي الأول</option>
<option>الفصل الدراسي الثاني</option>
</select>

<label>اسم التقرير</label>
<select id="reportType" onchange="updateReport()">
<option value="">اختر نوع التقرير</option>
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
<input type="file" id="img1" accept="image/*" onchange="loadImage(this,'imgBox1')">

<label>الصورة 2</label>
<input type="file" id="img2" accept="image/*" onchange="loadImage(this,'imgBox2')">


<!-- قالب التقرير -->
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
<div id="goalBox"></div>
</div>

<div class="report-row">
<div class="report-box">
<div class="report-box-title">نبذة مختصرة</div>
<div id="summaryBox"></div>
</div>
<div class="report-box">
<div class="report-box-title">إجراءات التنفيذ</div>
<div id="stepsBox"></div>
</div>
</div>

<div class="report-row">
<div class="report-box">
<div class="report-box-title">الاستراتيجيات</div>
<div id="strategiesBox"></div>
</div>
<div class="report-box">
<div class="report-box-title">نقاط القوة</div>
<div id="strengthsBox"></div>
</div>
</div>

<div class="report-row">
<div class="report-box">
<div class="report-box-title">نقاط التحسين</div>
<div id="improveBox"></div>
</div>
<div class="report-box">
<div class="report-box-title">التوصيات</div>
<div id="recommBox"></div>
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

</div>

<script>
const autoTexts={
goal:[
"تنمية مهارات الطلاب من خلال أنشطة تعليمية تفاعلية.",
"تحفيز الطلاب للمشاركة الفاعلة والاندماج في التعلم.",
"تعزيز القيم التربوية والسلوكية داخل البيئة المدرسية.",
"تطوير مهارات التفكير العليا لدى الطلاب.",
"رفع دافعية الطلاب للتعلم من خلال التعزيز المستمر."
],
summary:[
"تم تنفيذ النشاط داخل الصف بمشاركة جميع الطلاب وبأساليب محفزة.",
"تم توظيف أدوات تعليمية لتعزيز مشاركة الطلاب داخل الصف.",
"شهد الدرس تفاعلًا إيجابيًا بين المعلم والطلاب.",
"ركز النشاط على ترسيخ المفاهيم وربطها بواقع الطلاب.",
"تم تقديم الشرح بطريقة مبسطة وسهلة للطلاب."
],
steps:[
"شرح المفهوم ثم توزيع الطلاب إلى مجموعات للتطبيق العملي.",
"عرض أمثلة واقعية ومناقشتها بهدف ترسيخ الفهم.",
"تحفيز الطلاب على المشاركة من خلال أسئلة تفاعلية.",
"استخدام أدوات تعليمية متنوعة لتعزيز الفهم.",
"توظيف التقنية في تقديم محتوى الدرس."
],
strategies:[
"التعلم التعاوني داخل المجموعات.",
"التعلم النشط باستخدام المناقشات التفاعلية.",
"التعلم باللعب لتحفيز المشاركة.",
"تنوع الأنشطة الصفية.",
"استراتيجيات التمايز لتلبية الفروق الفردية."
],
strengths:[
"تفاعل كبير من الطلاب مع النشاط.",
"تحقيق أهداف الدرس بشكل متميز.",
"استخدام أدوات تعليمية مؤثرة.",
"انضباط وتنظيم عالي داخل الصف.",
"تحسن ملحوظ في مستوى الطلاب."
],
improve:[
"زيادة استخدام التعلم الرقمي.",
"التوسع في الأنشطة التطبيقية.",
"تعزيز مشاركة الطالب الضعيف.",
"تخصيص وقت إضافي للنقاش.",
"تنويع أساليب التقويم."
],
recomm:[
"الاستمرار في تطبيق الاستراتيجيات الفاعلة.",
"إتاحة فرص مشاركة أكبر لجميع الطلاب.",
"تطوير الوسائل التعليمية المستخدمة.",
"متابعة المستوى الأكاديمي للطلاب.",
"استمرار التحفيز والدعم الطلابي."
]
};

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
let reader=new FileReader();
reader.onload=function(){
document.getElementById(target).innerHTML='<img src="'+reader.result+'" style="width:100%;height:100%;object-fit:cover;">';
}
reader.readAsDataURL(file);
}

function downloadPDF(){
html2pdf().set({
margin:0,
filename:"report.pdf",
image:{type:"jpeg",quality:1},
html2canvas:{scale:3,useCORS:true},
jsPDF:{unit:"mm",format:"a4",orientation:"portrait"}
}).from(document.getElementById("report-content")).save();
}

async function sharePDFWhatsApp(){
const el=document.getElementById("report-content");
const worker=html2pdf().set({
margin:0,filename:"report.pdf",
image:{type:"jpeg",quality:1},
html2canvas:{scale:3,useCORS:true},
jsPDF:{unit:"mm",format:"a4",orientation:"portrait"}
}).from(el);
const blob=await worker.outputPdf("blob");
const file=new File([blob],"report.pdf",{type:"application/pdf"});
if(navigator.share){
navigator.share({title:"تقرير إشرافي",files:[file]});
}else{
worker.save();
}
}

async function loadDates(){
let g=new Date(),gy=g.getFullYear(),gm=g.getMonth()+1,gd=g.getDate();
document.getElementById("gDate").innerText=`${gd}-${gm}-${gy}`;
let r=await fetch(`https://api.aladhan.com/v1/gToH?date=${gd}-${gm}-${gy}`);
let d=await r.json(),h=d.data.hijri;
document.getElementById("hDate").innerText=`${h.day}-${h.month.number}-${h.year}`;
}
loadDates();
</script>

</body>
</html>