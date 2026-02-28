<!DOCTYPE html>
<html lang="mr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="google-site-verification" content="5FCzAFFd19PPEhoMOVBNgP6xqji3GGXhAupvh9nIk2A" />
    <title>ITI Pandharpur</title>
    <link rel="stylesheet" href="style.css">
    <style>
        /* Registration Overlay Styles */
        #registration-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(255, 255, 255, 0.98);
            z-index: 20000;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Arial', sans-serif;
        }

        .reg-box {
            width: 90%;
            max-width: 400px;
            padding: 30px;
            background: #fff;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            text-align: center;
            border-top: 6px solid #007bff;
        }

        .reg-box h2 { color: #007bff; font-size: 1.4rem; margin-bottom: 5px; }
        .reg-box h3 { color: #333; font-size: 1rem; margin-bottom: 25px; border-bottom: 1px solid #eee; padding-bottom: 15px; }

        .reg-group { text-align: left; margin-bottom: 15px; }
        .reg-group label { display: block; margin-bottom: 5px; font-weight: bold; color: #555; }
        .reg-group input { 
            width: 100%; padding: 12px; border: 1px solid #ccc; border-radius: 8px; box-sizing: border-box; font-size: 16px;
        }

        .reg-btn {
            width: 100%; padding: 15px; background: #007bff; color: white; border: none;
            border-radius: 8px; font-weight: bold; cursor: pointer; font-size: 1rem; transition: 0.3s;
        }

        .reg-btn:disabled { background: #ccc; cursor: not-allowed; }

        /* Hide main website initially */
        #main-site-wrapper { display: none; }

        /* Original Website Styles */
        #trades-section, #about-section, #gallery-section, #contact-section, #exam-section {
            display: none; padding: 40px 5%; background-color: #f4f4f4;
        }
        .trades-container, .about-container, .gallery-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
        .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 30px; }
        .contact-info-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .contact-card { background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); text-align: center; }
        .contact-card h4 { color: #007bff; margin-bottom: 10px; }
        .map-container { margin-top: 20px; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .dir-btn { display: block; background: #28a745; color: white; text-align: center; padding: 10px; text-decoration: none; font-weight: bold; margin-top: 5px; }
        .feedback-form { background: #fff; padding: 30px; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
        .feedback-form h3 { margin-bottom: 20px; color: #333; }
        .form-group { margin-bottom: 15px; }
        .form-group label { display: block; margin-bottom: 5px; font-weight: bold; }
        .form-group input, .form-group select, .form-group textarea { width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 5px; box-sizing: border-box; }
        .submit-btn { background: #007bff; color: white; border: none; padding: 12px 20px; border-radius: 5px; cursor: pointer; font-weight: bold; width: 100%; }
        .gallery-category { margin-bottom: 40px; }
        .gallery-title { background: #007bff; color: white; padding: 10px 20px; border-radius: 5px; margin-bottom: 20px; display: inline-block; }
        .gallery-grid { grid-template-columns: repeat(2, 1fr); }
        .grid-3 { grid-template-columns: repeat(3, 1fr); }
        .gallery-item { background: #fff; padding: 10px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        .gallery-item img { width: 100%; height: 250px; object-fit: cover; border-radius: 5px; display: block; }
        .trade-card, .facility-card { background: #fff; border-radius: 12px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.1); text-align: left; transition: transform 0.3s; padding: 20px; display: flex; flex-direction: column; cursor: pointer; }
        .facility-card:hover { transform: translateY(-5px); }
        .facility-card h4 { font-size: 1.2rem; color: #333; margin: 10px 0; }
        .facility-card p { font-size: 0.95rem; color: #666; line-height: 1.5; }
        .facility-icon { font-size: 30px; margin-bottom: 10px; }
        .trade-card img { width: 100%; height: 150px; object-fit: cover; border-radius: 8px; }
        .trade-card h4 { padding: 10px 0 5px 0; margin: 0; font-size: 1.1rem; color: #000; }
        .trade-info { font-size: 0.9rem; color: #555; margin: 2px 0; }
        .view-details-btn { margin: 10px 0; padding: 8px 15px; background-color: #007bff; color: white; border-radius: 4px; font-size: 0.85rem; font-weight: bold; display: inline-block; width: fit-content; text-align: center; }
        
        /* Exam Section Styles */
        .exam-info-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; margin-bottom: 30px; }
        .exam-stat-card { background: #fff; padding: 20px; border-radius: 10px; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.1); border-bottom: 4px solid #007bff; }
        .exam-stat-card .icon { font-size: 24px; margin-bottom: 10px; display: block; }
        .exam-stat-card h5 { margin: 5px 0; color: #555; font-size: 0.9rem; }
        .exam-stat-card p { font-weight: bold; color: #007bff; font-size: 1.1rem; margin: 0; }
        .exam-content-box { background: #fff; padding: 25px; border-radius: 10px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); margin-bottom: 20px; }
        .exam-content-box h4 { border-left: 4px solid #007bff; padding-left: 10px; margin-top: 0; color: #333; }
        .criteria-list { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .criteria-item { background: #f9f9f9; padding: 10px; border-radius: 5px; border-left: 3px solid #28a745; }

        .modal { display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.8); overflow-y: auto; }
        .modal-content { background-color: #fff; margin: 5% auto; padding: 20px; width: 85%; border-radius: 10px; position: relative; }
        .close-modal { position: absolute; right: 20px; top: 10px; font-size: 30px; cursor: pointer; }
        .details-flex { display: flex; gap: 30px; flex-wrap: wrap; }
        .details-left { flex: 1; min-width: 300px; }
        .details-left img { width: 100%; border-radius: 8px; margin-bottom: 20px; }
        .details-right { flex: 2; min-width: 300px; }
        .details-right h2 { color: #007bff; margin-top: 0; }
        .section-header { background: #eee; padding: 10px; margin: 20px 0 10px 0; border-left: 5px solid #007bff; font-weight: bold; }
        .points-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; list-style: none; padding: 0; }
        .points-grid li { padding: 5px; border-bottom: 1px solid #ddd; font-size: 0.85rem; }
        .career-list { list-style: none; padding: 0; display: grid; grid-template-columns: 1fr 1fr; gap: 5px; }
        .career-list li { font-size: 0.9rem; color: #333; }
        .career-list li::before { content: "✔ "; color: green; font-weight: bold; }
        
        /* Video Button Styles */
        .video-btn-container { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 15px; }
        .video-btn { display: inline-block; padding: 10px 15px; background-color: #ff0000; color: #fff; text-decoration: none; border-radius: 5px; font-weight: bold; transition: background 0.3s; font-size: 0.9rem; }
        .practice-btn { background-color: #28a745; }
        .video-btn:hover { opacity: 0.8; color: #fff; }

        @media (max-width: 768px) {
            .trades-container, .about-container, .gallery-grid, .grid-3, .contact-grid, .contact-info-cards, .criteria-list { grid-template-columns: 1fr; }
            .modal-content { width: 95%; }
            .points-grid, .career-list { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <div id="registration-overlay">
    

    <div id="main-site-wrapper">
        <header class="main-header">
            <div class="header-top">
                <img src="9692aDL-ns-230ba9ce-503a-4d52-a7f1-c39982d45480.jpg" alt="ITI Logo" class="logo">
                <h1>यशवंतराव केळकर शासकीय औद्योगिक प्रशिक्षण संस्था, पंढरपूर</h1>
            </div>

            <nav class="navbar">
                <ul>
                    <li><a href="#" onclick="showHome()">Home</a></li>
                    <li><a href="#" onclick="showAbout()">About Us</a></li>
                    <li><a href="#" onclick="showTrades()">Trades</a></li>
                    <li><a href="#" onclick="showExam()">Exam Info</a></li>
                    <li><a href="#" onclick="showGallery()">Gallery</a></li>
                    <li><a href="#" onclick="showContact()">Contact</a></li>
                </ul>
            </nav>
        </header>

        <div id="home-content">
            <section class="hero-section">
                <div class="hero-left">
                    <h2 class="slogan">"Skill Development for Better Future"</h2>
                    <div class="stats-container">
                        <div class="stat-box">Program 13</div>
                        <div class="stat-box">Students Trained 45000</div>
                        <div class="stat-box">Placement Assistance 90%</div>
                    </div>
                </div>
                <div class="hero-right">
                    <img src="IMG_20260117_113817.jpg" alt="College Building" class="college-img">
                </div>
            </section>

            <section class="why-choose">
                <h3>ITI कॉलेज का निवडावे?</h3>
                <ul>
                    <li>अत्याधुनिक वर्कशॉप आणि प्रगत मशिनरी उपलब्ध आहेत.</li>
                    <li>उत्कृष्ट प्लेसमेंट रेकॉर्ड आणि नामांकित कंपन्यांशी टाय-अप.</li>
                    <li>अनुभवी आणि कुशल प्रशिक्षकांकडून मार्गदर्शन.</li>
                    <li>कौशल्य विकासावर आधारित रोजगाराभिमुख अभ्यासक्रम.</li>
                </ul>
            </section>
        </div>

        <section id="exam-section">
            <h3 style="text-align:center; margin-bottom:10px;">AITT - All India Trade Test</h3>
            <p style="text-align:center; color:#666; margin-bottom:30px;">NCVT Certification Examination for ITI Trainees</p>
            
            <div class="exam-info-grid">
                <div class="exam-stat-card"><span class="icon">🏛️</span><h5>Conducted By</h5><p>NCVT</p></div>
                <div class="exam-stat-card"><span class="icon">📝</span><h5>Exam Type</h5><p>CBT + Practical</p></div>
                <div class="exam-stat-card"><span class="icon">⏱️</span><h5>CBT Duration</h5><p>1 Hour</p></div>
                <div class="exam-stat-card"><span class="icon">📋</span><h5>Total Questions</h5><p>75</p></div>
                <div class="exam-stat-card"><span class="icon">💯</span><h5>Total Marks</h5><p>150</p></div>
            </div>

            <div class="exam-content-box">
                <h4>About AITT (परीक्षेबद्दल माहिती)</h4>
                <p>All India Trade Test (AITT) ही नॅशनल कौन्सिल फॉर व्होकेशनल ट्रेनिंग (NCVT) द्वारे आयोजित केली जाणारी अंतिम परीक्षा आहे. ही परीक्षा 'Craftsmen Training Scheme' (CTS) अंतर्गत प्रशिक्षण पूर्ण करणाऱ्या सर्व विद्यार्थ्यांसाठी अनिवार्य आहे.</p>
                <p>या परीक्षेत यशस्वी होणाऱ्या उमेदवारांना 'नॅशनल ट्रेड सर्टिफिकेट' (NTC) प्रदान केले जाते, जे भारत सरकारच्या विविध नोकऱ्यांसाठी अत्यंत महत्वाचे मानले जाते.</p>
            </div>

            <div class="exam-content-box">
                <h4>Exam Pattern (परीक्षा पद्धत)</h4>
                <div style="margin-top:15px;">
                    <p><strong>💻 CBT Examination (कॉम्प्युटर आधारित परीक्षा):</strong></p>
                    <ul style="font-size: 0.95rem;">
                        <li><strong>Trade Theory:</strong> ट्रेड संबंधित तांत्रिक माहिती.</li>
                        <li><strong>Workshop Calculation & Science:</strong> गणित आणि विज्ञान.</li>
                        <li><strong>Engineering Drawing:</strong> इंजिनिअरिंग ड्रॉइंग.</li>
                        <li><strong>Employability Skills:</strong> व्यक्तिमत्व विकास आणि सॉफ्ट स्किल्स.</li>
                    </ul>
                    <p><strong>🔧 Practical Examination (प्रात्यक्षिक परीक्षा):</strong></p>
                    <ul style="font-size: 0.95rem;">
                        <li><strong>Workshop Practicals:</strong> कार्यशाळेत प्रत्यक्ष कामाचे मूल्यमापन.</li>
                        <li><strong>Sessional Work:</strong> वर्षभरातील कामावर आधारित गुण (Assignments & Projects).</li>
                    </ul>
                </div>
            </div>

            <div class="exam-content-box">
                <h4>Passing Criteria (उत्तीर्ण होण्याचे निकष)</h4>
                <div class="criteria-list">
                    <div class="criteria-item"><strong>40% Minimum:</strong> Theory (CBT) मध्ये किमान 40% गुण आवश्यक.</div>
                    <div class="criteria-item"><strong>60% Minimum:</strong> Practical आणि Sessional मध्ये किमान 60% गुण आवश्यक.</div>
                    <div class="criteria-item"><strong>40% Aggregate:</strong> एकूण निव्वळ सरासरी किमान 40% असावी.</div>
                    <div class="criteria-item"><strong>Attendance:</strong> प्रशिक्षणादरम्यान किमान 80% उपस्थिती अनिवार्य.</div>
                </div>
            </div>
        </section>

        <section id="about-section">
            <h3 style="text-align:center; margin-bottom:30px;">आमच्या बद्दल (About Us / Infrastructure)</h3>
            <div class="about-container">
                <div class="facility-card"><div class="facility-icon">🏢</div><h4>Sprawling Campus</h4><p>Our campus spreads across 27 acres of lush green environment.</p></div>
                <div class="facility-card"><div class="facility-icon">🏠</div><h4>Boys Hostel</h4><p>Hostel facilities are available for boys with all basic amenities.</p></div>
                <div class="facility-card"><div class="facility-icon">👔</div><h4>Staff Quarters</h4><p>On-campus residential facilities for our dedicated staff.</p></div>
                <div class="facility-card"><div class="facility-icon">🏡</div><h4>Principal's Residence</h4><p>Dedicated Principal's Residence within the campus.</p></div>
                <div class="facility-card"><div class="facility-icon">🌳</div><h4>Green Campus</h4><p>Our college campus is beautifully adorned with almond trees.</p></div>
                <div class="facility-card"><div class="facility-icon">💧</div><h4>RO Water</h4><p>Purified RO water facility is available for all students and staff.</p></div>
                <div class="facility-card"><div class="facility-icon">💻</div><h4>IT Lab</h4><p>Advanced IT Lab equipped with 21 PCs and a modern smart screen.</p></div>
                <div class="facility-card"><div class="facility-icon">🛡️</div><h4>Security</h4><p>The entire campus is under 24/7 CCTV surveillance for safety.</p></div>
                <div class="facility-card"><div class="facility-icon">🏠👧</div></h4>Girls hostel</h4></p>We are a safe, friendly, and supportive girls’ hostel where comfort and care come first.</p></div>
                <div class="facility-card"><div class="facility-icon">🎓</div><h4>Success Rate</h4><p>A proud institution where more than 400 students pass out  every year.</p></div>
                <div class="facility-card"><div class="facility-icon">🍱</div><h4>Canteen</h4></p>A We have an on-campus canteen that offers fresh snacks & hygienic food daily.</p></div>
            </div>
        </section>

        <section id="gallery-section">
            <h3 style="text-align:center; margin-bottom:30px;">फोटो गॅलरी (Gallery)</h3>
            <div class="gallery-category">
                <h4 class="gallery-title">१. वंदे मातरम्</h4>
                <div class="gallery-grid">
                    <div class="gallery-item"><img src="IMG-20260212-WA0028.jpg" alt="वंदे मातरम् इमेज १"></div>
                    <div class="gallery-item"><img src="vande_mataram_2.jpg" alt="वंदे मातरम् इमेज २"></div>
                </div>
            </div>
            <div class="gallery-category">
                <h4 class="gallery-title">२. वीर बालदिवस</h4>
                <div class="gallery-grid">
                    <div class="gallery-item"><img src="IMG-20260212-WA0022.jpg" alt="वीर बालदिवस इमेज १"></div>
                    <div class="gallery-item"><img src="IMG-20260212-WA0024.jpg" alt="वीर बालदिवस इमेज २"></div>
                </div>
            </div>
            <div class="gallery-category">
                <h4 class="gallery-title">३. विज्ञान तंत्रज्ञान</h4>
                <div class="gallery-grid grid-3">
                    <div class="gallery-item"><img src="IMG-20260212-WA0025.jpg" alt=""></div>
                    <div class="gallery-item"><img src="IMG-20260212-WA0021.jpg" alt="विज्ञान तंत्रज्ञान इमेज २"></div>
                    <div class="gallery-item"><img src="IMG-20260212-WA0017.jpg" alt="विज्ञान तंत्रज्ञान इमेज ३"></div>
                </div>
            </div>
            <div class="gallery-category">
                <h4 class="gallery-title">4. पुणे विभाग तंत्रज्ञान प्रदर्शन</h4>
                <div class="gallery-grid grid-4">
                    <div class="gallery-item"><img src="IMG-20260226-WA0000.jpg" alt="पुणे विभाग तंत्रज्ञान प्रदर्शन इमेज 1"></div>
                    <div class="gallery-item"><img src="IMG-20260226-WA0001.jpg" alt="पुणे विभाग तंत्रज्ञान प्रदर्शन इमेज 2"></div>
                    <div class="gallery-item"><img src="IMG-20260226-WA0002.jpg" alt="पुणे विभाग तंत्रज्ञान प्रदर्शन इमेज 3"></div>
                </div>
            </div>
        </section>

        <section id="trades-section">
            <h3 style="text-align:center; margin-bottom:30px;"> कोर्सेस ( Trades)</h3>
            <div class="trades-container" id="trades-list"></div>
        </section>

        <section id="contact-section">
            <h3 style="text-align:center; margin-bottom:30px;">संपर्क (Contact Us)</h3>
            <div class="contact-grid">
                <div>
                    <div class="contact-info-cards">
                        <div class="contact-card"><h4>📍 Address</h4><p>जुना कासेगाव रोड, पंढरपुर, जि. सोलापूर - ४१३३०४</p></div>
                        <div class="contact-card"><h4>📞 Phone</h4><p>+९१ 9970794226</p></div>
                        <div class="contact-card"><h4>✉️ Email</h4><p>iti.pandharpur@dvet.gov.in</p></div>
                        <div class="contact-card"><h4>⏰ Office Hours</h4><p>सकाळी १०:०० ते संध्याकाळी ५:00<br>(रविवार बंद)</p></div>
                    </div>
                    </div>
                </div>

                <div class="feedback-form">
                    <h3>फीडबॅक / चौकशी (Feedback)</h3>
                    <form id="feedbackForm">
                        <div class="form-group"><label>पूर्ण नाव</label><input type="text" name="fullName" required></div>
                        <div class="form-group"><label>ईमेल</label><input type="email" name="email" required></div>
                        <div class="form-group"><label>मोबाईल</label><input type="tel" name="phone" pattern="[0-9]{10}" required></div>
                        <div class="form-group">
                            <label>विषय</label>
                            <select name="subject" required>
                                <option value="Admission">Admission Enquiry</option>
                                <option value="Course">Course Information</option>
