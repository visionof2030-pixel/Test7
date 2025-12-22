
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>أداة إعداد التقارير التعليمية</title>
<style>
body {
  font-family: Tahoma, Arial, sans-serif;
  background: #eef7f5;
  margin: 0;
  padding: 20px;
  font-size: 12px;
}
.tool {
  max-width: 900px;
  margin: auto;
  background: white;
  padding: 20px;
  border-radius: 14px;
  box-shadow: 0 8px 20px rgba(0,0,0,.08);
}
.tool h2 {
  text-align: center;
  color: #0a3b40;
  margin-bottom: 16px;
  font-size: 18px;
}
label {
  font-weight: 700;
  margin-top: 12px;
  display: block;
  color: #0a3b40;
  font-size: 11px;
}
input, textarea, select {
  width: 100%;
  padding: 8px;
  margin-top: 4px;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 12px;
  box-sizing: border-box;
}
textarea {
  resize: vertical;
  min-height: 70px;
}
.small-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 5px;
  margin: 12px 0;
}
.small-grid input,
.small-grid select {
  font-size: 10px;
  padding: 4px 3px;
  height: 32px;
}
.auto-row {
  display: flex;
  gap: 6px;
  margin-top: 6px;
}
.auto-btn {
  flex: 1;
  background: #e0f2f1;
  border: 1px solid #0a3b40;
  color: #0a3b40;
  font-size: 11px;
  padding: 7px;
  border-radius: 5px;
  cursor: pointer;
}
.clear-btn {
  background: #fdecea;
  border: 1px solid #c62828;
  color: #c62828;
}
button#printBtn {
  margin-top: 18px;
  padding: 10px;
  width: 100%;
  background: #0a3b40;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  cursor: pointer;
}
.report {
  display: none;
}
@media print {
  body { background: white; padding: 0; }
  .tool { display: none; }
  .report { display: block; max-width: 210mm; margin: 0 auto; }
}
.header {
  background: #0a3b40;
  color: white;
  text-align: center;
  padding: 6px;
  margin-bottom: 8px;
  border-radius: 4px;
  min-height: auto;
}
.header-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
}
.ministry-title {
  font-size: 13pt;
  font-weight: bold;
}
.ministry-subtitle {
  font-size: 8pt;
}
.school-info {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  margin-top: 2px;
}
.edu-info {
  font-weight: bold;
  font-size: 9pt;
}
.school-name {
  font-weight: bold;
  font-size: 9pt;
}
.hijri-date {
  font-size: 8pt;
  margin-top: 3px;
  color: #e0f7fa;
}
.top-info.two-lines {
  display: flex;
  flex-direction: column;
  gap: 3px;
  margin-bottom: 8px;
}
.top-row {
  display: grid;
  gap: 2px;
}
.top-row.first {
  grid-template-columns: repeat(3, 1fr);
}
.top-row.second {
  grid-template-columns: repeat(4, 1fr);
}
.box {
  border: 1px solid #0a3b40;
  padding: 2px;
  text-align: center;
  font-size: 5.5pt;
  min-height: 22px;
  border-radius: 2px;
  background: #f8f9fa;
}
.box strong {
  display: block;
  font-size: 5.5pt;
  color: #0a3b40;
}
.goal-section {
  background: #e8f5e9;
  border-right: 2px solid #2e7d32;
  border-radius: 5px;
  padding: 6px;
  margin-bottom: 8px;
  text-align: center;
  min-height: auto;
}
.goal-section strong {
  font-size: 10px;
  margin-bottom: 2px;
}
.goal-section div {
  font-size: 10px;
  line-height: 1.3;
}
.grid2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  margin-bottom: 8px;
}
.grid4 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  margin-bottom: 8px;
}
.section {
  border: 1px solid #0a3b40;
  padding: 5px;
  border-radius: 5px;
  font-size: 10px;
}
.section strong {
  font-size: 10px;
  margin-bottom: 2px;
  display: block;
}
.section div {
  font-size: 10px;
  line-height: 1.3;
}
/* المحفزات - باللون الأخضر الليموني */
.section.motivators {
  border: 1px solid #9ccc65;
  background: #f1f8e9;
  min-height: 50px;
  height: auto;
  padding: 3px;
  font-size: 9px;
}
.section.motivators strong {
  font-size: 9.5px;
  margin-bottom: 1px;
  color: #689f38;
}
.section.motivators div {
  font-size: 9px;
  line-height: 1.2;
}
/* نقاط القوة - باللون الأزرق الغامق */
.section.strengths {
  border: 1px solid #0d47a1;
  background: #e3f2fd;
  min-height: 50px;
  height: auto;
  padding: 3px;
  font-size: 9px;
}
.section.strengths strong {
  font-size: 9.5px;
  margin-bottom: 1px;
  color: #0d47a1;
}
.section.strengths div {
  font-size: 9px;
  line-height: 1.2;
}
/* التحديات - باللون الأصفر */
.section.challenges {
  border: 1px solid #f57f17;
  background: #fffde7;
  min-height: 50px;
  height: auto;
  padding: 3px;
  font-size: 9px;
}
.section.challenges strong {
  font-size: 9.5px;
  margin-bottom: 1px;
  color: #f57f17;
}
.section.challenges div {
  font-size: 9px;
  line-height: 1.2;
}
/* مواطن القصور - باللون الأحمر */
.section.weaknesses {
  border: 1px solid #c62828;
  background: #ffebee;
  min-height: 50px;
  height: auto;
  padding: 3px;
  font-size: 9px;
}
.section.weaknesses strong {
  font-size: 9.5px;
  margin-bottom: 1px;
  color: #c62828;
}
.section.weaknesses div {
  font-size: 9px;
  line-height: 1.2;
}
.images {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
  margin: 15px 0;
}
.images img {
  width: 100%;
  max-height: 185px;
  object-fit: cover;
  border-radius: 6px;
  box-shadow: 0 3px 10px rgba(0,0,0,0.1);
}
.signatures {
  margin-top: 15px;
  padding-top: 8px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  font-size: 8pt;
}
.teacher-signature, .principal-signature {
  text-align: center;
  width: 45%;
}
.teacher-signature input, .principal-signature input {
  width: 80%;
  font-size: 8pt;
  padding: 3px;
  margin-top: 3px;
  border: none;
  border-bottom: 1px solid #ccc;
  text-align: center;
}
.signature-label {
  font-weight: bold;
  color: #0a3b40;
  margin-bottom: 3px;
  font-size: 9px;
}
</style>
</head>
<body>

