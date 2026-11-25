<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ประกาศคะแนนภาษาอังกฤษ ป.6/5</title>

  <style>
    * {
      box-sizing: border-box;
      font-family: Arial, "Noto Sans Thai", sans-serif;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: linear-gradient(135deg, #eef4ff
, #f8fbff
);
      color: #1f2937
;
    }

    header {
      padding: 32px 20px;
      text-align: center;
      color: white;
      background: linear-gradient(135deg, #2563eb
, #7c3aed
);
    }

    header h1 {
      margin: 0 0 8px;
      font-size: 30px;
    }

    header p {
      margin: 0;
      opacity: 0.9;
    }

    .container {
      width: min(1000px, 92%);
      margin: 28px auto;
    }

    .search-box {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      padding: 20px;
      margin-bottom: 24px;
      background: white;
      border-radius: 16px;
      box-shadow: 0 8px 24px rgba(37, 99, 235, 0.1);
    }

    .search-box input,
    .search-box select {
      flex: 1;
      min-width: 220px;
      padding: 13px 15px;
      border: 1px solid #dbe3f0
;
      border-radius: 10px;
      font-size: 16px;
      outline: none;
    }

    .search-box input:focus,
    .search-box select:focus {
      border-color: #2563eb
;
      box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.12);
    }

    .results {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(290px, 1fr));
      gap: 20px;
    }

    .student-card {
      overflow: hidden;
      background: white;
      border-radius: 18px;
      box-shadow: 0 8px 24px rgba(15, 23, 42, 0.08);
    }

    .student-header {
      padding: 20px;
      color: white;
      background: linear-gradient(135deg, #3b82f6
, #6366f1
);
    }

    .student-header h2 {
      margin: 0 0 6px;
      font-size: 21px;
    }

    .student-header p {
      margin: 0;
      opacity: 0.9;
    }

    .score-content {
      padding: 20px;
    }

    .score-row {
      display: flex;
      justify-content: space-between;
      padding: 13px 0;
      border-bottom: 1px solid #edf1f7
;
    }

    .score-row:last-child {
      border-bottom: 0;
    }

    .score-label {
      color: #64748b
;
    }

    .score-value {
      font-weight: bold;
      color: #1e293b
;
    }

    .total {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 16px;
      padding: 14px;
      color: #1e3a8a
;
      background: #eff6ff
;
      border-radius: 12px;
    }

    .grade {
      padding: 5px 12px;
      color: white;
      background: #16a34a
;
      border-radius: 999px;
      font-weight: bold;
    }

    .empty {
      grid-column: 1 / -1;
      padding: 40px 20px;
      text-align: center;
      color: #64748b
;
      background: white;
      border-radius: 16px;
    }

    footer {
      padding: 25px;
      color: #64748b
;
      text-align: center;
      font-size: 14px;
    }
  </style>
</head>

