
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>أداة إعداد التقارير التعليمية (نموذج تجريبي)</title>
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
<h2>أداة إعداد التقارير التعليمية (نموذج تجريبي)</h2>

<label>إدارة التعليم</label>
<select id="eduSelect" onchange="updateEduInfo(this.value)">
  <option value="">اختر إدارة التعليم</option>
  <option value="الإدارة العامة للتعليم بمنطقة الرياض" selected>الإدارة العامة للتعليم بمنطقة الرياض</option>
  <option value="الإدارة العامة للتعليم بمنطقة مكة المكرمة">الإدارة العامة للتعليم بمنطقة مكة المكرمة</option>
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
    <option value="تقرير نشاط إثرائي" selected>تقرير نشاط إثرائي</option>
    <option value="تقرير خطة علاجية">تقرير خطة علاجية</option>
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
// قاعدة البيانات الذكية للنصوص التلقائية
const smartReportTexts = {
  "تقرير نشاط إثرائي": {
    goal: "تمكين الطلاب المتميزين من تنمية قدراتهم العقلية والابداعية عبر أنشطة تعليمية متقدمة",
    desc1: "مبادرة تعليمية تهدف إلى إثراء خبرات الطلاب المتفوقين وتنمية مهارات التفكير النقدي والإبداعي لديهم",
    desc2: "تحديد الموهوبين أكاديمياً، تصميم برامج إثرائية مخصصة، توفير مختبرات علمية متطورة، إشراف أكاديمي متخصص، تقييم أداء دوري",
    desc3: "ارتفاع مستوى التفكير التحليلي بنسبة 40%، تطوير 15 مشروعاً بحثياً مبتكراً، مشاركة في مسابقات علمية محلية، تحسن الثقة بالنفس لدى المشاركين",
    desc4: "توسيع قاعدة المستفيدين، إنشاء نادي علمي دائم، توثيق التجارب الناجحة، تدريب المعلمين على استراتيجيات الإثراء",
    motivators: "جوائز تقديرية للمتميزين، رحلات علمية استكشافية، شهادات مشاركة معتمدة، نشر الإنجازات في الوسائل التعليمية",
    strengths: "معلمون متخصصون في الموهوبين، مرافق تعليمية مجهزة، دعم إداري كامل، شراكات مع جامعات محلية، منهجية علمية متكاملة",
    challenges: "محدودية الموارد المالية، صعوبة التوفيق بين البرنامج والمنهج الرسمي، تفاوت القدرات بين الموهوبين، نقص الخبرات المتخصصة",
    weaknesses: "ضعف المتابعة الأسرية، قلة الوقت المخصص، عدم وجود معايير موحدة للتقييم، محدودية وسائل الإثراء التقنية"
  },
  
  "تقرير خطة علاجية": {
    goal: "معالجة الفجوات التعليمية لدى الطلاب المتأخرين دراسياً وتمكينهم من اللحاق بأقرانهم عبر برامج تدخل منهجية",
    desc1: "برنامج منهجي شامل لتشخيص ومعالجة الصعوبات التعليمية لدى الفئات الأكثر احتياجاً للدعم الأكاديمي",
    desc2: "تشخيص فردي لكل حالة، وضع خطط علاجية مخصصة، جلسات تعليمية مكثفة، استخدام وسائل تعليمية مساندة، تقييم تقدم أسبوعي، توجيه وإرشاد تربوي",
    desc3: "تحسن 85% من الطلاب في المهارات الأساسية، ارتفاع معدلات النجاح بنسبة 30%، زيادة الثقة الأكاديمية، تحسن السلوك التعليمي، تفاعل إيجابي مع المنهج",
    desc4: "تطوير أدوات تشخيصية دقيقة، تدريب فرق علاجية متخصصة، إنشاء بنك موارد تعليمية، تعزيز الشراكة مع الأسر، إعداد تقارير متابعة دورية",
    motivators: "برامج تحفيزية مرحلية، جوائز للتحسن الملحوظ، شهادات تقدير، نشر قصص النجاح، تخصيص مرشدين أكاديميين",
    strengths: "فريق عمل متخصص، منهجية علاجية مثبتة، مرونة في الجدولة، دعم نفسي وتربوي، تعاون مجتمعي",
    challenges: "مقاومة التغيير من بعض الطلاب، صعوبة إقناع الأسر، نقص الموارد التعليمية المساندة، ضغط الوقت والمنهج",
    weaknesses: "عدم انتظام الحضور، ضعف المتابعة المنزلية، قلة الكوادر المتخصصة، محدودية التمويل، صعوبة قياس الأثر البعيد"
  }
};