<div class="tool">
<h2>أداة إعداد التقارير التعليمية</h2>

<label>إدارة التعليم</label>
<select id="eduSelect" onchange="updateEduInfo(this.value)">
  <option value="">اختر إدارة التعليم</option>
  <option value="الإدارة العامة للتعليم بمنطقة مكة المكرمة">الإدارة العامة للتعليم بمنطقة مكة المكرمة</option>
  <option value="الإدارة العامة للتعليم بمنطقة الرياض" selected>الإدارة العامة للتعليم بمنطقة الرياض</option>
  <option value="الإدارة العامة للتعليم بمنطقة المدينة المنورة">الإدارة العامة للتعليم بمنطقة المدينة المنورة</option>
  <option value="الإدارة العامة للتعليم بالمنطقة الشرقية">الإدارة العامة للتعليم بالمنطقة الشرقية</option>
  <option value="الإدارة العامة للتعليم بمنطقة القصيم">الإدارة العامة للتعليم بمنطقة القصيم</option>
  <option value="الإدارة العامة للتعليم بمنطقة عسير">الإدارة العامة للتعليم بمنطقة عسير</option>
  <option value="الإدارة العامة للتعليم بمنطقة تبوك">الإدارة العامة للتعليم بمنطقة تبوك</option>
  <option value="الإدارة العامة للتعليم بمنطقة حائل">الإدارة العامة للتعليم بمنطقة حائل</option>
  <option value="الإدارة العامة للتعليم بمنطقة الحدود الشمالية">الإدارة العامة للتعليم بمنطقة الحدود الشمالية</option>
  <option value="الإدارة العامة للتعليم بمنطقة جازان">الإدارة العامة للتعليم بمنطقة جازان</option>
  <option value="الإدارة العامة للتعليم بمنطقة نجران">الإدارة العامة للتعليم بمنطقة نجران</option>
  <option value="الإدارة العامة للتعليم بمنطقة الباحة">الإدارة العامة للتعليم بمنطقة الباحة</option>
  <option value="الإدارة العامة للتعليم بمنطقة الجوف">الإدارة العامة للتعليم بمنطقة الجوف</option>
  <option value="الإدارة العامة للتعليم بمحافظة الأحساء">الإدارة العامة للتعليم بمحافظة الأحساء</option>
  <option value="الإدارة العامة للتعليم بمحافظة الطائف">الإدارة العامة للتعليم بمحافظة الطائف</option>
  <option value="الإدارة العامة للتعليم بمحافظة جدة">الإدارة العامة للتعليم بمحافظة جدة</option>
</select>

<label>اسم المدرسة</label>
<input id="schoolInput" placeholder="أدخل اسم المدرسة هنا" oninput="sync('school',this.value)">

