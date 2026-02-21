<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>تقرير برنامج الإرشاد</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap');
@page{ size:A4; margin:0; }

body{
  margin:0;
  background:#f4f6f6;
  font-family:'Cairo',sans-serif;
  font-size:12px;
  color:#1f1f1f;
}

.wrapper{display:flex;justify-content:center;}

#a4{
  width:210mm;
  height:297mm;
  background:#fff;
  padding:20mm 18mm;
  box-sizing:border-box;
  overflow:hidden;
}

.container{width:170mm;margin:auto;}

/* ===== الهيدر ===== */
.header{
  background:#0d4f3d;
  height:105px;
  border-radius:6px;
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  position:relative;
  margin-bottom:18px;
}

.header img{width:115px;}

.header-school,
.header-education,
.header-date{
  font-size:11px;
  font-weight:600;
}

.header-school{position:absolute;right:18px;bottom:12px;}
.header-education{position:absolute;left:50%;bottom:6px;transform:translateX(-50%);}
.header-date{position:absolute;left:18px;top:8px;}

/* ===== العنوان الرئيسي ===== */
.title{
  font-size:13.5px;
  font-weight:700;
  margin-bottom:16px;
  padding-right:8px;
  border-right:4px solid #0e8c7a;
  color:#0e8c7a;
}

/* ===== معلومات البرنامج ===== */
.info-box{
  background:#fafafa;
  border:1px solid #e8ecec;
  border-radius:6px;
  padding:12px 14px;
  margin-bottom:20px;
}

.info-row{
  display:flex;
  align-items:center;
  gap:12px;
  padding:6px 0;
  border-bottom:1px solid #f1f1f1;
}

.info-row:last-child{border-bottom:none;}
.info-label{width:135px;font-weight:600;}
.info-value{flex:1;font-size:9.5px;}

/* ===== عناوين الأقسام ===== */
.section-title{
  font-weight:600;
  font-size:11px;
  margin:14px 0 6px 0;
  color:#0d4f3d;
}

/* ===== صندوق نصي (بديل الجدول) ===== */
.execution{
  background:#fcfcfc;
  border:1px solid #eceff0;
  border-radius:6px;
  padding:12px;
  line-height:1.8;
  margin-bottom:20px;
  font-size:9.5px;
}

/* ===== جدول النتائج ===== */
.table{
  width:100%;
  border-collapse:collapse;
  margin-bottom:18px;
}

.table th{
  background:#f7f9f9;
  font-size:10px;
  font-weight:600;
  border:1px solid #eceff0;
  padding:6px;
}

.table td{
  border:1px solid #eceff0;
  padding:6px;
  text-align:right;
  font-size:9.5px;
  line-height:1.8;
}

/* ===== زر ===== */
.btn{
  position:fixed;
  bottom:20px;
  left:20px;
  background:#25D366;
  color:#fff;
  border:none;
  padding:12px 22px;
  border-radius:30px;
  font-weight:700;
  cursor:pointer;
  z-index:999;
}

@media print{ .btn{display:none} }

@media (max-width:768px){
  #a4{width:100%;height:auto;padding:20px;}
  .container{width:100%;}
}
</style>
</head>

<body>

<button class="btn" onclick="sharePDF()">إرسال عبر واتساب</button>

<div class="wrapper">
<div id="a4">
<div class="container">

<div class="header">
  <img src="https://i.ibb.co/1fc5gB6v/9-C92-E57-B-23-FA-479-D-A024-1-D5-F871-B4-F8-D.png">
  <div class="header-school">سعيد بن العاص</div>
  <div class="header-education">إدارة التعليم بمنطقة مكة المكرمة</div>
  <div class="header-date">1447 هـ<br>2026 م</div>
</div>

<div class="title">تقرير برنامج الإرشاد وقت الأزمات</div>

<div class="info-box">
  <div class="info-row"><div class="info-label">اسم البرنامج</div><div class="info-value">برنامج الإرشاد وقت الأزمات</div></div>
  <div class="info-row"><div class="info-label">التاريخ</div><div class="info-value">١٤٤٧هـ</div></div>
  <div class="info-row"><div class="info-label">المجال</div><div class="info-value">تربوي - اجتماعي</div></div>
  <div class="info-row"><div class="info-label">المستهدفون</div><div class="info-value">جميع الطلاب</div></div>
</div>

<div class="section-title">أهداف البرنامج</div>
<div class="execution">
1- مساعدة الطلاب على التكيف النفسي.<br>
2- تنمية مهارات إدارة الضغوط.<br>
3- تقديم الدعم النفسي اللازم.<br>
4- إشراك الأسرة في العملية الإرشادية.
</div>

<div class="section-title">إجراءات التنفيذ</div>
<div class="execution">
1- تنفيذ لقاءات توعوية.<br>
2- تنفيذ أنشطة إرشادية.<br>
3- عقد جلسات فردية للطلاب.<br>
4- نشر مواد توعوية.
</div>

<div class="section-title">النتائج والتوصيات</div>
<table class="table">
<tr>
<th>النتائج</th>
<th>التوصيات</th>
</tr>
<tr>
<td>رفع مستوى الوعي لدى الطلاب.<br>تقليل مظاهر القلق.</td>
<td>تكثيف البرامج التوعوية.<br>إشراك الأسرة بشكل أكبر.</td>
</tr>
</table>

</div>
</div>
</div>

<script>
async function sharePDF() {
  const element = document.getElementById('a4');

  const pdfBlob = await html2pdf().set({
    margin:0,
    html2canvas:{scale:2,useCORS:true},
    jsPDF:{unit:'mm',format:'a4',orientation:'portrait'}
  }).from(element).toPdf().output('blob');

  const file = new File([pdfBlob], "تقرير-برنامج-الإرشاد.pdf", { type: "application/pdf" });

  if (navigator.canShare && navigator.canShare({ files: [file] })) {
    await navigator.share({
      files: [file],
      title: "تقرير برنامج الإرشاد"
    });
  } else {
    alert("المشاركة المباشرة غير مدعومة على هذا الجهاز. يرجى استخدام متصفح Chrome على الجوال.");
  }
}
</script>

</body>
</html>