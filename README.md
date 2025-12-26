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

/* FORM */
.container{max-width:900px;margin:auto;padding:15px;margin-bottom:30px;}
h2{text-align:center;margin-bottom:15px;color:#083024;}
label{font-size:13px;font-weight:700;margin-top:10px;display:block;color:#083024;}
input,select,textarea{
width:100%;padding:8px;margin-top:4px;
border:1px solid #066d4d;border-radius:6px;font-size:12px;
}
textarea{height:80px;resize:none;}
button{
margin-top:18px;background:#066d4d;color:#fff;border:none;
padding:12px 18px;font-size:15px;border-radius:6px;cursor:pointer;width:100%;
}
button:hover{background:#05523a;}
.auto-buttons{display:flex;gap:5px;margin-top:5px;}
.auto-buttons button{
padding:5px;background:#0a5c58;border:none;color:#fff;
cursor:pointer;border-radius:4px;font-size:10px;
}

/* REPORT */
.btn-container{
text-align:center;padding:10px;background:#f5f5f5;
position:fixed;top:0;left:0;width:100%;z-index:10;
display:flex;gap:10px;justify-content:center;
}
.btn-container button{
background:#066d4d;color:#fff;border:none;
padding:10px 25px;font-size:15px;border-radius:6px;cursor:pointer;
}
.btn-container button:hover{background:#05523a;}
@media print{.btn-container{display:none;}}

#report-content{display:none;}

.header{
width:100%;height:135px;margin-top:60px;
position:relative;overflow:hidden;
background:#083024;
display:flex;align-items:center;justify-content:center;
}
.header img{
position:relative;z-index:2;width:180px;opacity:.95;
}
.header-right-top,.header-right-bottom,.header-left-bottom{
position:absolute;color:#ffffff;font-weight:700;
}
.header-right-top{top:6px;right:12px;font-size:13px;}
.header-right-bottom{bottom:6px;right:12px;font-size:12px;font-weight:600;}
.header-left-bottom{bottom:6px;left:12px;font-size:12px;font-weight:600;direction:ltr;text-align:left;}

.page{width:100%;max-width:830px;padding:10px;margin:auto;}

.info-grid{
display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
gap:6px;margin-bottom:12px;
}
.info-box{
background:#e8f2ee;border-radius:8px;
font-size:11px;font-weight:600;
color:#083024;text-align:center;
height:42px;
display:flex;align-items:center;justify-content:center;
box-shadow:0 3px 6px rgba(6,109,77,0.28);
border:1px solid rgba(6,109,77,0.35);
}

.objective-box{
background:#f3f9f6;
border:1px solid rgba(6,109,77,0.35);
padding:6px 10px;border-radius:8px;margin-bottom:10px;
height:110px;overflow:auto;
box-shadow:0 3px 6px rgba(6,109,77,0.28);
}
.objective-title{
text-align:center;font-size:13px;font-weight:700;color:#083024;
border-bottom:1px solid #066d4d;padding-bottom:3px;margin-bottom:3px;
}

.report-row{
display:grid;grid-template-columns:1fr 1fr;
gap:10px;margin-bottom:10px;
}
.report-box{
background:#ffffff;border-radius:8px;
padding:6px;
border:1px solid rgba(6,109,77,0.35);
height:115px;overflow:auto;
box-shadow:0 3px 6px rgba(6,109,77,0.28);
}
.report-box-title{
font-size:12px;font-weight:700;text-align:center;color:#083024;
border-bottom:1px solid #ccd9d0;margin-bottom:4px;padding-bottom:3px;
}
.report-box-content{font-size:10px;line-height:1.3;}

.image-evidence-grid{
display:grid;grid-template-columns:1fr 1fr;
gap:8px;margin-top:8px;
}
.image-box{
height:200px;border:1px dashed #066d4d;border-radius:8px;
display:flex;align-items:center;justify-content:center;
color:#066d4d;font-size:10px;overflow:hidden;
box-shadow:0 3px 6px rgba(6,109,77,0.28);
}

.signature-section{
margin-top:20px;display:grid;grid-template-columns:1fr 1fr;gap:20px;
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
<h2>أداة إصدار التقارير والشواهد</h2>

<label>إدارة التعليم</label>
<select id="education">
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
<select id="term">
<option value="">اختر الفصل الدراسي</option>
<option>الفصل الدراسي الأول</option>
<option>الفصل الدراسي الثاني</option>
</select>

<label>التقرير</label>
<select id="reportType">
<option value="">اختر نوع التقرير</option>
<option>تقرير نشاط إثرائي</option>
<option>تقرير خطة علاجية</option>
<option>تقرير تكريم المتميزين</option>
<option>تقرير أنشطة صفية</option>
<option>تقرير خطة أسبوعية</option>
<option>تقرير توزيع المنهج</option>
<option>تقرير حصة النشاط</option>
<option>تقرير تنفيذ إذاعة مدرسية</option>
<option>تقرير تبادل الزيارات</option>
<option>تقرير مجتمعات التعلم</option>
<option>تقرير تنفيذ درس تطبيقي</option>
<option>تقرير حضور دورات وورش تدريبية</option>
<option>تقرير التواصل مع ولي الأمر</option>
<option>تقرير إشعار ولي الأمر عن مستوى ابنه</option>
<option>تقرير حضور اجتماع أولياء الأمور</option>
<option>تقرير تفعيل الخطة الاسبوعية</option>
<option>تقرير درس تم تنفيذه</option>
<option>تقرير تعليم تعاوني بين الطلاب</option>
<option>تقرير تصنيف الطلاب</option>
<option>تقرير تحفيز الطلاب</option>
<option>تقرير لكشف المتابعة</option>
<option>تقرير توزيع وقت الحصة</option>
<option>تقرير تنفيذ اختبار تحسن</option>
<option>تقرير المشاركات بين الطلاب</option>
<option>تقرير سجل الخطط العلاجية</option>
<option>تقرير سجل رعاية الموهوبين</option>
<option>تقرير تفعيل المنصات التعليمية</option>
<option>تقرير المجتمعات المهنية</option>
<option>تقرير الورش التدريبية التي قدمتها</option>
<option>تقرير الاشراف اليومي</option>
<option>تقرير الاحتفال باليوم الوطني</option>
<option>تقرير المبادرات والابتكار</option>
<option>تقرير حل مشكلة تربوية</option>
<option>تقرير توظيف الذكاء الاصطناعي</option>
<option>تقرير الفصول المقلوبة</option>
<option>تقرير تطوير البيئة الصفية</option>
<option>تقرير الوسائل التعليمية المبتكرة</option>
<option>تقرير المناوبة والفسحة</option>
<option>تقرير سجل التواصل مع اولياء الامور</option>
<option>تقارير الجرد ( للمختبرات وغرف المصادر)</option>
<option>تقرير ادارة الازمات</option>
<option>تقرير نقل أثر التدريب</option>
<option>تقرير المعلم الصغير</option>
<option>تقرير ادارة الاجتماعات ( للمدراء والمشرفين )</option>
<option>تقرير الاختبارات الذكية</option>
<option>تقرير المحتوى الرقمي المنتج</option>
<option>تقرير تعزيز السلوك الايجابي</option>
<option>تقرير سجل الدرجات الالكتروني</option>
<option>تقرير مقارنة السلاسل الزمنية</option>
<option>تقرير سجل  التغذية الراجعة من الطلاب</option>
<option>تقرير البحث الاجرائي</option>
<option>تقرير معرفة الميول والاتجاهات</option>
<option>تقرير عضوية لجنة التميز والجودة</option>
<option>تقرير عضوية لجنة التدقيق</option>
<option>تقرير رعاية الطلاب المتأخرين دراسيا</option>
<option>تقرير دراسة حالة</option>
<option>تقرير تحليل النتائج</option>
<option>تقرير تفعيل حصص النشاط</option>
<option>تقرير التدريب على الاختبارات المعيارية</option>
<option>تقرير مبادرة تطوعية</option>
</select>

<label>الصف</label>
<input id="grade">

<label>المادة</label>
<input id="subject">

<label>المستهدفون</label>
<input id="target">

<label>عدد الحضور</label>
<input id="count">

<label>مكان التنفيذ</label>
<input id="place">

<label>الهدف التربوي</label>
<textarea id="goal"></textarea>

<label>نبذة مختصرة</label>
<textarea id="summary"></textarea>

<label>إجراءات التنفيذ</label>
<textarea id="steps"></textarea>

<label>الاستراتيجيات</label>
<textarea id="strategies"></textarea>

<label>نقاط القوة</label>
<textarea id="strengths"></textarea>

<label>نقاط التحسين</label>
<textarea id="improve"></textarea>

<label>التوصيات</label>
<textarea id="recomm"></textarea>

<label>الصورة الأولى</label>
<input type="file" id="img1" accept="image/*">

<label>الصورة الثانية</label>
<input type="file" id="img2" accept="image/*">

<button onclick="showReport()">عرض التقرير</button>
</div>


<div id="report-content">

<div class="btn-container">
<button onclick="downloadPDF()">تنزيل ملف PDF</button>
<button onclick="sharePDFWhatsApp()">مشاركة عبر واتساب</button>
</div>

<div class="header">
<img src="https://i.ibb.co/1fc5gB6v/9-C92-E57-B-23-FA-479-D-A024-1-D5-F871-B4-F8-D.png">
<div class="header-right-top" id="educationBox">إدارة التعليم</div>
<div class="header-right-bottom" id="reportTypeBox">عنوان التقرير</div>
<div class="header-left-bottom"><span id="gDate"></span> | <span id="hDate"></span></div>
</div>

<div class="page">

<div class="info-grid">
<div class="info-box" id="termBox"></div>
<div class="info-box" id="gradeBox"></div>
<div class="info-box" id="subjectBox"></div>
<div class="info-box" id="reportNameBox"></div>
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
<div class="image-box">
<img id="image1Box" style="width:100%;height:100%;object-fit:cover;">
</div>
<div class="image-box">
<img id="image2Box" style="width:100%;height:100%;object-fit:cover;">
</div>
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
function showReport(){
document.querySelector(".container").style.display="none";
document.getElementById("report-content").style.display="block";

document.getElementById("educationBox").innerText=education.value;
document.getElementById("reportTypeBox").innerText=reportType.value;
document.getElementById("reportNameBox").innerText=reportType.value;
document.getElementById("termBox").innerText=term.value;
document.getElementById("gradeBox").innerText=grade.value;
document.getElementById("subjectBox").innerText=subject.value;
document.getElementById("targetBox").innerText=target.value;
document.getElementById("countBox").innerText=count.value;
document.getElementById("placeBox").innerText=place.value;

document.getElementById("goalBox").innerText=goal.value;
document.getElementById("summaryBox").innerText=summary.value;
document.getElementById("stepsBox").innerText=steps.value;
document.getElementById("strategiesBox").innerText=strategies.value;
document.getElementById("strengthsBox").innerText=strengths.value;
document.getElementById("improveBox").innerText=improve.value;
document.getElementById("recommBox").innerText=recomm.value;

let i1=img1.files[0];
let i2=img2.files[0];
if(i1){
let r1=new FileReader();
r1.onload=()=>{image1Box.src=r1.result;}
r1.readAsDataURL(i1);
}
if(i2){
let r2=new FileReader();
r2.onload=()=>{image2Box.src=r2.result;}
r2.readAsDataURL(i2);
}

loadDates();
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
</script>

</body>
</html>