<div class="small-grid">
  <select onchange="sync('reportTitle',this.value); autoFillReport(this.value);" id="reportSelect">
    <option value="">اختر نوع التقرير</option>
    <option value="تقرير نشاط إثرائي">تقرير نشاط إثرائي</option>
    <option value="تقرير خطة علاجية">تقرير خطة علاجية</option>
    <option value="تقرير تنفيذ اختبار تحسن">تقرير تنفيذ اختبار تحسن</option>
    <option value="تقرير تصنيف الطلاب">تقرير تصنيف الطلاب</option>
    <option value="تقرير تحليل النتائج">تقرير تحليل النتائج</option>
    <option value="تقرير سجل الخطط العلاجية">تقرير سجل الخطط العلاجية</option>
    <option value="تقرير رعاية الطلاب المتأخرين دراسيا">تقرير رعاية الطلاب المتأخرين دراسيا</option>
    <option value="تقرير دراسة حالة">تقرير دراسة حالة</option>
    <option value="تقرير التدريب على الاختبارات المعيارية">تقرير التدريب على الاختبارات المعيارية</option>
    <option value="تقرير توزيع المنهج">تقرير توزيع المنهج</option>
    <option value="تقرير توزيع وقت الحصة">تقرير توزيع وقت الحصة</option>
    <option value="تقرير درس تم تنفيذه">تقرير درس تم تنفيذه</option>
    <option value="تقرير تنفيذ درس تطبيقي">تقرير تنفيذ درس تطبيقي</option>
    <option value="تقرير أنشطة صفية">تقرير أنشطة صفية</option>
    <option value="تقرير تعليم تعاوني بين الطلاب">تقرير تعليم تعاوني بين الطلاب</option>
    <option value="تقرير الفصول المقلوبة">تقرير الفصول المقلوبة</option>
    <option value="تقرير توظيف الذكاء الاصطناعي">تقرير توظيف الذكاء الاصطناعي</option>
    <option value="تقرير الوسائل التعليمية المبتكرة">تقرير الوسائل التعليمية المبتكرة</option>
    <option value="تقرير تطوير البيئة الصفية">تقرير تطوير البيئة الصفية</option>
    <option value="تقرير تفعيل حصص النشاط">تقرير تفعيل حصص النشاط</option>
    <option value="تقرير حصة النشاط">تقرير حصة النشاط</option>
    <option value="تقرير المجتمعات المهنية">تقرير المجتمعات المهنية</option>
    <option value="تقرير مجتمعات التعلم">تقرير مجتمعات التعلم</option>
    <option value="تقرير كشف المتابعة">تقرير كشف المتابعة</option>
    <option value="تقرير سجل الدرجات الإلكتروني">تقرير سجل الدرجات الإلكتروني</option>
    <option value="تقرير سجل التغذية الراجعة من الطلاب">تقرير سجل التغذية الراجعة من الطلاب</option>
    <option value="تقرير مقارنة السلاسل الزمنية">تقرير مقارنة السلاسل الزمنية</option>
    <option value="تقرير الاختبارات الذكية">تقرير الاختبارات الذكية</option>
    <option value="تقرير تعزيز السلوك الإيجابي">تقرير تعزيز السلوك الإيجابي</option>
    <option value="تقرير تحفيز الطلاب">تقرير تحفيز الطلاب</option>
    <option value="تقرير معرفة الميول والاتجاهات">تقرير معرفة الميول والاتجاهات</option>
    <option value="تقرير حل مشكلة تربوية">تقرير حل مشكلة تربوية</option>
    <option value="تقرير تكريم المتميزين">تقرير تكريم المتميزين</option>
    <option value="تقرير الاحتفال باليوم الوطني">تقرير الاحتفال باليوم الوطني</option>
    <option value="تقرير المبادرات والابتكار">تقرير المبادرات والابتكار</option>
    <option value="تقرير مبادرة تطوعية">تقرير مبادرة تطوعية</option>
    <option value="تقرير المعلم الصغير">تقرير المعلم الصغير</option>
    <option value="تقرير تنفيذ إذاعة مدرسية">تقرير تنفيذ إذاعة مدرسية</option>
    <option value="تقرير المشاركات بين الطلاب">تقرير المشاركات بين الطلاب</option>
    <option value="تقرير التواصل مع ولي الأمر">تقرير التواصل مع ولي الأمر</option>
    <option value="تقرير إشعار ولي الأمر عن مستوى ابنه">تقرير إشعار ولي الأمر عن مستوى ابنه</option>
    <option value="تقرير حضور اجتماع أولياء الأمور">تقرير حضور اجتماع أولياء الأمور</option>
    <option value="تقرير سجل التواصل مع أولياء الأمور">تقرير سجل التواصل مع أولياء الأمور</option>
    <option value="تقرير تبادل الزيارات">تقرير تبادل الزيارات</option>
    <option value="تقرير حضور دورات وورش تدريبية">تقرير حضور دورات وورش تدريبية</option>
    <option value="تقرير نقل أثر التدريب">تقرير نقل أثر التدريب</option>
    <option value="تقرير الورش التدريبية التي قدمتها">تقرير الورش التدريبية التي قدمتها</option>
    <option value="تقرير البحث الإجرائي">تقرير البحث الإجرائي</option>
    <option value="تقرير خطة أسبوعية">تقرير خطة أسبوعية</option>
    <option value="تقرير تفعيل الخطة الأسبوعية">تقرير تفعيل الخطة الأسبوعية</option>
    <option value="تقرير الإشراف اليومي">تقرير الإشراف اليومي</option>
    <option value="تقرير إدارة الأزمات">تقرير إدارة الأزمات</option>
    <option value="تقرير إدارة الاجتماعات">تقرير إدارة الاجتماعات</option>
    <option value="تقرير المناوبة والفسحة">تقرير المناوبة والفسحة</option>
    <option value="تقارير الجرد (للمختبرات وغرف المصادر)">تقارير الجرد (للمختبرات وغرف المصادر)</option>
    <option value="تقرير تفعيل المنصات التعليمية">تقرير تفعيل المنصات التعليمية</option>
    <option value="تقرير المحتوى الرقمي المنتج">تقرير المحتوى الرقمي المنتج</option>
    <option value="تقرير التعلم التعاوني">تقرير التعلم التعاوني</option>
    <option value="تقرير التعلم القائم على المشروعات">تقرير التعلم القائم على المشروعات</option>
    <option value="تقرير التعلم القائم على حل المشكلات">تقرير التعلم القائم على حل المشكلات</option>
    <option value="تقرير التعلم بالاكتشاف">تقرير التعلم بالاكتشاف</option>
    <option value="تقرير العصف الذهني">تقرير العصف الذهني</option>
    <option value="تقرير التعلم باللعب">تقرير التعلم باللعب</option>
    <option value="تقرير التعلم الذاتي">تقرير التعلم الذاتي</option>
    <option value="تقرير التعلم القائم على الاستقصاء">تقرير التعلم القائم على الاستقصاء</option>
    <option value="تقرير التعلم المتمركز حول الطالب">تقرير التعلم المتمركز حول الطالب</option>
    <option value="تقرير التدريس المتمايز">تقرير التدريس المتمايز</option>
    <option value="تقرير التدريس المباشر">تقرير التدريس المباشر</option>
    <option value="تقرير التدريس العلاجي">تقرير التدريس العلاجي</option>
    <option value="تقرير التدريس الإثرائي">تقرير التدريس الإثرائي</option>
    <option value="تقرير التدريس القائم على الكفايات">تقرير التدريس القائم على الكفايات</option>
    <option value="تقرير التدريس باستخدام النمذجة">تقرير التدريس باستخدام النمذجة</option>
    <option value="تقرير التدريس باستخدام الأسئلة السابرة">تقرير التدريس باستخدام الأسئلة السابرة</option>
    <option value="تقرير التدريس بالحوار والمناقشة">تقرير التدريس بالحوار والمناقشة</option>
    <option value="تقرير التقويم التشخيصي">تقرير التقويم التشخيصي</option>
    <option value="تقرير التقويم البنائي">تقرير التقويم البنائي</option>
    <option value="تقرير التقويم الختامي">تقرير التقويم الختامي</option>
    <option value="تقرير التقويم بالأداء">تقرير التقويم بالأداء</option>
    <option value="تقرير التقويم الذاتي للطلاب">تقرير التقويم الذاتي للطلاب</option>
    <option value="تقرير التقويم بالأقران">تقرير التقويم بالأقران</option>
    <option value="تقرير التقويم الإلكتروني">تقرير التقويم الإلكتروني</option>
    <option value="تقرير تحليل أدوات التقويم">تقرير تحليل أدوات التقويم</option>
    <option value="تقرير استخدام المنصات التعليمية">تقرير استخدام المنصات التعليمية</option>
    <option value="تقرير توظيف التقنيات التعليمية">تقرير توظيف التقنيات التعليمية</option>
    <option value="تقرير استخدام التطبيقات التعليمية">تقرير استخدام التطبيقات التعليمية</option>
    <option value="تقرير توظيف السبورة التفاعلية">تقرير توظيف السبورة التفاعلية</option>
    <option value="تقرير إنتاج محتوى تعليمي رقمي">تقرير إنتاج محتوى تعليمي رقمي</option>
  </select>
  <input placeholder="المستهدفون" oninput="sync('target',this.value)">
  <input placeholder="العدد" oninput="sync('count',this.value)">
  <input placeholder="مكان التنفيذ" oninput="sync('location',this.value)">
  <select id="semesterSelect" onchange="sync('semester',this.value)">
    <option value="">اختر الفصل الدراسي</option>
    <option value="الفصل الدراسي الأول">الفصل الدراسي الأول</option>
    <option value="الفصل الدراسي الثاني">الفصل الدراسي الثاني</option>
  </select>
  <input placeholder="الصف" oninput="sync('grade',this.value)">
  <input placeholder="المادة" oninput="sync('subject',this.value)">