// توليد نصوص ذكية ومتنوعة عند الضغط على الزر
function getSmartTexts(reportType) {
  const texts = smartReportTexts[reportType];
  if (!texts) return null;
  
  // إنشاء نصوص متنوعة لكل مرة
  const variations = {
    goal: [
      texts.goal,
      texts.goal.replace("تمكين", "تعزيز").replace("تنمية", "تطوير"),
      texts.goal + " مع التركيز على تحقيق أقصى استفادة ممكنة من الموارد المتاحة"
    ],
    desc1: [
      texts.desc1,
      texts.desc1.replace("مبادرة", "برنامج").replace("تهدف", "يسعى"),
      "مشروع تربوي مبتكر يركز على " + texts.desc1.split(" ").slice(2).join(" ")
    ],
    desc2: [
      texts.desc2,
      texts.desc2.split("، ").sort(() => Math.random() - 0.5).join("، "),
      "تطبيق استراتيجيات متعددة تشمل: " + texts.desc2
    ]
  };
  
  return {
    goal: variations.goal[Math.floor(Math.random() * variations.goal.length)],
    desc1: variations.desc1[Math.floor(Math.random() * variations.desc1.length)],
    desc2: variations.desc2[Math.floor(Math.random() * variations.desc2.length)],
    desc3: texts.desc3,
    desc4: texts.desc4,
    motivators: texts.motivators,
    strengths: texts.strengths,
    challenges: texts.challenges,
    weaknesses: texts.weaknesses
  };
}

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
  if (!value) return;
  const eduHeader = document.getElementById('eduHeader');
  if (eduHeader) {
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
  if (!reportType) {
    alert("يرجى اختيار نوع التقرير أولاً");
    return;
  }
  
  const texts = getSmartTexts(reportType);
  if (!texts) return;

  // تعبئة الحقول
  document.getElementById('goalInput').value = texts.goal;
  document.getElementById('desc1Input').value = texts.desc1;
  document.getElementById('desc2Input').value = texts.desc2;
  document.getElementById('desc3Input').value = texts.desc3;
  document.getElementById('desc4Input').value = texts.desc4;
  document.getElementById('motivatorsInput').value = texts.motivators;
  document.getElementById('strengthsInput').value = texts.strengths;
  document.getElementById('challengesInput').value = texts.challenges;
  document.getElementById('weaknessesInput').value = texts.weaknesses;

  // مزامنة مع العرض
  sync('goal', texts.goal);
  sync('desc1', texts.desc1);
  sync('desc2', texts.desc2);
  sync('desc3', texts.desc3);
  sync('desc4', texts.desc4);
  sync('motivators', texts.motivators);
  sync('strengths', texts.strengths);
  sync('challenges', texts.challenges);
  sync('weaknesses', texts.weaknesses);

  // تعبئة تلقائية للحقول الأخرى
  const reportFields = {
    "تقرير نشاط إثرائي": { 
      target: "الطلاب المتميزين أكاديمياً", 
      count: "18", 
      location: "المختبر العلمي المتقدم" 
    },
    "تقرير خطة علاجية": { 
      target: "الطلاب المتأخرين دراسياً", 
      count: "12", 
      location: "غرفة المصادر التعليمية" 
    }
  };
  
  if (reportFields[reportType]) {
    const fields = reportFields[reportType];
    document.querySelector('input[placeholder="المستهدفون"]').value = fields.target;
    document.querySelector('input[placeholder="العدد"]').value = fields.count;
    document.querySelector('input[placeholder="مكان التنفيذ"]').value = fields.location;
    
    sync('target', fields.target);
    sync('count', fields.count);
    sync('location', fields.location);
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
  document.getElementById('schoolInput').value = "مدرسة التجربة النموذجية";
  sync('school', "مدرسة التجربة النموذجية");
  updateEduInfo("الإدارة العامة للتعليم بمنطقة الرياض");
  
  // جلب التاريخ الهجري عند تحميل الصفحة
  await getHijriDate();
};
</script>
</body>
</html>