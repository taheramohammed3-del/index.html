<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Math With Hawra - تطبيق المسابقات التفاعلية</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-pink: #ff6b9d;
            --light-pink: #ffc2d6;
            --primary-yellow: #ffd166;
            --light-yellow: #ffedb3;
            --white: #ffffff;
            --dark-text: #333333;
            --light-bg: #fff9fb;
            --success: #4CAF50;
            --warning: #FF9800;
            --info: #2196F3;
            --danger: #ff6b6b;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Tajawal', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--light-pink), var(--light-yellow));
            color: var(--dark-text);
            min-height: 100vh;
            padding: 20px;
        }
        
        .app-container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .home-page {
            text-align: center;
            padding: 40px 20px;
        }
        
        .logo-container {
            margin-bottom: 30px;
        }
        
        .logo {
            width: 180px;
            height: 180px;
            margin: 0 auto 20px;
            border-radius: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            background: var(--white);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-15px);
            }
        }
        
        .logo-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 25px;
        }
        
        .logo-text {
            font-size: 2.5rem;
            font-weight: bold;
            background: linear-gradient(135deg, var(--primary-pink), var(--primary-yellow));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
        }
        
        .logo-subtext {
            color: var(--dark-text);
            font-size: 1.2rem;
            opacity: 0.8;
        }
        
        .main-title {
            font-size: 2.8rem;
            margin-bottom: 15px;
            color: var(--dark-text);
        }
        
        .subtitle {
            font-size: 1.3rem;
            margin-bottom: 50px;
            color: var(--dark-text);
            line-height: 1.6;
        }
        
        .choice-container {
            display: flex;
            gap: 25px;
            justify-content: center;
            flex-wrap: wrap;
        }
        
        .choice-card {
            background: var(--white);
            padding: 40px 30px;
            border-radius: 20px;
            width: 320px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: transform 0.3s;
            cursor: pointer;
        }
        
        .choice-card:hover {
            transform: translateY(-10px);
        }
        
        .teacher-card {
            border: 4px solid var(--primary-pink);
        }
        
        .student-card {
            border: 4px solid var(--primary-yellow);
        }
        
        .choice-icon {
            font-size: 3.5rem;
            margin-bottom: 20px;
        }
        
        .teacher-card .choice-icon {
            color: var(--primary-pink);
        }
        
        .student-card .choice-icon {
            color: var(--primary-yellow);
        }
        
        .choice-title {
            font-size: 1.5rem;
            margin-bottom: 15px;
            font-weight: bold;
        }
        
        .choice-description {
            color: #666;
            margin-bottom: 25px;
            line-height: 1.6;
        }
        
        .btn {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }
        
        .btn-primary {
            background: var(--primary-pink);
            color: white;
        }
        
        .btn-secondary {
            background: var(--primary-yellow);
            color: var(--dark-text);
        }
        
        .btn-success {
            background: var(--success);
            color: white;
        }
        
        .btn-danger {
            background: var(--danger);
            color: white;
        }
        
        .btn-info {
            background: var(--info);
            color: white;
        }
        
        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
        }
        
        .page {
            display: none;
        }
        
        .page.active {
            display: block;
        }
        
        .page-header {
            display: flex;
            align-items: center;
            margin-bottom: 30px;
            padding: 20px;
            background: var(--white);
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .back-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--primary-pink);
            cursor: pointer;
            padding: 10px;
            margin-left: 15px;
        }
        
        .page-title {
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .teacher-page .page-title {
            color: var(--primary-pink);
        }
        
        .student-page .page-title {
            color: var(--primary-yellow);
        }
        
        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .dashboard-card {
            background: var(--white);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            cursor: pointer;
            transition: transform 0.3s;
        }
        
        .dashboard-card:hover {
            transform: translateY(-5px);
        }
        
        .dashboard-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
        }
        
        .teacher-dashboard .dashboard-icon {
            color: var(--primary-pink);
        }
        
        .student-dashboard .dashboard-icon {
            color: var(--primary-yellow);
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: var(--white);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            margin: 10px 0;
        }
        
        .stat-value.primary {
            color: var(--primary-pink);
        }
        
        .stat-value.secondary {
            color: var(--primary-yellow);
        }
        
        .stat-value.success {
            color: var(--success);
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .modal-content {
            background: var(--white);
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 400px;
            position: relative;
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            left: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            background: var(--light-bg);
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }
        
        .form-control {
            width: 100%;
            padding: 15px;
            border: 2px solid var(--light-pink);
            border-radius: 10px;
            font-size: 1rem;
        }
        
        .form-control:focus {
            border-color: var(--primary-pink);
            outline: none;
        }
        
        .btn-block {
            width: 100%;
            justify-content: center;
        }
        
        .quiz-form {
            background: var(--white);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        
        .question-item {
            background: var(--light-bg);
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 2px dashed var(--light-pink);
            position: relative;
        }
        
        .option-input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
            align-items: center;
        }
        
        .option-input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
        }
        
        .correct-option-radio {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }
        
        .remove-option-btn {
            background: none;
            border: none;
            color: var(--danger);
            cursor: pointer;
            font-size: 1.2rem;
            padding: 5px;
        }
        
        .image-upload {
            border: 2px dashed var(--light-pink);
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            margin-bottom: 15px;
        }
        
        .image-preview {
            max-width: 100%;
            max-height: 200px;
            margin-top: 10px;
            border-radius: 10px;
            display: none;
        }
        
        .remove-image-btn {
            position: absolute;
            top: 10px;
            left: 10px;
            background: rgba(255, 107, 107, 0.9);
            color: white;
            border: none;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            cursor: pointer;
            display: none;
        }
        
        .quiz-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .quiz-item {
            background: var(--white);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .quiz-actions {
            display: flex;
            gap: 10px;
        }
        
        .action-btn {
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
        }
        
        .view-btn {
            background: var(--primary-yellow);
            color: var(--dark-text);
        }
        
        .edit-btn {
            background: var(--info);
            color: white;
        }
        
        .delete-btn {
            background: var(--danger);
            color: white;
        }
        
        .share-btn {
            background: var(--primary-pink);
            color: white;
        }
        
        .quiz-container {
            background: var(--white);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        
        .quiz-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 2px solid var(--light-bg);
        }
        
        .timer {
            background: var(--primary-yellow);
            color: var(--dark-text);
            padding: 10px 20px;
            border-radius: 25px;
            font-weight: bold;
        }
        
        .question-text {
            font-size: 1.3rem;
            margin-bottom: 25px;
            text-align: center;
            line-height: 1.6;
        }
        
        .options-container {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .option {
            background: var(--light-bg);
            padding: 15px 20px;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid transparent;
        }
        
        .option:hover {
            background: var(--light-pink);
        }
        
        .option.selected {
            background: var(--primary-yellow);
            border-color: var(--primary-yellow);
        }
        
        .true-false-container {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-bottom: 25px;
        }
        
        .true-false-btn {
            flex: 1;
            padding: 20px;
            border: 2px solid var(--light-pink);
            border-radius: 15px;
            background: var(--light-bg);
            cursor: pointer;
            transition: all 0.3s;
            font-size: 1.2rem;
            font-weight: bold;
        }
        
        .true-false-btn.selected {
            background: var(--primary-yellow);
            border-color: var(--primary-yellow);
        }
        
        .navigation-buttons {
            display: flex;
            gap: 15px;
        }
        
        .nav-btn {
            padding: 15px 25px;
            border: none;
            border-radius: 25px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            flex: 1;
        }
        
        .prev-btn {
            background: var(--light-pink);
            color: var(--dark-text);
        }
        
        .next-btn {
            background: var(--primary-pink);
            color: white;
        }
        
        .submit-btn {
            background: var(--primary-yellow);
            color: var(--dark-text);
        }
        
        .results-container {
            background: var(--white);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            text-align: center;
        }
        
        .results-title {
            font-size: 2rem;
            margin-bottom: 20px;
            color: var(--primary-pink);
        }
        
        .score-display {
            font-size: 3rem;
            font-weight: bold;
            color: var(--primary-yellow);
            margin: 20px 0;
        }
        
        .stars-container {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 25px 0;
        }
        
        .star-icon {
            font-size: 2.5rem;
            color: var(--primary-yellow);
        }
        
        .ranking-badge {
            display: inline-block;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
            margin: 10px 5px;
        }
        
        .gold {
            background: gold;
            color: var(--dark-text);
        }
        
        .silver {
            background: silver;
            color: var(--dark-text);
        }
        
        .bronze {
            background: #cd7f32;
            color: white;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            left: 20px;
            right: 20px;
            background: var(--white);
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 2000;
            transform: translateY(-100px);
            opacity: 0;
            transition: all 0.3s;
        }
        
        .notification.show {
            transform: translateY(0);
            opacity: 1;
        }
        
        .notification.success {
            border-right: 5px solid var(--success);
        }
        
        .notification.warning {
            border-right: 5px solid var(--warning);
        }
        
        .notification.info {
            border-right: 5px solid var(--info);
        }
        
        .results-table {
            background: var(--white);
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        
        .result-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border-bottom: 1px solid var(--light-bg);
        }
        
        .result-item:last-child {
            border-bottom: none;
        }
        
        .clear-students-section {
            background: var(--white);
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            text-align: center;
            border: 2px solid var(--danger);
        }
        
        .danger-zone {
            background: #fff5f5;
        }
        
        .confirmation-dialog {
            display: none;
            margin-top: 15px;
            padding: 15px;
            background: var(--light-bg);
            border-radius: 10px;
        }
        
        .confirmation-buttons {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 15px;
        }
        
        .review-container {
            background: var(--white);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        
        .review-question {
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid var(--light-bg);
        }
        
        .answer-comparison {
            margin: 15px 0;
            padding: 15px;
            border-radius: 10px;
            background: var(--light-bg);
        }
        
        .correct-indicator {
            color: var(--success);
            font-weight: bold;
        }
        
        .incorrect-indicator {
            color: var(--danger);
            font-weight: bold;
        }
        
        .manual-grading {
            margin-top: 15px;
            padding: 15px;
            background: var(--light-bg);
            border-radius: 10px;
        }
        
        .points-input {
            width: 80px;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 5px;
            text-align: center;
        }
        
        .progress-bar {
            width: 100%;
            height: 10px;
            background: var(--light-bg);
            border-radius: 5px;
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background: var(--primary-pink);
            border-radius: 5px;
            transition: width 0.3s;
        }
        
        @media (max-width: 768px) {
            .choice-container {
                flex-direction: column;
                align-items: center;
            }
            
            .choice-card {
                width: 100%;
                max-width: 350px;
            }
            
            .dashboard {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .quiz-item {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
            
            .quiz-actions {
                justify-content: center;
            }
            
            .quiz-header {
                flex-direction: column;
                gap: 10px;
            }
            
            .option-input-group {
                flex-direction: column;
            }
            
            .true-false-container {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- الصفحة الرئيسية -->
        <div class="page home-page active" id="homePage">
            <div class="logo-container">
                <div class="logo">
                    <img src="https://i.ibb.co/N0YjKhR/logo-png.jpg" alt="Math With Hawra Logo" class="logo-img">
                </div>
                <div class="logo-text">Math With Hawra</div>
                <div class="logo-subtext">منصة التعليم التفاعلي</div>
            </div>
            
            <p class="subtitle">منصة مسابقات تفاعلية تعليمية<br>بإشراف المعلمة حوراء — تعلم ومرح في كل سؤال</p>
            
            <div class="choice-container">
                <div class="choice-card teacher-card" onclick="showTeacherLogin()">
                    <div class="choice-icon">
                        <i class="fas fa-chalkboard-teacher"></i>
                    </div>
                    <h2 class="choice-title">أنا المعلمة</h2>
                    <p class="choice-description">أنشئ مسابقات تفاعلية، أضف الصور، تابع النتائج</p>
                    <button class="btn btn-primary">
                        <i class="fas fa-sign-in-alt"></i>
                        دخول المعلمة
                    </button>
                </div>
                
                <div class="choice-card student-card" onclick="showStudentLogin()">
                    <div class="choice-icon">
                        <i class="fas fa-user-graduate"></i>
                    </div>
                    <h2 class="choice-title">أنا الطالبة</h2>
                    <p class="choice-description">انضم للمسابقات، استمتع بتجربة تفاعلية</p>
                    <button class="btn btn-secondary">
                        <i class="fas fa-sign-in-alt"></i>
                        دخول الطالبة
                    </button>
                </div>
            </div>
        </div>

        <!-- صفحة المعلمة -->
        <div class="page teacher-page" id="teacherPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('homePage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">لوحة تحكم المعلمة</h1>
            </div>

            <div class="stats-grid">
                <div class="stat-card">
                    <i class="fas fa-clipboard-list dashboard-icon"></i>
                    <div class="stat-value primary" id="totalQuizzes">0</div>
                    <p>إجمالي المسابقات</p>
                </div>
                <div class="stat-card">
                    <i class="fas fa-users dashboard-icon"></i>
                    <div class="stat-value secondary" id="totalStudents">0</div>
                    <p>الطالبات المشاركات</p>
                </div>
                <div class="stat-card">
                    <i class="fas fa-chart-line dashboard-icon"></i>
                    <div class="stat-value success" id="avgScore">0%</div>
                    <p>متوسط النتائج</p>
                </div>
            </div>

            <div class="dashboard teacher-dashboard">
                <div class="dashboard-card" onclick="showPage('createQuizPage')">
                    <div class="dashboard-icon">
                        <i class="fas fa-plus-circle"></i>
                    </div>
                    <h3>إنشاء مسابقة جديدة</h3>
                    <p>أنشئ مسابقة تفاعلية مع إمكانية إضافة الصور</p>
                    <button class="btn btn-primary" style="margin-top: 15px;">
                        <i class="fas fa-rocket"></i>
                        بدء الإنشاء
                    </button>
                </div>
                
                <div class="dashboard-card" onclick="showPage('quizzesPage')">
                    <div class="dashboard-icon">
                        <i class="fas fa-list-alt"></i>
                    </div>
                    <h3>المسابقات الحالية</h3>
                    <p>عرض وإدارة المسابقات</p>
                    <button class="btn btn-secondary" style="margin-top: 15px;">
                        <i class="fas fa-eye"></i>
                        عرض الكل
                    </button>
                </div>
                
                <div class="dashboard-card" onclick="showPage('resultsTeacherPage')">
                    <div class="dashboard-icon">
                        <i class="fas fa-chart-bar"></i>
                    </div>
                    <h3>النتائج والإحصائيات</h3>
                    <p>شاهد نتائج الطالبات</p>
                    <button class="btn btn-info" style="margin-top: 15px;">
                        <i class="fas fa-chart-pie"></i>
                        عرض النتائج
                    </button>
                </div>

                <div class="dashboard-card" onclick="showPage('reviewPage')">
                    <div class="dashboard-icon">
                        <i class="fas fa-check-circle"></i>
                    </div>
                    <h3>تصحيح النشاطات</h3>
                    <p>تصحيح إجابات الطالبات يدوياً</p>
                    <button class="btn btn-success" style="margin-top: 15px;">
                        <i class="fas fa-edit"></i>
                        بدء التصحيح
                    </button>
                </div>
            </div>
        </div>

        <!-- صفحة إنشاء المسابقة -->
        <div class="page create-quiz-page" id="createQuizPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('teacherPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
              
                <h1 class="page-title">إنشاء مسابقة جديدة</h1>
                <h1 class="page-title">لوحة تحكم المعلمة</h1>

 <!--🌟 إنشاء مسابقة جديدة 
<div class="create-quiz">
  <h2>✏ إنشاء مسابقة</h2>
  <input id="quizCode" placeholder="رمز المسابقة">
  <input id="question" placeholder="السؤال">
  <input id="correctAnswer" placeholder="الجواب الصحيح">
  <button onclick="saveQuiz()">💾 حفظ المسابقة</button>
</div>
-->
            </div>

            <div class="quiz-form">
                <div class="form-group">
                    <label for="quizTitle">عنوان المسابقة:</label>
                    <input type="text" id="quizTitle" class="form-control" placeholder="أدخل عنوان المسابقة">
                </div>
                
                <div class="form-group">
                    <label for="quizDescription">وصف المسابقة:</label>
                    <textarea id="quizDescription" class="form-control" rows="2" placeholder="أدخل وصفًا للمسابقة"></textarea>
                </div>

                <div class="form-group">
                    <label for="quizTime">وقت المسابقة (بالدقائق):</label>
                    <input type="number" id="quizTime" class="form-control" min="1" max="120" value="10">
                </div>
                
                <div class="form-group">
                    <label>نوع السؤال:</label>
                    <select id="questionType" class="form-control" onchange="changeQuestionType()">
                        <option value="multiple">اختيار من متعدد</option>
                        <option value="truefalse">صح أم خطأ</option>
                        <option value="text">سؤال نصي مفتوح</option>
                    </select>
                </div>
                
                <div id="questionsContainer">
                    <!-- الأسئلة تضاف هنا -->
                </div>
                
                <button class="btn btn-secondary" onclick="addNewQuestion()" style="margin-bottom: 15px;">
                    <i class="fas fa-plus"></i>
                    إضافة سؤال جديد
                </button>
                
                <button class="btn btn-primary btn-block" onclick="saveQuiz()">
                    <i class="fas fa-save"></i>
                    حفظ المسابقة
                </button>
            </div>
        </div>

        <!-- صفحة تعديل المسابقة -->
        <div class="page edit-quiz-page" id="editQuizPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('quizzesPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">تعديل المسابقة</h1>
            </div>

            <div class="quiz-form">
                <div class="form-group">
                    <label for="editQuizTitle">عنوان المسابقة:</label>
                    <input type="text" id="editQuizTitle" class="form-control" placeholder="أدخل عنوان المسابقة">
                </div>
                
                <div class="form-group">
                    <label for="editQuizDescription">وصف المسابقة:</label>
                    <textarea id="editQuizDescription" class="form-control" rows="2" placeholder="أدخل وصفًا للمسابقة"></textarea>
                </div>

                <div class="form-group">
                    <label for="editQuizTime">وقت المسابقة (بالدقائق):</label>
                    <input type="number" id="editQuizTime" class="form-control" min="1" max="120" value="10">
                </div>
                
                <div id="editQuestionsContainer">
                    <!-- الأسئلة المعدلة تضاف هنا -->
                </div>
                
                <button class="btn btn-secondary" onclick="addNewQuestionToEdit()" style="margin-bottom: 15px;">
                    <i class="fas fa-plus"></i>
                    إضافة سؤال جديد
                </button>
                
                <button class="btn btn-primary btn-block" onclick="updateQuiz()">
                    <i class="fas fa-save"></i>
                    تحديث المسابقة
                </button>
            </div>
        </div>

        <!-- صفحة المسابقات الحالية -->
        <div class="page quizzes-page" id="quizzesPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('teacherPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">المسابقات الحالية</h1>
            </div>

            <div class="quiz-list" id="quizzesList">
                <!-- المسابقات تضاف هنا -->
            </div>
        </div>

        <!-- صفحة نتائج المعلمة -->
        <div class="page results-teacher-page" id="resultsTeacherPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('teacherPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">النتائج والإحصائيات</h1>
            </div>

            <!-- قسم مسح الطالبات -->
            <div class="clear-students-section danger-zone">
                <h3 style="color: var(--danger);">
                    <i class="fas fa-exclamation-triangle"></i> منطقة الحذف
                </h3>
                <p style="color: var(--danger); font-weight: bold; margin-bottom: 15px;">
                    تحذير: هذا الإجراء لا يمكن التراجع عنه
                </p>
                <p>يمكنك مسح جميع نتائج الطالبات وإعادة البدء من جديد</p>
                
                <button class="btn btn-danger" onclick="showClearConfirmation()" style="margin-top: 15px;">
                    <i class="fas fa-trash-alt"></i>
                    مسح جميع نتائج الطالبات
                </button>

                <div class="confirmation-dialog" id="clearConfirmationDialog">
                    <p><strong>هل أنت متأكد من أنك تريد مسح جميع نتائج الطالبات؟</strong></p>
                    <p>سيتم حذف جميع النتائج ولا يمكن استعادتها.</p>
                    <div class="confirmation-buttons">
                        <button class="btn btn-danger" onclick="clearAllStudentsResults()">
                            <i class="fas fa-check"></i>
                            نعم، مسح الكل
                        </button>
                        <button class="btn btn-secondary" onclick="hideClearConfirmation()">
                            <i class="fas fa-times"></i>
                            إلغاء
                        </button>
                    </div>
                </div>
            </div>

            <div class="results-table">
                <h3 style="margin-bottom: 20px; color: var(--primary-pink);">نتائج الطالبات</h3>
                <div id="studentsResultsList">
                    <!-- النتائج تضاف هنا -->
                </div>
            </div>
        </div>

        <!-- صفحة تصحيح النشاطات -->
        <div class="page review-page" id="reviewPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('teacherPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">تصحيح النشاطات</h1>
            </div>

            <div class="review-container" id="reviewContainer">
                <!-- النشاطات تضاف هنا -->
            </div>
        </div>

        <!-- صفحة الطالبة -->
        <div class="page student-page" id="studentPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('homePage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">لوحة الطالبة</h1>
          
                <h1 class="page-title">لوحة تحكم المعلمة</h1>

<script>
  // 🌸 دالة تحميل المسابقة للطالبة
  function loadQuiz() {
    const studentCode = document.getElementById("studentCode").value;
    const dbRef = ref(db);

    if (!studentCode) {
      alert("⚠ الرجاء إدخال رمز المسابقة!");
      return;
    }

    get(child(dbRef, "quizzes/" + studentCode))
      .then((snapshot) => {
        if (snapshot.exists()) {
          const data = snapshot.val();
          const display = document.getElementById("quizDisplay");
          display.innerHTML = `
            <h3>📖 السؤال:</h3>
            <p>${data.question}</p>
            <h4>✏ اكتبي إجابتك هنا:</h4>
            <input id="studentAnswer" placeholder="جوابك هنا">
            <button onclick="checkAnswer('${data.correctAnswer}')">تحقّق من الإجابة</button>
          `;
        } else {
          alert("❌ لا توجد مسابقة بهذا الرمز!");
        }
      })
      .catch((error) => alert("⚠ حدث خطأ أثناء تحميل البيانات: " + error));
  }

  // 🌟 دالة التحقق من الإجابة
  function checkAnswer(correctAnswer) {
    const studentAnswer = document.getElementById("studentAnswer").value;
    if (studentAnswer.trim() === correctAnswer.trim()) {
      alert("🎉 إجابة صحيحة! أحسنتِ 👏");
    } else {
      alert("❌ إجابة خاطئة، حاولي مجددًا!");
    }
  }
</script>
            </div>

            <div class="dashboard student-dashboard">
                <div class="dashboard-card" onclick="showStudentLogin()">
                    <div class="dashboard-icon">
                        <i class="fas fa-play-circle"></i>
                    </div>
                    <h3>الانضمام لمسابقة</h3>
                    <p>ادخلي رمز المسابقة للبدء</p>
                    <button class="btn btn-secondary" style="margin-top: 15px;">
                        <i class="fas fa-sign-in-alt"></i>
                        انضم الآن
                    </button>
                </div>
                
                <div class="dashboard-card">
                    <div class="dashboard-icon">
                        <i class="fas fa-trophy"></i>
                    </div>
                    <h3>نتائجي</h3>
                    <p>شاهدي تقدمك في المسابقات</p>
                    <button class="btn btn-primary" style="margin-top: 15px;" onclick="showMyResults()">
                        <i class="fas fa-chart-bar"></i>
                        عرض النتائج
                    </button>
                </div>
            </div>
        </div>
    -->
        <!-- صفحة المسابقة -->
        <div class="page quiz-page" id="quizPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('studentPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title" id="quizTitleDisplay">مسابقة الرياضيات</h1>
            </div>

            <div class="progress-bar">
                <div class="progress" id="quizProgress" style="width: 0%"></div>
            </div>

            <div class="quiz-container">
                <div class="quiz-header">
                    <div class="timer" id="timer">⏰ 10:00</div>
                    <div class="question-counter" id="questionCounter">السؤال 1 من 3</div>
                </div>
                
                <div id="questionImageContainer"></div>
                
                <div class="question-text" id="questionText">ما هو ناتج جمع ٥ + ٧؟</div>
                
                <div class="options-container" id="optionsContainer">
                    <div class="option" onclick="selectOption(this, 0)">١٠</div>
                    <div class="option" onclick="selectOption(this, 1)">١١</div>
                    <div class="option" onclick="selectOption(this, 2)">١٢</div>
                    <div class="option" onclick="selectOption(this, 3)">١٣</div>
                </div>

                <div id="textAnswerContainer" style="display: none;">
                    <textarea id="textAnswer" rows="4" placeholder="أدخل إجابتك هنا..." style="width: 100%; padding: 15px; border: 2px solid var(--light-pink); border-radius: 10px; font-size: 1rem;"></textarea>
                </div>
                
                <div class="navigation-buttons">
                    <button class="nav-btn prev-btn" onclick="prevQuestion()">
                        <i class="fas fa-arrow-right"></i>
                        السابق
                    </button>
                    <button class="nav-btn next-btn" onclick="nextQuestion()">
                        التالي
                        <i class="fas fa-arrow-left"></i>
                    </button>
                    <button class="nav-btn submit-btn" onclick="finishQuiz()" style="display: none;">
                        <i class="fas fa-flag-checkered"></i>
                        إنهاء المسابقة
                    </button>
                </div>
            </div>
        </div>

        <!-- صفحة النتائج -->
        <div class="page results-page" id="resultsPage">
            <div class="page-header">
                <button class="back-btn" onclick="showPage('studentPage')">
                    <i class="fas fa-arrow-right"></i>
                </button>
                <h1 class="page-title">نتائج المسابقة</h1>
            </div>

            <div class="results-container">
                <h2 class="results-title">🎉 تهانينا! 🎉</h2>
                <p>لقد أنهيت المسابقة بنجاح</p>
                <div class="score-display" id="finalScore">85%</div>
                <div class="stars-container">
                    <i class="fas fa-star star-icon"></i>
                    <i class="fas fa-star star-icon"></i>
                    <i class="fas fa-star star-icon"></i>
                </div>
                <p>إجمالي النقاط: <span id="totalPoints">17</span> من <span id="maxPoints">20</span></p>
                
                <div id="rankingBadge" style="margin: 20px 0;"></div>
                
                <button class="btn btn-secondary btn-block" onclick="showPage('homePage')" style="margin-top: 30px;">
                    <i class="fas fa-home"></i>
                    العودة للصفحة الرئيسية
                </button>
            </div>
        </div>
    </div>

    <!-- نوافذ الدخول -->
    <div class="modal" id="studentLoginModal">
        <div class="modal-content">
            <span class="close-modal" onclick="hideModal('studentLoginModal')">×</span>
            <h2 style="text-align: center; margin-bottom: 25px; color: var(--primary-yellow);">
                <i class="fas fa-user-graduate"></i><br>
                دخول الطالبة
            </h2>
            <div class="form-group">
                <label for="studentName">اسم الطالبة:</label>
                <input type="text" id="studentName" class="form-control" placeholder="أدخل اسمك الثلاثي">
            </div>
            <div class="form-group">
                <label for="quizCode">رمز المسابقة:</label>
                <input type="text" id="quizCode" class="form-control" placeholder="أدخل رمز المسابقة">
            </div>
            <button class="btn btn-secondary btn-block" onclick="confirmStudentLogin()">
                <i class="fas fa-play-circle"></i>
                بدء المسابقة
            </button>
        </div>
    </div>
    
    <div class="modal" id="teacherLoginModal">
        <div class="modal-content">
            <span class="close-modal" onclick="hideModal('teacherLoginModal')">×</span>
            <h2 style="text-align: center; margin-bottom: 25px; color: var(--primary-pink);">
                <i class="fas fa-chalkboard-teacher"></i><br>
                دخول المعلمة
            </h2>
            <div class="form-group">
                <label for="teacherName">اسم المعلمة:</label>
                <input type="text" id="teacherName" class="form-control" placeholder="أدخل اسمك">
            </div>
            <div class="form-group">
                <label for="teacherPassword">كلمة المرور:</label>
                <input type="password" id="teacherPassword" class="form-control" placeholder="أدخل كلمة المرور">
            </div>
            <button class="btn btn-primary btn-block" onclick="confirmTeacherLogin()">
                <i class="fas fa-sign-in-alt"></i>
                دخول
            </button>
        </div>
    </div>
    
    <!-- إشعارات -->
    <div class="notification" id="notification">
        <div class="notification-content">
            <i class="fas fa-info-circle" style="margin-left: 10px;"></i>
            <span id="notificationText">هذا إشعار تجريبي</span>
        </div>
        <button class="close-notification" onclick="hideNotification()">
            <i class="fas fa-times"></i>
        </button>
    </div>

    <script>
        // بيانات التطبيق
        let currentQuestion = 0;
        let userAnswers = [];
        let timerInterval;
        let timeLeft = 600;
        let currentQuiz = null;
        let questionCount = 0;
        let currentEditingQuizIndex = -1;

        // عرض الصفحات
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
            
            if (pageId === 'teacherPage') {
                updateTeacherStats();
            }
            if (pageId === 'quizzesPage') {
                loadQuizzes();
            }
            if (pageId === 'resultsTeacherPage') {
                loadStudentResults();
            }
            if (pageId === 'reviewPage') {
                loadActivitiesForReview();
            }
        }

        // النوافذ
        function showTeacherLogin() {
            document.getElementById('teacherLoginModal').style.display = 'flex';
        }

        function showStudentLogin() {
            document.getElementById('studentLoginModal').style.display = 'flex';
        }

        function hideModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // تسجيل الدخول
        function confirmTeacherLogin() {
            const teacherName = document.getElementById('teacherName').value;
            const teacherPassword = document.getElementById('teacherPassword').value;
            
            if (teacherName && teacherPassword) {
                hideModal('teacherLoginModal');
                showPage('teacherPage');
                showNotification(`مرحباً ${teacherName}!`, 'success');
                
                // حفظ بيانات الدخول
                localStorage.setItem('mathWithHawra_teacher', JSON.stringify({
                    name: teacherName,
                    loginTime: new Date().toISOString()
                }));
            } else {
                showNotification('يرجى إدخال اسم المعلمة وكلمة المرور', 'warning');
            }
        }

        function confirmStudentLogin() {
            const studentName = document.getElementById('studentName').value;
            const quizCode = document.getElementById('quizCode').value;
            
            if (studentName && quizCode) {
                const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
                const quiz = savedQuizzes.find(q => q.code === quizCode);
                
                if (quiz) {
                    hideModal('studentLoginModal');
                    startQuiz(quiz, studentName);
                } else {
                    showNotification('رمز المسابقة غير صحيح', 'warning');
                }
            } else {
                showNotification('يرجى إدخال اسم الطالبة ورمز المسابقة', 'warning');
            }
        }

        // نظام إنشاء المسابقات
        function changeQuestionType() {
            // سيتم تنفيذها عند إضافة سؤال جديد
        }

        function addNewQuestion() {
            questionCount++;
            const questionsContainer = document.getElementById('questionsContainer');
            const questionType = document.getElementById('questionType').value;
            
            const questionDiv = document.createElement('div');
            questionDiv.className = 'question-item';
            questionDiv.innerHTML = `
                <h4>السؤال ${questionCount}</h4>
                <button class="remove-option-btn" onclick="this.parentElement.remove(); questionCount--;" style="position: absolute; top: 15px; left: 15px;">
                    <i class="fas fa-times"></i>
                </button>
                <div class="form-group">
                    <label>نص السؤال:</label>
                    <input type="text" class="question-text-input" placeholder="أدخل نص السؤال">
                </div>
                <div class="form-group">
                    <label>رفع صورة للسؤال (اختياري):</label>
                    <div class="image-upload" onclick="this.querySelector('input').click()">
                        <i class="fas fa-cloud-upload-alt upload-icon"></i>
                        <p>انقر لرفع صورة</p>
                        <input type="file" class="question-image-input" accept="image/*" style="display: none;">
                        <img class="image-preview">
                    </div>
                </div>
                ${questionType === "multiple" ? `
                    <div class="form-group">
                        <label>خيارات الإجابة:</label>
                        <div class="option-input-group">
                            <input type="text" class="option-input" placeholder="الخيار الأول">
                            <input type="radio" name="correct-${questionCount}" value="0" class="correct-option-radio">
                            <button class="remove-option-btn" onclick="removeNewOption(this)">
                                <i class="fas fa-times"></i>
                            </button>
                        </div>
                        <div class="option-input-group">
                            <input type="text" class="option-input" placeholder="الخيار الثاني">
                            <input type="radio" name="correct-${questionCount}" value="1" class="correct-option-radio">
                            <button class="remove-option-btn" onclick="removeNewOption(this)">
                                <i class="fas fa-times"></i>
                            </button>
                        </div>
                        <button class="btn btn-secondary" onclick="addNewOption(this.parentElement)" style="padding: 8px 15px; margin-top: 10px;">
                            <i class="fas fa-plus"></i>
                            إضافة خيار
                        </button>
                    </div>
                ` : questionType === "truefalse" ? `
                    <div class="form-group">
                        <label>الإجابة الصحيحة:</label>
                        <div style="display: flex; gap: 10px;">
                            <label style="display: flex; align-items: center; gap: 5px;">
                                <input type="radio" name="correct-${questionCount}" value="0" class="correct-option-radio">
                                صح
                            </label>
                            <label style="display: flex; align-items: center; gap: 5px;">
                                <input type="radio" name="correct-${questionCount}" value="1" class="correct-option-radio">
                                خطأ
                            </label>
                        </div>
                    </div>
                ` : `
                    <div class="form-group">
                        <label>الإجابة النموذجية (للتقييم اليدوي):</label>
                        <textarea class="model-answer" placeholder="أدخل الإجابة النموذجية هنا..." rows="3"></textarea>
                    </div>
                `}
            `;
            
            questionsContainer.appendChild(questionDiv);
            
            // إضافة حدث لرفع الصور
            const imageInput = questionDiv.querySelector('.question-image-input');
            const imagePreview = questionDiv.querySelector('.image-preview');
            
            imageInput.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        imagePreview.src = e.target.result;
                        imagePreview.style.display = 'block';
                    }
                    reader.readAsDataURL(file);
                }
            });
        }

        function addNewOption(container) {
            const optionGroups = container.querySelectorAll('.option-input-group');
            const newIndex = optionGroups.length;
            
            const newOptionGroup = document.createElement('div');
            newOptionGroup.className = 'option-input-group';
            newOptionGroup.innerHTML = `
                <input type="text" class="option-input" placeholder="الخيار ${newIndex + 1}">
                <input type="radio" name="${container.querySelector('.correct-option-radio').name}" value="${newIndex}" class="correct-option-radio">
                <button class="remove-option-btn" onclick="removeNewOption(this)">
                    <i class="fas fa-times"></i>
                </button>
            `;
            
            container.insertBefore(newOptionGroup, container.lastElementChild);
        }

        function removeNewOption(button) {
            const optionGroup = button.parentElement;
            if (optionGroup.parentElement.querySelectorAll('.option-input-group').length > 1) {
                optionGroup.remove();
            } else {
                showNotification('يجب أن يكون هناك خيار واحد على الأقل', 'warning');
            }
        }

        function saveQuiz() {
            const quizTitle = document.getElementById('quizTitle').value;
            if (!quizTitle) {
                showNotification('يرجى إدخال عنوان للمسابقة', 'warning');
                return;
            }

            const questions = [];
            const questionElements = document.querySelectorAll('.question-item');
            
            questionElements.forEach((questionElement) => {
                const questionText = questionElement.querySelector('.question-text-input').value;
                const questionType = document.getElementById('questionType').value;
                
                if (questionText) {
                    const question = {
                        question: questionText,
                        type: questionType,
                        options: [],
                        correctAnswer: 0,
                        image: ""
                    };

                    if (questionType === "multiple") {
                        const optionInputs = questionElement.querySelectorAll('.option-input');
                        const correctRadio = questionElement.querySelector('.correct-option-radio:checked');
                        
                        optionInputs.forEach((input) => {
                            if (input.value) {
                                question.options.push(input.value);
                            }
                        });
                        
                        if (correctRadio) {
                            question.correctAnswer = parseInt(correctRadio.value);
                        }
                    } else if (questionType === "truefalse") {
                        question.options = ["صح", "خطأ"];
                        const correctRadio = questionElement.querySelector('.correct-option-radio:checked');
                        if (correctRadio) {
                            question.correctAnswer = parseInt(correctRadio.value);
                        }
                    } else {
                        const modelAnswer = questionElement.querySelector('.model-answer');
                        question.modelAnswer = modelAnswer ? modelAnswer.value : "";
                    }

                    // حفظ الصورة إذا وجدت
                    const imagePreview = questionElement.querySelector('.image-preview');
                    if (imagePreview && imagePreview.style.display !== 'none') {
                        question.image = imagePreview.src;
                    }

                    questions.push(question);
                }
            });

            if (questions.length === 0) {
                showNotification('يرجى إضافة أسئلة على الأقل', 'warning');
                return;
            }

            const quizData = {
                title: quizTitle,
                description: document.getElementById('quizDescription').value,
                code: generateQuizCode(),
                questions: questions,
                time: parseInt(document.getElementById('quizTime').value) || 10,
                createdAt: new Date().toISOString()
            };

            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            savedQuizzes.push(quizData);
            localStorage.setItem('mathWithHawra_quizzes', JSON.stringify(savedQuizzes));

            showNotification(`تم حفظ المسابقة بنجاح! رمز المسابقة: ${quizData.code}`, 'success');
            showPage('quizzesPage');
        }

        function generateQuizCode() {
            return 'MTH' + Math.random().toString(36).substr(2, 6).toUpperCase();
        }

        // إدارة المسابقات
        function loadQuizzes() {
            const quizzesList = document.getElementById('quizzesList');
            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            
            if (savedQuizzes.length === 0) {
                quizzesList.innerHTML = `
                    <div style="text-align: center; padding: 40px; color: #666;">
                        <i class="fas fa-clipboard-list" style="font-size: 3rem; margin-bottom: 15px;"></i>
                        <h3>لا توجد مسابقات حالية</h3>
                        <p>قم بإنشاء مسابقة جديدة للبدء</p>
                    </div>
                `;
                return;
            }
            
            quizzesList.innerHTML = '';
            savedQuizzes.forEach((quiz, index) => {
                const quizItem = document.createElement('div');
                quizItem.className = 'quiz-item';
                quizItem.innerHTML = `
                    <div class="quiz-info">
                        <h3>${quiz.title}</h3>
                        <p>${quiz.description || 'لا يوجد وصف'}</p>
                        <p>${quiz.questions.length} أسئلة - ${quiz.time} دقائق</p>
                        <p><small>رمز المسابقة: ${quiz.code}</small></p>
                    </div>
                    <div class="quiz-actions">
                        <button class="action-btn view-btn" onclick="viewQuiz(${index})">
                            <i class="fas fa-eye"></i>
                            عرض
                        </button>
                        <button class="action-btn edit-btn" onclick="editQuiz(${index})">
                            <i class="fas fa-edit"></i>
                            تعديل
                        </button>
                        <button class="action-btn share-btn" onclick="shareQuiz('${quiz.code}')">
                            <i class="fas fa-share"></i>
                            مشاركة
                        </button>
                        <button class="action-btn delete-btn" onclick="deleteQuiz(${index})">
                            <i class="fas fa-trash"></i>
                            حذف
                        </button>
                    </div>
                `;
                quizzesList.appendChild(quizItem);
            });
        }

        function viewQuiz(index) {
            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            const quiz = savedQuizzes[index];
            
            let quizDetails = `مسابقة: ${quiz.title}\n`;
            quizDetails += `الأسئلة: ${quiz.questions.length}\n`;
            quizDetails += `الرمز: ${quiz.code}\n`;
            quizDetails += `الوقت: ${quiz.time} دقيقة\n\n`;
            quizDetails += `الأسئلة:\n`;
            
            quiz.questions.forEach((question, qIndex) => {
                quizDetails += `\n${qIndex + 1}. ${question.question}\n`;
                if (question.type === 'multiple') {
                    question.options.forEach((option, oIndex) => {
                        const isCorrect = oIndex === question.correctAnswer;
                        quizDetails += `   ${isCorrect ? '✓' : ' '} ${option}${isCorrect ? ' (صحيح)' : ''}\n`;
                    });
                } else if (question.type === 'truefalse') {
                    quizDetails += `   ✓ ${question.correctAnswer === 0 ? 'صح' : 'خطأ'} (صحيح)\n`;
                }
            });
            
            alert(quizDetails);
        }

        // دالة تعديل المسابقة
        function editQuiz(index) {
            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            const quiz = savedQuizzes[index];
            
            if (!quiz) {
                showNotification('لم يتم العثور على المسابقة', 'warning');
                return;
            }
            
            currentEditingQuizIndex = index;
            
            // تعبئة البيانات في نموذج التعديل
            document.getElementById('editQuizTitle').value = quiz.title;
            document.getElementById('editQuizDescription').value = quiz.description || '';
            document.getElementById('editQuizTime').value = quiz.time || 10;
            
            // مسح الأسئلة الحالية وإضافة الأسئلة الموجودة
            const editQuestionsContainer = document.getElementById('editQuestionsContainer');
            editQuestionsContainer.innerHTML = '';
            
            quiz.questions.forEach((question, qIndex) => {
                addQuestionToEditForm(question, qIndex);
            });
            
            showPage('editQuizPage');
            showNotification('يمكنك الآن تعديل المسابقة', 'info');
        }

        function addQuestionToEditForm(question, index) {
            const editQuestionsContainer = document.getElementById('editQuestionsContainer');
            
            const questionDiv = document.createElement('div');
            questionDiv.className = 'question-item';
            questionDiv.innerHTML = `
                <h4>السؤال ${index + 1}</h4>
                <button class="remove-option-btn" onclick="this.parentElement.remove()" style="position: absolute; top: 15px; left: 15px;">
                    <i class="fas fa-times"></i>
                </button>
                <div class="form-group">
                    <label>نص السؤال:</label>
                    <input type="text" class="question-text-input" value="${question.question}" placeholder="أدخل نص السؤال">
                </div>
                <div class="form-group">
                    <label>رفع صورة للسؤال (اختياري):</label>
                    <div class="image-upload" onclick="this.querySelector('input').click()">
                        <i class="fas fa-cloud-upload-alt upload-icon"></i>
                        <p>انقر لرفع صورة</p>
                        <input type="file" class="question-image-input" accept="image/*" style="display: none;">
                        <img class="image-preview" ${question.image ? `src="${question.image}" style="display: block;"` : ''}>
                    </div>
                </div>
                ${question.type === "multiple" ? `
                    <div class="form-group">
                        <label>خيارات الإجابة:</label>
                        <div id="options-container-${index}">
                            ${question.options.map((option, oIndex) => `
                                <div class="option-input-group">
                                    <input type="text" class="option-input" value="${option}" placeholder="الخيار ${oIndex + 1}">
                                    <input type="radio" name="correct-${index}" value="${oIndex}" ${oIndex === question.correctAnswer ? 'checked' : ''} class="correct-option-radio">
                                    <button class="remove-option-btn" onclick="removeNewOption(this)">
                                        <i class="fas fa-times"></i>
                                    </button>
                                </div>
                            `).join('')}
                        </div>
                        <button class="btn btn-secondary" onclick="addNewOptionToEdit(${index})" style="padding: 8px 15px; margin-top: 10px;">
                            <i class="fas fa-plus"></i>
                            إضافة خيار
                        </button>
                    </div>
                ` : question.type === "truefalse" ? `
                    <div class="form-group">
                        <label>الإجابة الصحيحة:</label>
                        <div style="display: flex; gap: 10px;">
                            <label style="display: flex; align-items: center; gap: 5px;">
                                <input type="radio" name="correct-${index}" value="0" ${question.correctAnswer === 0 ? 'checked' : ''} class="correct-option-radio">
                                صح
                            </label>
                            <label style="display: flex; align-items: center; gap: 5px;">
                                <input type="radio" name="correct-${index}" value="1" ${question.correctAnswer === 1 ? 'checked' : ''} class="correct-option-radio">
                                خطأ
                            </label>
                        </div>
                    </div>
                ` : `
                    <div class="form-group">
                        <label>الإجابة النموذجية (للتقييم اليدوي):</label>
                        <textarea class="model-answer" placeholder="أدخل الإجابة النموذجية هنا..." rows="3">${question.modelAnswer || ''}</textarea>
                    </div>
                `}
            `;
            
            editQuestionsContainer.appendChild(questionDiv);
            
            // إضافة حدث لرفع الصور
            const imageInput = questionDiv.querySelector('.question-image-input');
            const imagePreview = questionDiv.querySelector('.image-preview');
            
            imageInput.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        imagePreview.src = e.target.result;
                        imagePreview.style.display = 'block';
                    }
                    reader.readAsDataURL(file);
                }
            });
        }

        function addNewQuestionToEdit() {
            const editQuestionsContainer = document.getElementById('editQuestionsContainer');
            const questionCount = editQuestionsContainer.querySelectorAll('.question-item').length;
            
            const questionDiv = document.createElement('div');
            questionDiv.className = 'question-item';
            questionDiv.innerHTML = `
                <h4>سؤال جديد</h4>
                <button class="remove-option-btn" onclick="this.parentElement.remove()" style="position: absolute; top: 15px; left: 15px;">
                    <i class="fas fa-times"></i>
                </button>
                <div class="form-group">
                    <label>نص السؤال:</label>
                    <input type="text" class="question-text-input" placeholder="أدخل نص السؤال">
                </div>
                <div class="form-group">
                    <label>رفع صورة للسؤال (اختياري):</label>
                    <div class="image-upload" onclick="this.querySelector('input').click()">
                        <i class="fas fa-cloud-upload-alt upload-icon"></i>
                        <p>انقر لرفع صورة</p>
                        <input type="file" class="question-image-input" accept="image/*" style="display: none;">
                        <img class="image-preview">
                    </div>
                </div>
                <div class="form-group">
                    <label>خيارات الإجابة:</label>
                    <div class="option-input-group">
                        <input type="text" class="option-input" placeholder="الخيار الأول">
                        <input type="radio" name="correct-new" value="0" class="correct-option-radio">
                        <button class="remove-option-btn" onclick="removeNewOption(this)">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                    <div class="option-input-group">
                        <input type="text" class="option-input" placeholder="الخيار الثاني">
                        <input type="radio" name="correct-new" value="1" class="correct-option-radio">
                        <button class="remove-option-btn" onclick="removeNewOption(this)">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                    <button class="btn btn-secondary" onclick="addNewOption(this.parentElement)" style="padding: 8px 15px; margin-top: 10px;">
                        <i class="fas fa-plus"></i>
                        إضافة خيار
                    </button>
                </div>
            `;
            
            editQuestionsContainer.appendChild(questionDiv);
            
            // إضافة حدث لرفع الصور
            const imageInput = questionDiv.querySelector('.question-image-input');
            const imagePreview = questionDiv.querySelector('.image-preview');
            
            imageInput.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        imagePreview.src = e.target.result;
                        imagePreview.style.display = 'block';
                    }
                    reader.readAsDataURL(file);
                }
            });
        }

        function addNewOptionToEdit(questionIndex) {
            const optionsContainer = document.getElementById(`options-container-${questionIndex}`);
            const optionGroups = optionsContainer.querySelectorAll('.option-input-group');
            const newIndex = optionGroups.length;
            
            const newOptionGroup = document.createElement('div');
            newOptionGroup.className = 'option-input-group';
            newOptionGroup.innerHTML = `
                <input type="text" class="option-input" placeholder="الخيار ${newIndex + 1}">
                <input type="radio" name="correct-${questionIndex}" value="${newIndex}" class="correct-option-radio">
                <button class="remove-option-btn" onclick="removeNewOption(this)">
                    <i class="fas fa-times"></i>
                </button>
            `;
            
            optionsContainer.appendChild(newOptionGroup);
        }

        function updateQuiz() {
            const quizTitle = document.getElementById('editQuizTitle').value;
            if (!quizTitle) {
                showNotification('يرجى إدخال عنوان للمسابقة', 'warning');
                return;
            }

            const questions = [];
            const questionElements = document.querySelectorAll('#editQuestionsContainer .question-item');
            
            questionElements.forEach((questionElement, index) => {
                const questionText = questionElement.querySelector('.question-text-input').value;
                
                if (questionText) {
                    // تحديد نوع السؤال بناءً على العناصر الموجودة
                    let questionType = "multiple";
                    if (questionElement.querySelector('.model-answer')) {
                        questionType = "text";
                    } else if (questionElement.querySelector('input[type="radio"][value="0"]') && 
                               questionElement.querySelector('input[type="radio"][value="1"]') &&
                               !questionElement.querySelector('.option-input-group')) {
                        questionType = "truefalse";
                    }

                    const question = {
                        question: questionText,
                        type: questionType,
                        options: [],
                        correctAnswer: 0,
                        image: ""
                    };

                    if (questionType === "multiple") {
                        const optionInputs = questionElement.querySelectorAll('.option-input');
                        const correctRadio = questionElement.querySelector('.correct-option-radio:checked');
                        
                        optionInputs.forEach((input) => {
                            if (input.value) {
                                question.options.push(input.value);
                            }
                        });
                        
                        if (correctRadio) {
                            question.correctAnswer = parseInt(correctRadio.value);
                        }
                    } else if (questionType === "truefalse") {
                        question.options = ["صح", "خطأ"];
                        const correctRadio = questionElement.querySelector('.correct-option-radio:checked');
                        if (correctRadio) {
                            question.correctAnswer = parseInt(correctRadio.value);
                        }
                    } else {
                        const modelAnswer = questionElement.querySelector('.model-answer');
                        question.modelAnswer = modelAnswer ? modelAnswer.value : "";
                    }

                    // حفظ الصورة إذا وجدت
                    const imagePreview = questionElement.querySelector('.image-preview');
                    if (imagePreview && imagePreview.style.display !== 'none') {
                        question.image = imagePreview.src;
                    }

                    questions.push(question);
                }
            });

            if (questions.length === 0) {
                showNotification('يرجى إضافة أسئلة على الأقل', 'warning');
                return;
            }

            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            
            if (currentEditingQuizIndex >= 0 && currentEditingQuizIndex < savedQuizzes.length) {
                // تحديث المسابقة الحالية
                savedQuizzes[currentEditingQuizIndex].title = quizTitle;
                savedQuizzes[currentEditingQuizIndex].description = document.getElementById('editQuizDescription').value;
                savedQuizzes[currentEditingQuizIndex].time = parseInt(document.getElementById('editQuizTime').value) || 10;
                savedQuizzes[currentEditingQuizIndex].questions = questions;
                
                localStorage.setItem('mathWithHawra_quizzes', JSON.stringify(savedQuizzes));
                
                showNotification('تم تحديث المسابقة بنجاح!', 'success');
                showPage('quizzesPage');
                currentEditingQuizIndex = -1;
            } else {
                showNotification('حدث خطأ في تحديث المسابقة', 'warning');
            }
        }

        function shareQuiz(code) {
            const link = `mathwithhawra.com/quiz/${code}`;
            navigator.clipboard.writeText(link).then(() => {
                showNotification('تم نسخ رابط المسابقة', 'success');
            });
        }

        function deleteQuiz(index) {
            if (confirm('هل أنت متأكد من حذف هذه المسابقة؟')) {
                const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
                savedQuizzes.splice(index, 1);
                localStorage.setItem('mathWithHawra_quizzes', JSON.stringify(savedQuizzes));
                loadQuizzes();
                showNotification('تم حذف المسابقة', 'success');
            }
        }

        // باقي الدوال الأساسية
        function updateTeacherStats() {
            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            const savedResults = JSON.parse(localStorage.getItem('mathWithHawra_results')) || [];
            
            document.getElementById('totalQuizzes').textContent = savedQuizzes.length;
            
            const uniqueStudents = [...new Set(savedResults.map(result => result.studentName))];
            document.getElementById('totalStudents').textContent = uniqueStudents.length;
            
            if (savedResults.length > 0) {
                const totalScore = savedResults.reduce((sum, result) => sum + result.score, 0);
                const avgScore = Math.round(totalScore / savedResults.length);
                document.getElementById('avgScore').textContent = `${avgScore}%`;
            }
        }

        function loadStudentResults() {
            const studentsResultsList = document.getElementById('studentsResultsList');
            const savedResults = JSON.parse(localStorage.getItem('mathWithHawra_results')) || [];
            
            if (savedResults.length === 0) {
                studentsResultsList.innerHTML = `
                    <div style="text-align: center; padding: 40px; color: #666;">
                        <i class="fas fa-chart-bar" style="font-size: 3rem; margin-bottom: 15px;"></i>
                        <h3>لا توجد نتائج حالياً</h3>
                        <p>لم تشارك أي طالبة في المسابقات بعد</p>
                    </div>
                `;
                return;
            }
            
            studentsResultsList.innerHTML = '';
            const studentResults = {};
            savedResults.forEach(result => {
                if (!studentResults[result.studentName]) {
                    studentResults[result.studentName] = [];
                }
                studentResults[result.studentName].push(result);
            });
            
            Object.keys(studentResults).forEach(studentName => {
                const results = studentResults[studentName];
                const latestResult = results[results.length - 1];
                
                const resultItem = document.createElement('div');
                resultItem.className = 'result-item';
                resultItem.innerHTML = `
                    <div>
                        <h4>${studentName}</h4>
                        <p>${latestResult.quizTitle}</p>
                        <p><small>${new Date(latestResult.date).toLocaleDateString('ar-SA')}</small></p>
                    </div>
                    <div style="text-align: left;">
                        <div class="score-display" style="font-size: 1.5rem;">${latestResult.score}%</div>
                        <p>${latestResult.correctAnswers}/${latestResult.totalQuestions} نقطة</p>
                        ${latestResult.manuallyGraded ? '<p><small>✓ مصححة يدوياً</small></p>' : ''}
                    </div>
                `;
                studentsResultsList.appendChild(resultItem);
            });
        }

        function showClearConfirmation() {
            document.getElementById('clearConfirmationDialog').style.display = 'block';
        }

        function hideClearConfirmation() {
            document.getElementById('clearConfirmationDialog').style.display = 'none';
        }

        function clearAllStudentsResults() {
            localStorage.removeItem('mathWithHawra_results');
            loadStudentResults();
            updateTeacherStats();
            showNotification('تم مسح جميع نتائج الطالبات بنجاح', 'success');
            hideClearConfirmation();
        }

        function loadActivitiesForReview() {
            const reviewContainer = document.getElementById('reviewContainer');
            const savedResults = JSON.parse(localStorage.getItem('mathWithHawra_results')) || [];
            const savedQuizzes = JSON.parse(localStorage.getItem('mathWithHawra_quizzes')) || [];
            
            if (savedResults.length === 0) {
                reviewContainer.innerHTML = `
                    <div style="text-align: center; padding: 40px; color: #666;">
                        <i class="fas fa-check-circle" style="font-size: 3rem; margin-bottom: 15px;"></i>
                        <h3>لا توجد نشاطات للتصحيح</h3>
                        <p>لم تشارك أي طالبة في المسابقات بعد</p>
                    </div>
                `;
                return;
            }
            
            reviewContainer.innerHTML = '';
            
            savedResults.forEach((result, index) => {
                const quiz = savedQuizzes.find(q => q.title === result.quizTitle);
                if (!quiz) return;
                
                const activityDiv = document.createElement('div');
                activityDiv.className = 'review-question';
                
                let answersComparison = '';
                if (result.quizQuestions && result.userAnswers) {
                    result.quizQuestions.forEach((question, qIndex) => {
                        const userAnswer = result.userAnswers[qIndex];
                        const correctAnswer = question.correctAnswer;
                        const isCorrect = userAnswer === correctAnswer;
                        
                        answersComparison += `
                            <div class="answer-comparison">
                                <h4>السؤال ${qIndex + 1}: ${question.question}</h4>
                                <p><strong>إجابة الطالبة:</strong> ${question.type === 'multiple' || question.type === 'truefalse' ? question.options[userAnswer] : userAnswer}</p>
                                <p><strong>الإجابة الصحيحة:</strong> ${question.type === 'multiple' || question.type === 'truefalse' ? question.options[correctAnswer] : question.modelAnswer || 'لا توجد إجابة نموذجية'}</p>
                                <p class="${isCorrect ? 'correct-indicator' : 'incorrect-indicator'}">
                                    ${isCorrect ? '✓ إجابة صحيحة' : '✗ إجابة خاطئة'}
                                </p>
                            </div>
                        `;
                    });
                }
                
                activityDiv.innerHTML = `
                    <h3>نشاط: ${result.studentName} - ${result.quizTitle}</h3>
                    <p>النتيجة التلقائية: ${result.score}%</p>
                    ${answersComparison}
                    <div class="manual-grading">
                        <label>التصحيح اليدوي:</label>
                        <input type="number" class="points-input" id="manualScore-${index}" min="0" max="100" value="${result.score}">
                        <button class="btn btn-primary" onclick="updateManualScore(${index})" style="margin-right: 10px; padding: 8px 15px;">
                            <i class="fas fa-save"></i>
                            تحديث النتيجة
                        </button>
                    </div>
                `;
                
                reviewContainer.appendChild(activityDiv);
            });
        }

        function updateManualScore(index) {
            const manualScoreInput = document.getElementById(`manualScore-${index}`);
            const newScore = parseInt(manualScoreInput.value);
            
            if (newScore >= 0 && newScore <= 100) {
                const savedResults = JSON.parse(localStorage.getItem('mathWithHawra_results')) || [];
                if (savedResults[index]) {
                    savedResults[index].score = newScore;
                    savedResults[index].manuallyGraded = true;
                    localStorage.setItem('mathWithHawra_results', JSON.stringify(savedResults));
                    showNotification('تم تحديث النتيجة بنجاح', 'success');
                }
            } else {
                showNotification('يرجى إدخال نتيجة بين 0 و 100', 'warning');
            }
        }

        // نظام المسابقة
        function startQuiz(quiz, studentName) {
            currentQuiz = quiz;
            currentQuestion = 0;
            userAnswers = new Array(quiz.questions.length).fill(null);
            
            document.getElementById('quizTitleDisplay').textContent = quiz.title;
            document.querySelector('#studentLoginModal #studentName').value = studentName;
            
            showPage('quizPage');
            displayQuestion();
            startTimer();
            
            showNotification(`مرحباً ${studentName}! حظاً موفقاً`, 'success');
        }

        function displayQuestion() {
            const question = currentQuiz.questions[currentQuestion];
            document.getElementById('questionText').textContent = question.question;
            document.getElementById('questionCounter').textContent = `السؤال ${currentQuestion + 1} من ${currentQuiz.questions.length}`;
            
            // تحديث شريط التقدم
            const progress = ((currentQuestion + 1) / currentQuiz.questions.length) * 100;
            document.getElementById('quizProgress').style.width = `${progress}%`;
            
            // عرض صورة السؤال إذا وجدت
            const questionImageContainer = document.getElementById('questionImageContainer');
            questionImageContainer.innerHTML = '';
            
            if (question.image) {
                const questionImage = document.createElement('img');
                questionImage.src = question.image;
                questionImage.className = 'question-image';
                questionImage.style.maxWidth = '100%';
                questionImage.style.maxHeight = '200px';
                questionImage.style.margin = '0 auto 20px';
                questionImage.style.display = 'block';
                questionImage.style.borderRadius = '10px';
                questionImageContainer.appendChild(questionImage);
            }
            
            const optionsContainer = document.getElementById('optionsContainer');
            const textAnswerContainer = document.getElementById('textAnswerContainer');
            
            optionsContainer.style.display = 'none';
            textAnswerContainer.style.display = 'none';
            
            if (question.type === "multiple" || question.type === "truefalse") {
                optionsContainer.style.display = 'flex';
                optionsContainer.innerHTML = '';
                
                if (question.type === "multiple") {
                    question.options.forEach((option, index) => {
                        const optionElement = document.createElement('div');
                        optionElement.className = 'option';
                        if (userAnswers[currentQuestion] === index) {
                            optionElement.classList.add('selected');
                        }
                        optionElement.textContent = option;
                        optionElement.onclick = () => selectOption(optionElement, index);
                        optionsContainer.appendChild(optionElement);
                    });
                } else {
                    // أسئلة صح/خطأ
                    const trueFalseContainer = document.createElement('div');
                    trueFalseContainer.className = 'true-false-container';
                    
                    const trueBtn = document.createElement('button');
                    trueBtn.className = `true-false-btn ${userAnswers[currentQuestion] === 0 ? 'selected' : ''}`;
                    trueBtn.textContent = 'صح';
                    trueBtn.onclick = () => selectTrueFalse(trueBtn, 0);
                    
                    const falseBtn = document.createElement('button');
                    falseBtn.className = `true-false-btn ${userAnswers[currentQuestion] === 1 ? 'selected' : ''}`;
                    falseBtn.textContent = 'خطأ';
                    falseBtn.onclick = () => selectTrueFalse(falseBtn, 1);
                    
                    trueFalseContainer.appendChild(trueBtn);
                    trueFalseContainer.appendChild(falseBtn);
                    optionsContainer.appendChild(trueFalseContainer);
                }
            } else {
                // أسئلة نصية مفتوحة
                textAnswerContainer.style.display = 'block';
                const textAnswer = document.getElementById('textAnswer');
                textAnswer.value = userAnswers[currentQuestion] || '';
                
                textAnswer.oninput = () => {
                    userAnswers[currentQuestion] = textAnswer.value;
                };
            }
            
            document.querySelector('.prev-btn').style.display = currentQuestion === 0 ? 'none' : 'block';
            document.querySelector('.next-btn').style.display = currentQuestion === currentQuiz.questions.length - 1 ? 'none' : 'block';
            document.querySelector('.submit-btn').style.display = currentQuestion === currentQuiz.questions.length - 1 ? 'block' : 'none';
        }

        function selectOption(optionElement, index) {
            document.querySelectorAll('.option').forEach(opt => {
                opt.classList.remove('selected');
            });
            optionElement.classList.add('selected');
            userAnswers[currentQuestion] = index;
        }

        function selectTrueFalse(button, value) {
            document.querySelectorAll('.true-false-btn').forEach(btn => {
                btn.classList.remove('selected');
            });
            button.classList.add('selected');
            userAnswers[currentQuestion] = value;
        }

        function startTimer() {
            clearInterval(timerInterval);
            timeLeft = (currentQuiz.time || 10) * 60;
            updateTimer();
            
            timerInterval = setInterval(() => {
                timeLeft--;
                updateTimer();
                
                if (timeLeft <= 0) {
                    clearInterval(timerInterval);
                    finishQuiz();
                }
            }, 1000);
        }

        function updateTimer() {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            document.getElementById('timer').textContent = `⏰ ${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }

        function nextQuestion() {
            if (currentQuestion < currentQuiz.questions.length - 1) {
                currentQuestion++;
                displayQuestion();
            } else {
                finishQuiz();
            }
        }

        function prevQuestion() {
            if (currentQuestion > 0) {
                currentQuestion--;
                displayQuestion();
            }
        }

        function finishQuiz() {
            clearInterval(timerInterval);
            
            let correctAnswers = 0;
            userAnswers.forEach((answer, index) => {
                const question = currentQuiz.questions[index];
                
                if (question.type === "text") {
                    // الأسئلة النصية تحتاج تصحيح يدوي
                    correctAnswers += 0.5;
                } else if (answer === question.correctAnswer) {
                    correctAnswers++;
                }
            });
            
            const score = Math.round((correctAnswers / currentQuiz.questions.length) * 100);
            
            document.getElementById('finalScore').textContent = `${score}%`;
            document.getElementById('totalPoints').textContent = Math.round(correctAnswers);
            document.getElementById('maxPoints').textContent = currentQuiz.questions.length;
            
            // إضافة شارة التصنيف
            const rankingBadge = document.getElementById('rankingBadge');
            rankingBadge.innerHTML = '';
            
            if (score >= 90) {
                rankingBadge.innerHTML = '<span class="ranking-badge gold">🥇 متفوقة</span>';
            } else if (score >= 75) {
                rankingBadge.innerHTML = '<span class="ranking-badge silver">🥈 جيدة جداً</span>';
            } else if (score >= 60) {
                rankingBadge.innerHTML = '<span class="ranking-badge bronze">🥉 جيدة</span>';
            }
            
            // حفظ النتيجة
            const studentName = document.querySelector('#studentLoginModal #studentName').value;
            const resultData = {
                studentName: studentName,
                quizTitle: currentQuiz.title,
                score: score,
                correctAnswers: Math.round(correctAnswers),
                totalQuestions: currentQuiz.questions.length,
                userAnswers: userAnswers,
                quizQuestions: currentQuiz.questions,
                date: new Date().toISOString(),
                needsManualGrading: currentQuiz.questions.some(q => q.type === "text")
            };
            
            const savedResults = JSON.parse(localStorage.getItem('mathWithHawra_results')) || [];
            savedResults.push(resultData);
            localStorage.setItem('mathWithHawra_results', JSON.stringify(savedResults));
            
            showPage('resultsPage');
        }

        function showMyResults() {
            const savedResults = JSON.parse(localStorage.getItem('mathWithHawra_results')) || [];
            const studentName = document.getElementById('studentName')?.value;
            
            if (!studentName) {
                showNotification('يرجى تسجيل الدخول أولاً', 'warning');
                return;
            }
            
            const studentResults = savedResults.filter(result => result.studentName === studentName);
            
            if (studentResults.length === 0) {
                showNotification('لا توجد نتائج حالياً. شارك في مسابقة أولاً!', 'info');
            } else {
                let resultsMessage = `نتائجك في المسابقات:\n\n`;
                studentResults.forEach(result => {
                    resultsMessage += `${result.quizTitle}: ${result.score}%\n`;
                });
                alert(resultsMessage);
            }
        }

        // الإشعارات
        function showNotification(message, type = 'info') {
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notificationText');
            
            notification.className = `notification ${type}`;
            notificationText.textContent = message;
            
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 4000);
        }

        function hideNotification() {
            document.getElementById('notification').classList.remove('show');
        }

        // تهيئة التطبيق - بدون مسابقة تجريبية
        document.addEventListener('DOMContentLoaded', function() {
            // فقط تهيئة التطبيق بدون إضافة مسابقة رياضيات
            const firstTime = !localStorage.getItem('mathWithHawra_initialized');
            if (firstTime) {
                // لا نضيف أي مسابقة تجريبية
                localStorage.setItem('mathWithHawra_initialized', 'true');
            }
            
            showNotification('مرحباً بك في Math With Hawra!', 'success');
        });

        // إغلاق النوافذ بالنقر خارجها
        window.onclick = function(event) {
            if (event.target === document.getElementById('teacherLoginModal')) {
                hideModal('teacherLoginModal');
            }
            if (event.target === document.getElementById('studentLoginModal')) {
                hideModal('studentLoginModal');
            }
        }
    </script>
<!-- 🔥 كود Firebase (لن يغيّر أي شيء في التصميم) -->
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
  import { getDatabase, ref, set, get, child } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-database.js";

  const firebaseConfig = {
    apiKey: "AIzaSyC8yEv8lfLXtvN841M2dxprM5K16qN0uic",
    authDomain: "math-with-hawra.firebaseapp.com",
    databaseURL: "https://math-with-hawra-default-rtdb.firebaseio.com",
    projectId: "math-with-hawra",
    storageBucket: "math-with-hawra.firebasestorage.app",
    messagingSenderId: "935800201765",
    appId: "1:935800201765:web:ae30b29dad82c5238055cc",
    measurementId: "G-4XDBR8D52F"
  };

  const app = initializeApp(firebaseConfig);
  const db = getDatabase(app);

  // 🧪 اختبار الاتصال
  set(ref(db, "test/connection"), { connected: true })
    .then(() => console.log("✅ Firebase Connected!"))
    .catch((error) => console.error("❌ Error:", error));
</script>
<script>
  // 🌟 دالة حفظ المسابقة
  function saveQuiz() {
    const quizCode = document.getElementById("quizCode").value;
    const question = document.getElementById("question").value;
    const correctAnswer = document.getElementById("correctAnswer").value;

    if (!quizCode || !question || !correctAnswer) {
      alert("⚠ الرجاء إدخال كل الحقول!");
      return;
    }

    // نحفظ البيانات في Firebase
    const quizData = {
      question: question,
      correctAnswer: correctAnswer
    };

    set(ref(db, "quizzes/" + quizCode), quizData)
      .then(() => alert("✅ تم حفظ المسابقة بنجاح!"))
      .catch((error) => alert("❌ حدث خطأ: " + error));
  }
</script
</body>
</html>ر