</div>

<div class="auto-row">
  <button class="auto-btn" onclick="autoFillReport(document.getElementById('reportSelect').value)">تعبئة تلقائية للتقرير</button>
  <button class="auto-btn clear-btn" onclick="clearAllFields()">مسح جميع الحقول</button>
</div>

<label>الهدف التربوي</label>
<textarea id="goalInput" oninput="sync('goal',this.value)"></textarea>

<label>وصف مختصر</label>
<textarea id="desc1Input" oninput="sync('desc1',this.value)"></textarea>

<label>إجراءات التنفيذ</label>
<textarea id="desc2Input" oninput="sync('desc2',this.value)"></textarea>

<label>النتائج</label>
<textarea id="desc3Input" oninput="sync('desc3',this.value)"></textarea>

<label>التوصيات</label>
<textarea id="desc4Input" oninput="sync('desc4',this.value)"></textarea>

<!-- الصف الأول: المحفزات ونقاط القوة -->
<div class="grid2">
  <div>
    <label>المحفزات</label>
    <textarea id="motivatorsInput" oninput="sync('motivators',this.value)"></textarea>
  </div>
  <div>
    <label>نقاط القوة</label>
    <textarea id="strengthsInput" oninput="sync('strengths',this.value)"></textarea>
  </div>
</div>

<!-- الصف الثاني: التحديات ومواطن القصور -->
<div class="grid2">
  <div>
    <label>التحديات</label>
    <textarea id="challengesInput" oninput="sync('challenges',this.value)"></textarea>
  </div>
  <div>
    <label>مواطن القصور</label>
    <textarea id="weaknessesInput" oninput="sync('weaknesses',this.value)"></textarea>
  </div>
</div>

<label>إرفاق الصور (اختياري)</label>
<input type="file" multiple accept="image/*" onchange="loadImages(this)">

<div class="signatures">
  <div class="teacher-signature">
    <div class="signature-label">اسم المعلم</div>
    <input type="text" id="teacherInput" placeholder="أدخل اسم المعلم" oninput="sync('teacherName', this.value)">
  </div>
  <div class="principal-signature">
    <div class="signature-label">اسم مدير المدرسة</div>
    <input type="text" id="principalInput" placeholder="أدخل اسم المدير" oninput="sync('principalName', this.value)">
  </div>
</div>

<button id="printBtn" onclick="window.print()">معاينة وطباعة التقرير</button>
</div>

<!-- قسم التقرير للطباعة -->
<div class="report">
<div class="header">
  <div class="header-content">
    <div class="ministry-title">وزارة التعليم</div>
    <div class="ministry-subtitle">Ministry of Education</div>
    <div class="school-info">
      <div class="edu-info" id="eduHeader">الإدارة العامة للتعليم بمنطقة الرياض</div>
      <div class="school-name" id="school"></div>
    </div>
    <div class="hijri-date" id="hijriDate">جاري تحميل التاريخ الهجري...</div>
  </div>
