<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>أداة إصدار التقارير والشواهد</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap');
*{margin:0;padding:0;box-sizing:border-box;}
html,body{font-family:'Cairo',sans-serif;background:#ffffff;direction:rtl;}
.container{max-width:900px;margin:auto;padding:15px;}
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

.flex-row{display:flex;gap:10px;}
.flex-col{flex:1;}

.image-upload{margin-top:5px;font-size:12px;}

.auto-buttons{display:flex;gap:5px;margin-top:5px;}
.auto-buttons button{
padding:5px;background:#0a5c58;border:none;color:#fff;
cursor:pointer;border-radius:4px;font-size:10px;
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
<div class="auto-buttons">
<button type="button" onclick="autoFill('goal',1)">نص 1</button>
<button type="button" onclick="autoFill('goal',2)">نص 2</button>
<button type="button" onclick="autoFill('goal',3)">نص 3</button>
<button type="button" onclick="autoFill('goal',4)">نص 4</button>
<button type="button" onclick="autoFill('goal',5)">نص 5</button>
</div>

<label>نبذة مختصرة</label>
<textarea id="summary"></textarea>
<div class="auto-buttons">
<button type="button" onclick="autoFill('summary',1)">نص 1</button>
<button type="button" onclick="autoFill('summary',2)">نص 2</button>
<button type="button" onclick="autoFill('summary',3)">نص 3</button>
<button type="button" onclick="autoFill('summary',4)">نص 4</button>
<button type="button" onclick="autoFill('summary',5)">نص 5</button>
</div>

<label>إجراءات التنفيذ</label>
<textarea id="steps"></textarea>
<div class="auto-buttons">
<button type="button" onclick="autoFill('steps',1)">نص 1</button>
<button type="button" onclick="autoFill('steps',2)">نص 2</button>
<button type="button" onclick="autoFill('steps',3)">نص 3</button>
<button type="button" onclick="autoFill('steps',4)">نص 4</button>
<button type="button" onclick="autoFill('steps',5)">نص 5</button>
</div>

<label>الاستراتيجيات</label>
<textarea id="strategies"></textarea>
<div class="auto-buttons">
<button type="button" onclick="autoFill('strategies',1)">نص 1</button>
<button type="button" onclick="autoFill('strategies',2)">نص 2</button>
<button type="button" onclick="autoFill('strategies',3)">نص 3</button>
<button type="button" onclick="autoFill('strategies',4)">نص 4</button>
<button type="button" onclick="autoFill('strategies',5)">نص 5</button>
</div>

<label>نقاط القوة</label>
<textarea id="strengths"></textarea>
<div class="auto-buttons">
<button type="button" onclick="autoFill('strengths',1)">نص 1</button>
<button type="button" onclick="autoFill('strengths',2)">نص 2</button>
<button type="button" onclick="autoFill('strengths',3)">نص 3</button>
<button type="button" onclick="autoFill('strengths',4)">نص 4</button>
<button type="button" onclick="autoFill('strengths',5)">نص 5</button>
</div>

<label>نقاط التحسين</label>
<textarea id="improve"></textarea>
<div class="auto-buttons">
<button type="button" onclick="autoFill('improve',1)">نص 1</button>
<button type="button" onclick="autoFill('improve',2)">نص 2</button>
<button type="button" onclick="autoFill('improve',3)">نص 3</button>
<button type="button" onclick="autoFill('improve',4)">نص 4</button>
<button type="button" onclick="autoFill('improve',5)">نص 5</button>
</div>

<label>التوصيات</label>
<textarea id="recomm"></textarea>
<div class="auto-buttons">
<button type="button" onclick="autoFill('recomm',1)">نص 1</button>
<button type="button" onclick="autoFill('recomm',2)">نص 2</button>
<button type="button" onclick="autoFill('recomm',3)">نص 3</button>
<button type="button" onclick="autoFill('recomm',4)">نص 4</button>
<button type="button" onclick="autoFill('recomm',5)">نص 5</button>
</div>

<label>الصورة الأولى</label>
<input type="file" id="img1" class="image-upload" accept="image/*">

<label>الصورة الثانية</label>
<input type="file" id="img2" class="image-upload" accept="image/*">

<button onclick="saveData()">إنشاء التقرير</button>
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
}

function autoFill(field,i){
document.getElementById(field).value=autoTexts[field][i-1];
}

function saveData(){
let data={
education:education.value,
term:term.value,
reportType:reportType.value,
grade:grade.value,
subject:subject.value,
target:target.value,
count:count.value,
place:place.value,
goal:goal.value,
summary:summary.value,
steps:steps.value,
strategies:strategies.value,
strengths:strengths.value,
improve:improve.value,
recomm:recomm.value
};
localStorage.setItem("reportData",JSON.stringify(data));
saveImage("img1","image1");
saveImage("img2","image2");
setTimeout(()=>{window.location.href="report.html";},500);
}

function saveImage(inputId,key){
let file=document.getElementById(inputId).files[0];
if(!file) return;
let reader=new FileReader();
reader.onload=()=>{localStorage.setItem(key,reader.result);}
reader.readAsDataURL(file);
}
</script>

</body>
</html>