<body>
  <header>
    <h1>ประกาศคะแนนวิชาภาษาอังกฤษ</h1>
    <p>นักเรียนชั้นประถมศึกษาปีที่ 6/5</p>
  </header>

  <main class="container">
    <section class="search-box">
      <input
        type="text"
        id="searchInput"
        placeholder="ค้นหาด้วยเลขที่หรือชื่อ..."
      />

      <select id="gradeFilter">
        <option value="ทั้งหมด">แสดงนักเรียนทั้งหมด</option>
        <option value="4">เกรด 4</option>
        <option value="3.5">เกรด 3.5</option>
        <option value="3">เกรด 3</option>
        <option value="2.5">เกรด 2.5</option>
        <option value="2">เกรด 2</option>
        <option value="1">เกรด 1</option>
        <option value="0">เกรด 0</option>
      </select>
    </section>

    <section id="results" class="results"></section>
  </main>

  <footer>
    ระบบประกาศคะแนนภาษาอังกฤษ ป.6/5
  </footer>

  <script>
    /*
      แก้ไขข้อมูลนักเรียนตรงนี้
      collected = คะแนนเก็บ
      exam = คะแนนสอบ
      total = คะแนนรวม จะคำนวณอัตโนมัติ
    */

    const students = [
      {
        number: "1",
        name: "เด็กชายกิตติพงษ์ ใจดี",
        collected: 38,
        exam: 48
      },
      {
        number: "2",
        name: "เด็กหญิงพิมพ์ชนก แสงทอง",
        collected: 35,
        exam: 44
      },
      {
        number: "3",
        name: "เด็กชายธนกร มีสุข",
        collected: 30,
        exam: 39
      },
      {
        number: "4",
        name: "เด็กหญิงณัฐธิดา ตั้งใจเรียน",
        collected: 27,
        exam: 35
      },
      {
        number: "5",
        name: "เด็กชายภัทรพล รุ่งเรือง",
        collected: 22,
        exam: 28
      }
    ];

    function calculateGrade(total) {
      if (total >= 80) return "4";
      if (total >= 75) return "3.5";
      if (total >= 70) return "3";
      if (total >= 65) return "2.5";
      if (total >= 60) return "2";
      if (total >= 50) return "1";
      return "0";
    }

    function getGradeColor(grade) {
      if (grade === "4") return "#16a34a
";
      if (grade === "3.5" || grade === "3") return "#2563eb
";
      if (grade === "2.5" || grade === "2") return "#d97706
";
      return "#dc2626
";
    }

    function renderStudents() {
      const searchText = document
        .getElementById("searchInput")
        .value
        .trim()
        .toLowerCase();

      const selectedGrade = document.getElementById("gradeFilter").value;
      const results = document.getElementById("results");

      const filteredStudents = students
        .map(student => {
          const total = student.collected + student.exam;
          const grade = calculateGrade(total);

          return {
            ...student,
            total,
            grade
          };
        })
        .filter(student => {
          const matchesSearch =
            student.name.toLowerCase().includes(searchText) ||
            student.number.includes(searchText);

          const matchesGrade =
            selectedGrade === "ทั้งหมด" ||
            student.grade === selectedGrade;

          return matchesSearch && matchesGrade;
        });

      if (filteredStudents.length === 0) {
        results.innerHTML = `
          <div class="empty">
            ไม่พบข้อมูลนักเรียนที่ค้นหา
          </div>
        `;
        return;
      }

      results.innerHTML = filteredStudents
        .map(student => {
          const gradeColor = getGradeColor(student.grade);

          return `
            <article class="student-card">
              <div class="student-header">
                <h2>${student.name}</h2>
                <p>เลขที่ ${student.number} | ชั้น ป.6/5</p>
              </div>

              <div class="score-content">
                <div class="score-row">
                  <span class="score-label">คะแนนเก็บ</span>
                  <span class="score-value">${student.collected} / 40</span>
                </div>

                <div class="score-row">
                  <span class="score-label">คะแนนสอบ</span>
                  <span class="score-value">${student.exam} / 60</span>
                </div>

                <div class="total">
                  <strong>คะแนนรวม</strong>
                  <strong>${student.total} / 100</strong>
                </div>

                <div
                  class="total"
                  style="margin-top: 10px; background: #f8fafc
;"
                >
                  <strong>ระดับผลการเรียน</strong>
                  <span
                    class="grade"
                    style="background: ${gradeColor};"
                  >
                    เกรด ${student.grade}
                  </span>
                </div>
              </div>
            </article>
          `;
        })
        .join("");
    }

    document
      .getElementById("searchInput")
      .addEventListener("input", renderStudents);

    document
      .getElementById("gradeFilter")
      .addEventListener("change", renderStudents);

    renderStudents();
  </script>
</body>
</html>

การใช้งาน:

เปิดโปรแกรมแก้ไขข้อความ
คัดลอกโค้ดทั้งหมด
บันทึกชื่อไฟล์เป็น index.html
เปิดไฟล์ด้วยเว็บเบราว์เซอร์
แก้ไขข้อมูลนักเรียนในตัวแปร students ให้เป็นข้อมูลจริงของชั้น ป.6/5