</div>

<div class="top-info two-lines">
  <div class="top-row first">
    <div class="box"><strong>الفصل الدراسي</strong><div id="semester"></div></div>
    <div class="box"><strong>الصف</strong><div id="grade"></div></div>
    <div class="box"><strong>المادة</strong><div id="subject"></div></div>
  </div>
  <div class="top-row second">
    <div class="box"><strong>التقرير</strong><div id="reportTitle"></div></div>
    <div class="box"><strong>المستهدفون</strong><div id="target"></div></div>
    <div class="box"><strong>العدد</strong><div id="count"></div></div>
    <div class="box"><strong>مكان التنفيذ</strong><div id="location"></div></div>
  </div>
</div>

<div class="goal-section">
<strong>الهدف التربوي</strong>
<div id="goal"></div>
</div>

<div class="grid2">
  <div class="section"><strong>وصف مختصر</strong><div id="desc1"></div></div>
  <div class="section"><strong>إجراءات التنفيذ</strong><div id="desc2"></div></div>
</div>

<div class="grid2">
  <div class="section"><strong>النتائج</strong><div id="desc3"></div></div>
  <div class="section"><strong>التوصيات</strong><div id="desc4"></div></div>
</div>

<!-- الصف الأول في التقرير: المحفزات ونقاط القوة -->
<div class="grid4">
  <div class="section motivators"><strong>المحفزات</strong><div id="motivators"></div></div>
  <div class="section strengths"><strong>نقاط القوة</strong><div id="strengths"></div></div>
</div>

<!-- الصف الثاني في التقرير: التحديات ومواطن القصور -->
<div class="grid4">
  <div class="section challenges"><strong>التحديات</strong><div id="challenges"></div></div>
  <div class="section weaknesses"><strong>مواطن القصور</strong><div id="weaknesses"></div></div>
</div>

<div class="images" id="imagesBox"></div>

<div class="signatures">
  <div class="teacher-signature">
    <div class="signature-label">المعلم</div>
    <div id="teacherName"></div>
  </div>
  <div class="principal-signature">
    <div class="signature-label">مدير المدرسة</div>
    <div id="principalName"></div>
  </div>
</div>
</div>

<script>
// قاعدة البيانات الكاملة للنصوص الذكية لكل تقرير
const reportTexts = {
  "تقرير نشاط إثرائي": {
    goal: "تنمية المهارات الإبداعية والتفكير النقدي لدى الطلاب المتميزين",
    desc1: "أنشطة إثرائية متقدمة لتعزيز القدرات العقلية والإبداعية",
    desc2: "تصميم محتوى متقدم، ورش عمل تفاعلية، مشاريع بحثية مصغرة، عروض تقديمية، تقييم إبداعي",
    desc3: "تطور ملحوظ في التفكير النقدي، ابتكار حلول إبداعية، زيادة الثقة العلمية",
    desc4: "استمرارية البرامج الإثرائية، توسيع قاعدة المشاركين، تعزيز الشراكات الأكاديمية",
    motivators: "جوائز تقديرية، شهادات تميز، مشاركة في مسابقات علمية، زيارات ميدانية",
    strengths: "محتوى علمي متقدم، مرونة في التنفيذ، تفاعل طلابي عالٍ، بيئة محفزة",
    challenges: "تنوع المستويات الفكرية، صعوبة توفير الموارد المتخصصة، ضيق الإطار الزمني",
    weaknesses: "نقص الأجهزة المتطورة، محدودية الميزانية، قلة الخبرات الاستشارية"
  },
  "تقرير خطة علاجية": {
    goal: "تدارك الفجوات التعليمية وتحسين الأداء الأكاديمي للطلاب المتأخرين",
    desc1: "برنامج تدريبي مكثف لمعالجة نقاط الضعف وتحسين التحصيل الدراسي",
    desc2: "تشخيص دقيق للصعوبات، وضع خطط فردية، تدريبات مكثفة، متابعة يومية، تقييم أسبوعي",
    desc3: "تحسن بنسبة 75% في المستوى الدراسي، انخفاض معدل الرسوب، زيادة الثقة بالنفس",
    desc4: "تطوير أدوات التشخيص، تدريب المعلمين المتخصصين، تفعيل التعليم العلاجي المستمر",
    motivators: "نظام مكافآت تقدمي، شهادات تحسن، حصص تقوية مجانية، متابعة فردية",
    strengths: "فريق تدريسي متخصص، مواد تعليمية مكثفة، متابعة حثيثة، بيئة داعمة",
    challenges: "مقاومة بعض الطلاب، ضعف متابعة الأهالي، كثافة المناهج الدراسية",
    weaknesses: "قلة الموارد المالية، نقص الغرف الصفية، ضغط الوقت على المعلمين"
  },
  "تقرير تنفيذ اختبار تحسن": {
    goal: "قياس مدى التطور في الأداء الأكاديمي وتحليل مؤشرات التحسن",
    desc1: "تطبيق اختبارات قياسية لتقييم التقدم الدراسي وتحليل النتائج",
    desc2: "إعداد الاختبارات، تحديد المعايير، التطبيق الجماعي، تصحيح آلي، تحليل النتائج",
    desc3: "زيادة متوسط الدرجات بنسبة 15%، تحسن في الفهم الاستيعابي، ارتفاع مؤشرات التحسن",
    desc4: "توحيد معايير الاختبارات، تكرار التقييم الدوري، تطوير بنوك الأسئلة",
    motivators: "نتائج فورية، رسوم بيانية توضيحية، تقارير تحليلية، جوائز للمتفوقين",
    strengths: "دقة في القياس، موضوعية في التقييم، سرعة في النتائج، تحليل إحصائي دقيق",
    challenges: "قلق الاختبارات، تباين الظروف، صعوبة التطبيق الموحد، ضغط الوقت",
    weaknesses: "تكاليف التصحيح الآلي، حاجة للتدريب المستمر، صعوبة معايرة الأسئلة"
  },
  "تقرير تصنيف الطلاب": {
    goal: "تحليل وتصنيف الطلاب حسب القدرات والمستويات التعليمية",
    desc1: "دراسة شاملة لتوزيع الطلاب حسب المستويات وتحديد الاحتياجات",
    desc2: "جمع البيانات، تحليل النتائج، تطبيق معايير التصنيف، إعداد التقارير، تقديم التوصيات",
    desc3: "تحديد دقيق للمستويات، توزيع منطقي للمجموعات، فهم عميق للفروق الفردية",
    desc4: "تطوير معايير التصنيف، تحديث البيانات دورياً، تحسين التوزيع الصفي",
    motivators: "مجموعات متجانسة، تعليم مخصص، تقارير شخصية، مسارات تعليمية واضحة",
    strengths: "دقة في التصنيف، مراعاة الفروق، بيانات حديثة، تحليل متعدد الأبعاد",
    challenges: "حساسية التصنيف، مقاومة التغيير، صعوبة التوزيع المتوازن، ضغط أولياء الأمور",
    weaknesses: "نقص البيانات التاريخية، محدودية المعايير، صعوبة المتابعة المستمرة"
  },
  "تقرير تحليل النتائج": {
    goal: "دراسة شاملة للنتائج الدراسية واستخلاص مؤشرات الأداء",
    desc1: "تحليل إحصائي متقدم للنتائج الدراسية وتحديد الاتجاهات العامة",
    desc2: "جمع البيانات، معالجة إحصائية، تحليل المقارنات، استخلاص المؤشرات، وضع التوصيات",
    desc3: "كشف أنماط الأداء، تحديد نقاط القوة والضعف، رسم مسارات التحسين المستقبلية",
    desc4: "اعتماد التحليل الدوري، تدريب الكوادر، توحيد المنهجية، تطوير أدوات التحليل",
    motivators: "رؤية واضحة للأداء، مؤشرات قابلة للقياس، تقارير تحليلية متقدمة",
    strengths: "دقة علمية، تحليل متعمق، رسوم بيانية توضيحية، مقارنات تاريخية",
    challenges: "تعقيد البيانات، نقص الخبرات الإحصائية، صعوبة التفسير، تباين الدقة",
    weaknesses: "نقص البرامج المتخصصة، محدودية الوقت، صعوبة التوحيد القياسي"
  },
  "تقرير سجل الخطط العلاجية": {
    goal: "توثيق ومتابعة تنفيذ الخطط العلاجية وتقييم فاعليتها",
    desc1: "حفظ وتنظيم سجلات الخطط العلاجية وتتبع تطور الحالات",
    desc2: "تسجيل الحالات، توثيق الخطط، متابعة التنفيذ، تقييم النتائج، تحديث السجلات",
    desc3: "حفظ منظم للبيانات، سهولة في المتابعة، تقييم موضوعي، تتبع مستمر للتطور",
    desc4: "توحيد نماذج التسجيل، تدريب الموظفين، رقمنة السجلات، تحسين آليات المتابعة",
    motivators: "سهولة الوصول للمعلومات، تقارير دورية، متابعة منظمة، تحسين الخدمة",
    strengths: "تنظيم محكم، تحديث مستمر، بيانات دقيقة، سهولة في الاسترجاع",
    challenges: "عبء التوثيق، صعوبة المتابعة، نقص الوقت، مقاومة التسجيل",
    weaknesses: "نقص التجهيزات، ضعف التدريب، محدودية التخزين، صعوبة التوحيد"
  },
  "تقرير رعاية الطلاب المتأخرين دراسيا": {
    goal: "توفير دعم متكامل للطلاب المتأخرين وتمكينهم أكاديمياً",
    desc1: "برنامج شامل للرعاية النفسية والتعليمية للطلاب ذوي الأداء المتدني",
    desc2: "تشخيص الأسباب، تقديم الدعم النفسي، توفير المساعدة الأكاديمية، متابعة مكثفة، تقييم دوري",
    desc3: "تحسن في المستوى الدراسي، ارتفاع التحفيز الذاتي، انخفاض نسبة التسرب، زيادة الاندماج",
    desc4: "توسيع نطاق الرعاية، تعزيز الشراكات المجتمعية، تطوير آليات الدعم، تدريب المتخصصين",
    motivators: "برامج دعم نفسي، جو إيجابي، متابعة فردية، أنشطة ترفيهية علاجية",
    strengths: "فريق متعدد التخصصات، برامج مخصصة، بيئة داعمة، متابعة شاملة",
    challenges: "تعقيد المشكلات، نقص الموارد، مقاومة التغيير، ضغط الوقت",
    weaknesses: "نقص الكوادر المتخصصة، محدودية التمويل، صعوبة القياس النفسي"
  },
  "تقرير دراسة حالة": {
    goal: "تحليل عميق لحالة فردية واستخلاص دروس وتوصيات تطبيقية",
    desc1: "بحث معمق في حالة دراسية محددة لفهم العوامل المؤثرة والاستفادة منها",
    desc2: "جمع المعلومات، تحليل البيانات، تحديد العوامل، وضع الفرضيات، استخلاص النتائج",
    desc3: "فهم عميق للحالة، تحديد العوامل الحاسمة، استخلاص دروس قيمة، تطوير حلول عملية",
    desc4: "تعميم الدروس المستفادة، تطوير أدوات التحليل، تدريب الباحثين، نشر النتائج",
    motivators: "معرفة متعمقة، حلول إبداعية، تطوير مهني، مساهمة في المعرفة",
    strengths: "تحليل دقيق، منهجية علمية، نتائج قابلة للتعميم، مساهمة في التطوير",
    challenges: "حساسية المعلومات، صعوبة الوصول للبيانات، تعقيد التحليل، وقت طويل",
    weaknesses: "نقص التدريب المنهجي، محدودية العينات، صعوبة القياس الكمي"
  },
  "تقرير التدريب على الاختبارات المعيارية": {
    goal: "إعداد الطلاب نفسياً وأكاديمياً للاختبارات المعيارية المحلية والدولية",
    desc1: "برنامج تدريبي مكثف لتعريف الطلاب بآليات الاختبارات المعيارية وتحسين أدائهم",
    desc2: "شرح أنماط الأسئلة، تدريبات مكثفة، محاكاة الاختبارات، تحليل الأخطاء، تقديم نصائح",
    desc3: "زيادة الثقة بالنفس، تحسن في إدارة الوقت، ارتفاع الدرجات، انخفاض القلق",
    desc4: "استمرارية البرامج التدريبية، تطوير المحتوى، توسيع الفئات المستهدفة، تحديث الأساليب",
    motivators: "نتائج محاكاة، جوائز تشجيعية، شهادات مشاركة، تقارير تحليلية",
    strengths: "مدربون متخصصون، مواد تدريبية حديثة، محاكاة واقعية، تحليل مفصل",
    challenges: "تنوع المستويات، ضغط الوقت، تكاليف التدريب، مقاومة بعض الطلاب",
    weaknesses: "نقص المراجع، محدودية التجهيزات، صعوبة المحاكاة الدقيقة"
  },
  "تقرير توزيع المنهج": {
    goal: "تنظيم وتخطيط زمني محكم لتنفيذ المناهج الدراسية بشكل متوازن",
    desc1: "تخطيط زمني تفصيلي لتنفيذ محتويات المنهج الدراسي خلال الفصل",
    desc2: "تحليل المحتوى، تحديد الأولويات، توزيع زمني منطقي، مراعاة الفعاليات، مراجعة مستمرة",
    desc3: "تنفيذ منظم للمنهج، تجنب التزاحم، توزيع متوازن، تحقيق الأهداف الزمنية",
    desc4: "مرونة في التعديل، مشاركة المعلمين، تقييم دوري، تحسين التوزيع سنوياً",
    motivators: "وضوح في الخطة، تجنب العشوائية، تحسين الإنجاز، سهولة المتابعة",
    strengths: "تنظيم محكم، مراعاة الظروف، مرونة في التطبيق، مشاركة جماعية",
    challenges: "تغير الظروف، ضغط الوقت، تنوع الآراء، صعوبة التوازن",
    weaknesses: "نقص الخبرة التخطيطية، مقاومة التغيير، صعوبة التطبيق الحرفي"
  }
};

// النصوص الافتراضية للتقارير التي ليس لها نصوص محددة
const defaultTexts = {
  goal: "تحسين العملية التعليمية وتطوير الممارسات التدريسية",
  desc1: "تقرير يصف عملية تنفيذ نشاط تعليمي هادف ومخطط له",
  desc2: "التخطيط للنشاط، تجهيز الموارد، التنفيذ الفعلي، المتابعة المستمرة، التقييم النهائي",
  desc3: "تحقيق الأهداف المخطط لها، تحسن في الأداء، رضا المشاركين، نتائج إيجابية",
  desc4: "الاستمرارية في التنفيذ، التوسع في النشاط، تطوير الآليات، تعميم النتائج",
  motivators: "تحفيز المشاركين، توفير الدعم، تقدير الجهود، بيئة محفزة",
  strengths: "التزام الفريق، دعم الإدارة، كفاءة التنفيذ، وضوح الأهداف",
  challenges: "ضيق الوقت، نقص الموارد، صعوبة التنسيق، مقاومة التغيير",
  weaknesses: "نقص الخبرة، محدودية الإمكانيات، صعوبة القياس، ضعف المتابعة"
};

// دالة للحصول على التاريخ الهجري من API خارجي
async function getHijriDate() {
  try {
    const response = await fetch('https://api.aladhan.com/v1/gToH');
    
    if (!response.ok) {
      throw new Error('فشل في الحصول على التاريخ الهجري');
    }
    
    const data = await response.json();
    
    if (data.code === 200 && data.data) {
      const hijri = data.data.hijri;
      const dateString = `${hijri.day} ${hijri.month.ar} ${hijri.year} هـ`;
      document.getElementById('hijriDate').textContent = `التاريخ الهجري: ${dateString}`;
    } else {
      document.getElementById('hijriDate').textContent = "التاريخ الهجري: غير متاح";
    }
  } catch (error) {
    console.error('خطأ في الحصول على التاريخ الهجري:', error);
    document.getElementById('hijriDate').textContent = "التاريخ الهجري: ١ رمضان ١٤٤٥ هـ";
  }
}

// دالة لتحديث معلومات إدارة التعليم في الهيدر
function updateEduInfo(value) {
  const eduHeader = document.getElementById('eduHeader');
  if (eduHeader && value) {
    eduHeader.textContent = value;
  }
}

function sync(id, value) {
  const el = document.getElementById(id);
  if (el) {
    el.textContent = value;
  }
}

function autoFillReport(reportType) {
  const texts = reportTexts[reportType] || defaultTexts;
  
  document.getElementById('goalInput').value = texts.goal;
  document.getElementById('desc1Input').value = texts.desc1;
  document.getElementById('desc2Input').value = texts.desc2;
  document.getElementById('desc3Input').value = texts.desc3;
  document.getElementById('desc4Input').value = texts.desc4;
  document.getElementById('motivatorsInput').value = texts.motivators;
  document.getElementById('strengthsInput').value = texts.strengths;
  document.getElementById('challengesInput').value = texts.challenges;
  document.getElementById('weaknessesInput').value = texts.weaknesses;

  sync('goal', texts.goal);
  sync('desc1', texts.desc1);
  sync('desc2', texts.desc2);
  sync('desc3', texts.desc3);
  sync('desc4', texts.desc4);
  sync('motivators', texts.motivators);
  sync('strengths', texts.strengths);
  sync('challenges', texts.challenges);
  sync('weaknesses', texts.weaknesses);

  // تعبئة الحقول الإضافية بناءً على نوع التقرير
  const reportFields = {
    "تقرير نشاط إثرائي": { target: "الطلاب المتميزين", count: "15", location: "المختبر العلمي" },
    "تقرير خطة علاجية": { target: "الطلاب المتأخرين دراسياً", count: "10", location: "غرفة المصادر" },
    "تقرير تنفيذ اختبار تحسن": { target: "جميع الطلاب", count: "40", location: "قاعة الاختبارات" },
    "تقرير تصنيف الطلاب": { target: "طلاب الصفوف", count: "35", location: "مكتب الإرشاد" },
    "تقرير تحليل النتائج": { target: "المعلمون والإداريون", count: "8", location: "قاعة الاجتماعات" },
    "تقرير سجل الخطط العلاجية": { target: "منسقي الدعم التعليمي", count: "5", location: "مكتب التوجيه" },
    "تقرير رعاية الطلاب المتأخرين دراسيا": { target: "الطلاب الضعاف", count: "12", location: "غرفة الدعم النفسي" },
    "تقرير دراسة حالة": { target: "الحالة الفردية", count: "1", location: "بيئة الدراسة" },
    "تقرير التدريب على الاختبارات المعيارية": { target: "طلاب الشهادات", count: "25", location: "معمل التدريب" },
    "تقرير توزيع المنهج": { target: "معلمو المواد", count: "10", location: "قاعة التخطيط" }
  };
  
  if (reportFields[reportType]) {
    const fields = reportFields[reportType];
    document.querySelector('input[placeholder="المستهدفون"]').value = fields.target;
    document.querySelector('input[placeholder="العدد"]').value = fields.count;
    document.querySelector('input[placeholder="مكان التنفيذ"]').value = fields.location;
    
    sync('target', fields.target);
    sync('count', fields.count);
    sync('location', fields.location);
  } else {
    document.querySelector('input[placeholder="المستهدفون"]').value = "المستهدفين";
    document.querySelector('input[placeholder="العدد"]').value = "20";
    document.querySelector('input[placeholder="مكان التنفيذ"]').value = "مكان التنفيذ";
    
    sync('target', "المستهدفين");
    sync('count', "20");
    sync('location', "مكان التنفيذ");
  }
}

function clearAllFields() {
  const fieldsToClear = [
    'goalInput', 'desc1Input', 'desc2Input', 'desc3Input', 'desc4Input',
    'motivatorsInput', 'strengthsInput', 'challengesInput', 'weaknessesInput',
    'teacherInput', 'principalInput', 'schoolInput'
  ];
  
  const placeholders = [
    'المستهدفون',
    'العدد',
    'مكان التنفيذ',
    'الصف',
    'المادة'
  ];
  
  fieldsToClear.forEach(id => {
    const element = document.getElementById(id);
    if (element) {
      element.value = '';
      const syncId = id.replace('Input', '');
      if (!['teacher', 'principal', 'school'].includes(syncId)) {
        sync(syncId, '');
      }
    }
  });
  
  placeholders.forEach(placeholder => {
    const input = document.querySelector(`input[placeholder="${placeholder}"]`);
    if (input) input.value = '';
  });
  
  sync('target', '');
  sync('count', '');
  sync('location', '');
  sync('grade', '');
  sync('subject', '');
  sync('teacherName', '');
  sync('principalName', '');
  
  document.getElementById('semesterSelect').selectedIndex = 0;
  sync('semester', '');
  
  document.getElementById('imagesBox').innerHTML = '';
}

function loadImages(input) {
  const box = document.getElementById("imagesBox");
  box.innerHTML = "";
  Array.from(input.files).slice(0, 2).forEach(file => {
    const reader = new FileReader();
    reader.onload = e => {
      const img = document.createElement("img");
      img.src = e.target.result;
      box.appendChild(img);
    };
    reader.readAsDataURL(file);
  });
}

// تعبئة أولية للمساعدة في التجربة
window.onload = async function() {
  document.getElementById('schoolInput').value = "مدرسة النموذجية الابتدائية";
  sync('school', "مدرسة النموذجية الابتدائية");
  updateEduInfo("الإدارة العامة للتعليم بمنطقة الرياض");
  
  // جلب التاريخ الهجري عند تحميل الصفحة
  await getHijriDate();
};
</script>
</body>
</html>
