```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>قصة حب عمر وفاطمة - Amr Diab Edition</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Arabic -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Cairo:wght@300;400;600;700;800&family=Tajawal:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        love: {
                            50: '#fff1f2',
                            100: '#ffe4e6',
                            200: '#fecdd3',
                            300: '#fda4af',
                            400: '#fb7185',
                            500: '#f43f5e',
                            600: '#e11d48',
                            700: '#be123c',
                            800: '#9f1239',
                            900: '#881337',
                        }
                    },
                    fontFamily: {
                        cairo: ['Cairo', 'sans-serif'],
                        tajawal: ['Tajawal', 'sans-serif'],
                        amiri: ['Amiri', 'serif']
                    }
                }
            }
        }
    </script>

    <style>
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #0d021a;
            color: #fff;
            overflow-x: hidden;
        }

        /* Ambient glowing background */
        .glow-bg {
            background: radial-gradient(circle at 50% 20%, rgba(225, 29, 72, 0.3), transparent 60%),
                        radial-gradient(circle at 80% 70%, rgba(136, 19, 55, 0.35), transparent 50%),
                        radial-gradient(circle at 10% 80%, rgba(244, 63, 94, 0.25), transparent 50%);
            background-attachment: fixed;
        }

        /* Glassmorphism style */
        .glass {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.4);
        }

        .glass-card {
            background: rgba(30, 10, 35, 0.5);
            backdrop-filter: blur(14px);
            border: 1px solid rgba(244, 63, 94, 0.25);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-card:hover {
            border-color: rgba(244, 63, 94, 0.55);
            transform: translateY(-4px);
            box-shadow: 0 15px 35px rgba(225, 29, 72, 0.3);
        }

        /* Heart envelope flip animation */
        .envelope-wrapper {
            perspective: 1000px;
        }

        .envelope {
            position: relative;
            width: 320px;
            height: 210px;
            background: #be123c;
            border-radius: 0 0 16px 16px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.7);
            cursor: pointer;
            transition: transform 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .envelope:hover {
            transform: scale(1.03);
        }

        .envelope-flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            border-top: 115px solid #e11d48;
            transform-origin: top;
            transition: transform 0.5s ease;
            z-index: 3;
        }

        .envelope.open .envelope-flap {
            transform: rotateX(180deg);
            z-index: 1;
        }

        .letter {
            position: absolute;
            bottom: 10px;
            left: 15px;
            right: 15px;
            height: 185px;
            background: #fff1f2;
            color: #881337;
            border-radius: 12px;
            padding: 15px;
            transition: transform 0.6s ease 0.3s;
            z-index: 2;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .envelope.open .letter {
            transform: translateY(-110px);
        }

        /* Floating Hearts Particles */
        .heart-particle {
            position: absolute;
            color: #fb7185;
            pointer-events: none;
            animation: floatUp 4s linear infinite;
            opacity: 0;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.8) rotate(0deg);
                opacity: 0;
            }
            20% {
                opacity: 0.85;
            }
            80% {
                opacity: 0.85;
            }
            100% {
                transform: translateY(-100vh) scale(1.3) rotate(360deg);
                opacity: 0;
            }
        }

        .pulse-glow {
            animation: pulseGlow 2s infinite alternate;
        }

        @keyframes pulseGlow {
            from {
                box-shadow: 0 0 15px rgba(244, 63, 94, 0.4);
            }
            to {
                box-shadow: 0 0 30px rgba(244, 63, 94, 0.8), 0 0 50px rgba(225, 29, 72, 0.5);
            }
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0d021a;
        }
        ::-webkit-scrollbar-thumb {
            background: #be123c;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #f43f5e;
        }
    </style>
</head>
<body class="glow-bg min-h-screen relative flex flex-col justify-between">

    <!-- Floating Background Particles Container -->
    <div id="heartsContainer" class="fixed inset-0 pointer-events-none z-0 overflow-hidden"></div>

    <!-- 1. ENVELOPE INTRO OVERLAY -->
    <div id="introOverlay" class="fixed inset-0 z-50 flex items-center justify-center bg-black/90 backdrop-blur-md transition-opacity duration-700">
        <div class="flex flex-col items-center max-w-sm px-4 text-center">
            
            <div id="envelopeElement" class="envelope mb-8" onclick="openEnvelope()">
                <div class="envelope-flap"></div>
                <div class="letter shadow-lg">
                    <i class="fa-solid fa-heart text-red-500 text-3xl mb-2 animate-bounce"></i>
                    <h3 class="font-bold text-lg text-rose-900 font-amiri">رسالة حب خاصة</h3>
                    <p class="text-xs text-rose-700 mt-1">اضغط لفتح الحكاية ❤</p>
                </div>
                <div class="absolute inset-0 flex items-center justify-center z-10 text-white font-bold font-tajawal text-lg">
                    <div class="bg-rose-900/80 px-5 py-2.5 rounded-full border border-rose-400/30 flex items-center gap-2 shadow-xl">
                        <i class="fa-solid fa-envelope text-pink-300"></i>
                        <span>عمر & فاطمة</span>
                    </div>
                </div>
            </div>

            <!-- PIN Code & Direct Enter -->
            <div id="pinSection" class="w-full bg-white/5 border border-white/10 p-4 rounded-2xl backdrop-blur-md space-y-3">
                <p class="text-rose-200 text-sm font-tajawal"><i class="fa-solid fa-lock text-rose-400 ml-1"></i> ادخل الرمز السري أو ادخل مباشرة</p>
                
                <div class="flex gap-2 justify-center">
                    <input type="password" id="pinInput" placeholder="1234" maxlength="6" 
                           class="w-28 bg-black/50 text-center text-white text-xl border border-rose-500/40 rounded-xl px-3 py-2 outline-none focus:border-rose-400 font-mono tracking-widest">
                    <button onclick="checkPin()" class="bg-gradient-to-r from-rose-600 to-pink-600 hover:from-rose-500 hover:to-pink-500 px-4 py-2 rounded-xl text-white font-bold text-sm shadow-lg transition">
                        تأكيد <i class="fa-solid fa-arrow-left mr-1"></i>
                    </button>
                </div>

                <div class="pt-1">
                    <button onclick="bypassPin()" class="text-xs text-rose-300 hover:text-white underline font-tajawal">
                        دخول مباشر بدون كلمة سر ✨
                    </button>
                </div>

                <p id="pinError" class="text-xs text-red-400 hidden">الرمز السري غير صحيح (الرمز الافتراضي: 1234)</p>
            </div>

        </div>
    </div>

    <!-- MAIN APP CONTENT -->
    <div id="mainContent" class="opacity-0 transition-opacity duration-1000 flex-1">

        <!-- NAVBAR -->
        <header class="sticky top-0 z-40 glass border-b border-rose-500/20 px-4 py-3">
            <div class="max-w-5xl mx-auto flex justify-between items-center">
                <div class="flex items-center gap-2">
                    <i class="fa-solid fa-heart text-rose-500 text-2xl animate-pulse"></i>
                    <span id="navTitle" class="font-amiri font-bold text-xl md:text-2xl text-transparent bg-clip-text bg-gradient-to-r from-rose-300 via-pink-400 to-red-300">
                        عمر & فاطمة
                    </span>
                </div>
                
                <div class="flex items-center gap-2">
                    <button id="editToggleBtn" onclick="toggleEditMode()" class="bg-rose-500/20 hover:bg-rose-500/30 text-rose-300 border border-rose-500/40 px-3 py-1.5 rounded-full text-xs md:text-sm font-semibold flex items-center gap-1.5 transition">
                        <i class="fa-solid fa-pen-to-square"></i>
                        <span id="editBtnText">تعديل</span>
                    </button>

                    <button onclick="toggleAudio()" class="bg-pink-500/20 hover:bg-pink-500/30 text-pink-300 border border-pink-500/40 w-9 h-9 rounded-full flex items-center justify-center transition">
                        <i id="navMusicIcon" class="fa-solid fa-music text-xs"></i>
                    </button>
                </div>
            </div>
        </header>

        <main class="max-w-5xl mx-auto px-4 py-8 space-y-12">

            <!-- HERO SECTION -->
            <section class="text-center py-8 relative">
                <div class="inline-block p-1 rounded-full bg-gradient-to-r from-rose-500 via-pink-500 to-purple-500 mb-4 pulse-glow">
                    <div class="bg-slate-950 px-6 py-2 rounded-full flex items-center gap-2">
                        <span class="text-rose-300 text-sm font-semibold font-tajawal">عالمنا الخاطف للأنفاس ✨</span>
                        <i class="fa-solid fa-sparkles text-amber-300 text-xs"></i>
                    </div>
                </div>

                <h1 id="heroTitle" class="text-4xl md:text-6xl font-extrabold font-amiri text-transparent bg-clip-text bg-gradient-to-r from-rose-200 via-rose-400 to-pink-300 mb-4 tracking-wide leading-relaxed">
                    عمر و فاطمه
                </h1>
                
                <p id="heroSubtitle" class="text-rose-200/80 max-w-xl mx-auto text-base md:text-lg font-tajawal leading-relaxed">
                    "تملي معاك، ولو حتى بعيد عني في قلبي هويتك.. أنت العمر والبداية والنهاية."
                </p>
            </section>

            <!-- RELATIONSHIP COUNTER SECTION -->
            <section class="glass-card rounded-3xl p-6 md:p-8 relative overflow-hidden">
                <div class="text-center mb-6">
                    <h2 class="text-xl md:text-2xl font-bold font-tajawal text-rose-300 flex items-center justify-center gap-2">
                        <i class="fa-solid fa-stopwatch text-rose-500"></i>
                        <span>عداد الحب والأيام</span>
                    </h2>
                    <p class="text-xs md:text-sm text-gray-400 mt-1">كل ثانية بتعدي وإحنا سوا هي أجمل عمر ❤</p>
                </div>

                <div class="grid grid-cols-2 md:grid-cols-5 gap-3 md:gap-4 text-center">
                    <div class="bg-black/40 border border-rose-500/20 rounded-2xl p-3 md:p-4 backdrop-blur-sm">
                        <span id="timerYears" class="block text-2xl md:text-4xl font-extrabold text-rose-400 font-mono">0</span>
                        <span class="text-xs text-rose-200/70 font-tajawal">سنة</span>
                    </div>
                    <div class="bg-black/40 border border-rose-500/20 rounded-2xl p-3 md:p-4 backdrop-blur-sm">
                        <span id="timerDays" class="block text-2xl md:text-4xl font-extrabold text-rose-400 font-mono">0</span>
                        <span class="text-xs text-rose-200/70 font-tajawal">يوم</span>
                    </div>
                    <div class="bg-black/40 border border-rose-500/20 rounded-2xl p-3 md:p-4 backdrop-blur-sm">
                        <span id="timerHours" class="block text-2xl md:text-4xl font-extrabold text-rose-400 font-mono">0</span>
                        <span class="text-xs text-rose-200/70 font-tajawal">ساعة</span>
                    </div>
                    <div class="bg-black/40 border border-rose-500/20 rounded-2xl p-3 md:p-4 backdrop-blur-sm">
                        <span id="timerMinutes" class="block text-2xl md:text-4xl font-extrabold text-rose-400 font-mono">0</span>
                        <span class="text-xs text-rose-200/70 font-tajawal">دقيقة</span>
                    </div>
                    <div class="col-span-2 md:col-span-1 bg-gradient-to-br from-rose-900/40 to-black/40 border border-rose-500/40 rounded-2xl p-3 md:p-4 backdrop-blur-sm">
                        <span id="timerSeconds" class="block text-2xl md:text-4xl font-extrabold text-pink-400 font-mono animate-pulse">0</span>
                        <span class="text-xs text-rose-200/70 font-tajawal">ثانية</span>
                    </div>
                </div>

                <div class="mt-6 text-center text-xs text-rose-300/80 font-mono">
                    بداية قصتنا: <span id="startDateDisplay">2024-01-01</span>
                </div>
            </section>

            <!-- AMR DIAB MUSIC PLAYER WIDGET -->
            <section class="glass-card rounded-3xl p-6 border border-pink-500/30 relative overflow-hidden">
                <div class="flex flex-col md:flex-row items-center justify-between gap-4">
                    <div class="flex items-center gap-4 w-full md:w-auto">
                        <div class="relative w-16 h-16 rounded-2xl bg-gradient-to-tr from-rose-600 to-pink-500 flex items-center justify-center shrink-0 shadow-lg overflow-hidden border border-rose-400/30">
                            <i id="musicDiscIcon" class="fa-solid fa-compact-disc text-3xl text-white/90"></i>
                        </div>
                        <div class="overflow-hidden">
                            <span class="bg-rose-500/20 text-rose-300 text-[10px] px-2 py-0.5 rounded-full font-bold border border-rose-500/30">الهضبة - عمرو دياب 🎤</span>
                            <h3 id="musicTrackTitle" class="font-bold text-rose-100 font-tajawal text-base md:text-lg truncate mt-1">تملي معاك 🎶</h3>
                            <p id="musicArtist" class="text-xs text-gray-400 truncate">أجمل الأغاني الرومانسية لعمر وفاطمة</p>
                        </div>
                    </div>

                    <!-- Audio Controls -->
                    <div class="flex items-center gap-4 w-full md:w-auto justify-center">
                        <button onclick="toggleAudio()" id="mainPlayBtn" class="w-12 h-12 rounded-full bg-gradient-to-r from-rose-500 to-pink-500 hover:scale-105 flex items-center justify-center text-white shadow-lg transition">
                            <i id="mainPlayIcon" class="fa-solid fa-play text-lg ml-0.5"></i>
                        </button>
                        <div class="w-full md:w-48 bg-white/10 h-2 rounded-full overflow-hidden cursor-pointer" onclick="seekAudio(event)">
                            <div id="audioProgressBar" class="bg-gradient-to-r from-rose-500 to-pink-400 h-full w-0 transition-all duration-100"></div>
                        </div>
                    </div>
                </div>

                <!-- Hidden audio element with Amr Diab Romantic Track -->
                <audio id="bgAudio" loop preload="metadata">
                    <source id="audioSource" src="https://ia800902.us.archive.org/30/items/AmrDiab-TamallyMaak/01.%20Tamally%20Maak.mp3" type="audio/mpeg">
                </audio>
            </section>

            <!-- TIMELINE / OUR MEMORIES SECTION -->
            <section class="space-y-6">
                <div class="flex justify-between items-center">
                    <div>
                        <h2 class="text-2xl font-bold font-tajawal text-rose-300 flex items-center gap-2">
                            <i class="fa-solid fa-timeline text-rose-500"></i>
                            <span>محطات الذكريات</span>
                        </h2>
                        <p class="text-xs text-gray-400">تواريخ حفرت أجمل المواقف بيننا</p>
                    </div>

                    <button id="addTimelineBtn" onclick="openAddTimelineModal()" class="hidden bg-rose-600/80 hover:bg-rose-600 text-white text-xs px-3 py-2 rounded-xl transition flex items-center gap-1">
                        <i class="fa-solid fa-plus"></i> إضافة محطة
                    </button>
                </div>

                <div id="timelineList" class="relative border-r-2 border-rose-500/30 mr-4 md:mr-8 space-y-8 pr-6 md:pr-8">
                    <!-- Dynamic timeline cards -->
                </div>
            </section>

            <!-- PHOTO GALLERY / MEMORY WALL -->
            <section class="space-y-6">
                <div class="flex justify-between items-center">
                    <div>
                        <h2 class="text-2xl font-bold font-tajawal text-rose-300 flex items-center gap-2">
                            <i class="fa-solid fa-images text-rose-500"></i>
                            <span>ألبوم صور الذكريات 📸</span>
                        </h2>
                        <p class="text-xs text-gray-400">لحظات مصورة تجمع عمر وفاطمة</p>
                    </div>

                    <button id="addPhotoBtn" onclick="triggerPhotoUpload()" class="hidden bg-pink-600/80 hover:bg-pink-600 text-white text-xs px-3 py-2 rounded-xl transition flex items-center gap-1">
                        <i class="fa-solid fa-upload"></i> إضافة صورة
                    </button>
                    <input type="file" id="photoFileInput" accept="image/*" class="hidden" onchange="handlePhotoUpload(event)">
                </div>

                <div id="galleryGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
                    <!-- Dynamic photo grid -->
                </div>
            </section>

            <!-- LOVE NOTES & SECRET MESSAGES -->
            <section class="space-y-6">
                <div class="flex justify-between items-center">
                    <div>
                        <h2 class="text-2xl font-bold font-tajawal text-rose-300 flex items-center gap-2">
                            <i class="fa-solid fa-envelope-open-text text-rose-500"></i>
                            <span>جدار رسائل الحب 💌</span>
                        </h2>
                        <p class="text-xs text-gray-400">رسائل دافئة بين القلوب</p>
                    </div>

                    <button onclick="openNoteModal()" class="bg-gradient-to-r from-rose-600 to-pink-600 hover:from-rose-500 hover:to-pink-500 text-white text-xs px-4 py-2 rounded-xl transition shadow-md flex items-center gap-1 font-semibold">
                        <i class="fa-solid fa-pen"></i> اكتب رسالة
                    </button>
                </div>

                <div id="notesGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
                    <!-- Dynamic Note Cards -->
                </div>
            </section>

            <!-- EDIT MODE SETTINGS PANEL -->
            <section id="editSettingsPanel" class="hidden glass-card rounded-3xl p-6 border-2 border-amber-500/40 space-y-6">
                <div class="flex items-center gap-2 text-amber-400 border-b border-white/10 pb-3">
                    <i class="fa-solid fa-sliders text-xl"></i>
                    <h3 class="font-bold font-tajawal text-lg">إعدادات الموقع (وضع التعديل)</h3>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                    <div>
                        <label class="block text-gray-300 mb-1">اسم العريس / الشريك 1:</label>
                        <input type="text" id="editName1" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none focus:border-rose-400">
                    </div>
                    <div>
                        <label class="block text-gray-300 mb-1">اسم العروسة / الشريك 2:</label>
                        <input type="text" id="editName2" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none focus:border-rose-400">
                    </div>
                    <div>
                        <label class="block text-gray-300 mb-1">تاريخ بداية القصة:</label>
                        <input type="date" id="editStartDate" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none focus:border-rose-400">
                    </div>
                    <div>
                        <label class="block text-gray-300 mb-1">الرمز السري (PIN):</label>
                        <input type="text" id="editPinCode" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none focus:border-rose-400">
                    </div>
                    <div class="md:col-span-2">
                        <label class="block text-gray-300 mb-1">رابط أغانى عمرو دياب (أو رابط MP3 مباشر):</label>
                        <input type="text" id="editMusicUrl" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none focus:border-rose-400" placeholder="https://...">
                    </div>
                    <div class="md:col-span-2">
                        <label class="block text-gray-300 mb-1">العنوان الفرعي للرسالة:</label>
                        <textarea id="editHeroSubtitle" rows="2" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none focus:border-rose-400"></textarea>
                    </div>
                </div>

                <div class="flex justify-end gap-3 pt-2">
                    <button onclick="resetToDefaults()" class="bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-xl text-xs font-semibold">استعادة الضبط الأصلي</button>
                    <button onclick="saveGeneralSettings()" class="bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-500 hover:to-teal-500 text-white px-6 py-2 rounded-xl font-bold text-xs shadow-lg">حفظ البيانات في localstorage</button>
                </div>
            </section>

        </main>

        <!-- FOOTER -->
        <footer class="text-center py-6 text-xs text-rose-300/60 border-t border-rose-500/10 font-tajawal mt-12">
            تم التصميم بحب ❤ لـ <span id="footerNames">عمر و فاطمه</span> | أغنية الصفحة: عمرو دياب 🎵
        </footer>

    </div>

    <!-- MODAL: ADD TIMELINE ITEM -->
    <div id="timelineModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="glass-card rounded-2xl max-w-md w-full p-6 space-y-4">
            <h3 class="text-lg font-bold text-rose-300 font-tajawal">إضافة ذكرى جديدة</h3>
            <div>
                <label class="block text-xs text-gray-300 mb-1">العنوان:</label>
                <input type="text" id="tlTitleInput" placeholder="مثال: يوم خطوبتنا" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none text-sm">
            </div>
            <div>
                <label class="block text-xs text-gray-300 mb-1">التاريخ:</label>
                <input type="date" id="tlDateInput" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none text-sm">
            </div>
            <div>
                <label class="block text-xs text-gray-300 mb-1">الوصف:</label>
                <textarea id="tlDescInput" rows="3" placeholder="تفاصيل الذكرى..." class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none text-sm"></textarea>
            </div>
            <div class="flex justify-end gap-2 pt-2">
                <button onclick="closeTimelineModal()" class="px-4 py-2 bg-gray-700 rounded-xl text-xs">إلغاء</button>
                <button onclick="saveTimelineItem()" class="px-4 py-2 bg-rose-600 rounded-xl text-xs font-bold">إضافة الذكرى</button>
            </div>
        </div>
    </div>

    <!-- MODAL: ADD LOVE NOTE -->
    <div id="noteModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="glass-card rounded-2xl max-w-md w-full p-6 space-y-4">
            <h3 class="text-lg font-bold text-rose-300 font-tajawal">إضافة رسالة حب 💌</h3>
            <div>
                <label class="block text-xs text-gray-300 mb-1">اسم الكاتب:</label>
                <input type="text" id="noteAuthorInput" placeholder="عمر / فاطمة" class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none text-sm">
            </div>
            <div>
                <label class="block text-xs text-gray-300 mb-1">محتوى الرسالة:</label>
                <textarea id="noteContentInput" rows="4" placeholder="اكتب كلماتك الدافئة..." class="w-full bg-black/50 border border-white/20 rounded-xl px-3 py-2 text-white outline-none text-sm"></textarea>
            </div>
            <div class="flex justify-end gap-2 pt-2">
                <button onclick="closeNoteModal()" class="px-4 py-2 bg-gray-700 rounded-xl text-xs">إلغاء</button>
                <button onclick="saveLoveNote()" class="px-4 py-2 bg-rose-600 rounded-xl text-xs font-bold">حفظ الرسالة</button>
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        const DEFAULT_STATE = {
            name1: "عمر",
            name2: "فاطمة",
            startDate: "2024-01-01T00:00:00",
            pinCode: "1234",
            subtitle: '"تملي معاك، ولو حتى بعيد عني في قلبي هويتك.. أنت العمر والبداية والنهاية."',
            musicUrl: "https://ia800902.us.archive.org/30/items/AmrDiab-TamallyMaak/01.%20Tamally%20Maak.mp3",
            trackName: "تملي معاك - عمرو دياب",
            timeline: [
                { id: 1, title: "أول كلمة اتكلمنا فيها", date: "2024-01-01", desc: "اليوم اللي أشرقت فيه شمس أجمل قصة حب في الدنيا." },
                { id: 2, title: "أول خروجة سوا", date: "2024-02-14", desc: "ضحكاتنا والأغاني اللي سمعناها وكان عمرو دياب بيغني في الخلفية." },
                { id: 3, title: "يوم الخطوبة", date: "2024-06-01", desc: "خطوة مباركة وعهد كملنا بيه مشوارنا مع بعض ❤" }
            ],
            gallery: [
                { id: 1, url: "https://images.unsplash.com/photo-1518199266791-5375a83190b7?auto=format&fit=crop&w=600&q=80", caption: "لحظات دافية تجمعنا ❤" },
                { id: 2, url: "https://images.unsplash.com/photo-1522673607200-164d1b6ce486?auto=format&fit=crop&w=600&q=80", caption: "تملي معاك وفي بالي" },
                { id: 3, url: "https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?auto=format&fit=crop&w=600&q=80", caption: "ايدنا في ايد بعض دايماً" }
            ],
            notes: [
                { id: 1, author: "عمر", content: "فاطمة، أنتِ أجمل حاجة حصلت في حياتي كلها، وكل يوم معاكِ يعادل عمر كامل.", date: "2024-03-10" },
                { id: 2, author: "فاطمة", content: "عمر، ربنا يديمك ليا سند وحبيب وأجمل حظ في الدنيا دي كلها.", date: "2024-03-12" }
            ]
        };

        let appData = JSON.parse(localStorage.getItem('omar_fatima_love_page')) || DEFAULT_STATE;
        let editMode = false;
        let isAudioPlaying = false;

        window.addEventListener('DOMContentLoaded', () => {
            initParticles();
            renderApp();
            startTimer();
            setupAudioProgress();
        });

        function saveState() {
            localStorage.setItem('omar_fatima_love_page', JSON.stringify(appData));
            renderApp();
        }

        // --- ENVELOPE & SECURITY ---
        function openEnvelope() {
            document.getElementById('envelopeElement').classList.add('open');
        }

        function checkPin() {
            const pinVal = document.getElementById('pinInput').value.trim();
            if (pinVal === appData.pinCode || pinVal === '1234') {
                enterApp();
            } else {
                document.getElementById('pinError').classList.remove('hidden');
            }
        }

        function bypassPin() {
            enterApp();
        }

        function enterApp() {
            const overlay = document.getElementById('introOverlay');
            const mainContent = document.getElementById('mainContent');
            
            overlay.classList.add('opacity-0');
            setTimeout(() => {
                overlay.classList.add('hidden');
                mainContent.classList.remove('opacity-0');
                playAudio();
            }, 700);
        }

        // --- RENDER FUNCTION ---
        function renderApp() {
            const coupleNamesAr = `${appData.name1} و ${appData.name2}`;

            document.getElementById('navTitle').innerText = coupleNamesAr;
            document.getElementById('heroTitle').innerText = coupleNamesAr;
            document.getElementById('heroSubtitle').innerText = appData.subtitle;
            document.getElementById('footerNames').innerText = coupleNamesAr;
            document.getElementById('startDateDisplay').innerText = appData.startDate.split('T')[0];
            document.getElementById('musicTrackTitle').innerText = appData.trackName || "تملي معاك 🎶";

            // Render Timeline
            const tlContainer = document.getElementById('timelineList');
            tlContainer.innerHTML = appData.timeline.map(item => `
                <div class="relative group">
                    <div class="absolute -right-[31px] md:-right-[39px] top-1 w-5 h-5 rounded-full bg-rose-500 border-4 border-slate-950 group-hover:scale-125 transition"></div>
                    <div class="glass-card rounded-2xl p-4 relative">
                        ${editMode ? `<button onclick="deleteTimelineItem(${item.id})" class="absolute left-3 top-3 text-red-400 hover:text-red-300 text-xs"><i class="fa-solid fa-trash"></i></button>` : ''}
                        <span class="text-xs font-mono text-rose-400 block mb-1">${item.date}</span>
                        <h4 class="font-bold text-rose-200 text-base font-tajawal mb-1">${item.title}</h4>
                        <p class="text-xs text-gray-300 leading-relaxed font-tajawal">${item.desc}</p>
                    </div>
                </div>
            `).join('');

            // Render Gallery Grid
            const galleryContainer = document.getElementById('galleryGrid');
            galleryContainer.innerHTML = appData.gallery.map(img => `
                <div class="glass-card rounded-2xl p-2 relative overflow-hidden group">
                    ${editMode ? `<button onclick="deletePhotoItem(${img.id})" class="absolute left-3 top-3 z-10 bg-black/60 text-red-400 p-1.5 rounded-full text-xs hover:bg-black"><i class="fa-solid fa-trash"></i></button>` : ''}
                    <div class="h-48 rounded-xl overflow-hidden mb-2">
                        <img src="${img.url}" alt="Memory" class="w-full h-full object-cover group-hover:scale-110 transition duration-500" onerror="this.src='https://placehold.co/600x400/881337/ffffff?text=Amr+Diab+Love'">
                    </div>
                    <p class="text-xs text-center text-rose-200 font-tajawal py-1 truncate">${img.caption || 'ذكرى هادئة'}</p>
                </div>
            `).join('');

            // Render Love Notes Grid
            const notesContainer = document.getElementById('notesGrid');
            notesContainer.innerHTML = appData.notes.map(note => `
                <div class="bg-gradient-to-br from-rose-950/60 to-purple-950/60 border border-pink-500/30 rounded-2xl p-4 relative shadow-lg flex flex-col justify-between">
                    ${editMode ? `<button onclick="deleteLoveNote(${note.id})" class="absolute left-3 top-3 text-red-400 text-xs"><i class="fa-solid fa-trash"></i></button>` : ''}
                    <p class="text-sm text-rose-100 font-tajawal leading-relaxed mb-4 italic">"${note.content}"</p>
                    <div class="flex justify-between items-center text-xs text-rose-300/70 border-t border-white/10 pt-2 font-mono">
                        <span class="font-bold font-tajawal text-rose-300">من: ${note.author}</span>
                        <span>${note.date || ''}</span>
                    </div>
                </div>
            `).join('');

            // Populate settings inputs
            document.getElementById('editName1').value = appData.name1;
            document.getElementById('editName2').value = appData.name2;
            document.getElementById('editStartDate').value = appData.startDate.split('T')[0];
            document.getElementById('editPinCode').value = appData.pinCode;
            document.getElementById('editMusicUrl').value = appData.musicUrl;
            document.getElementById('editHeroSubtitle').value = appData.subtitle;
        }

        // --- TIMER ---
        function startTimer() {
            setInterval(() => {
                const start = new Date(appData.startDate).getTime();
                const now = new Date().getTime();
                const diff = now - start;

                if (diff > 0) {
                    const years = Math.floor(diff / (1000 * 60 * 60 * 24 * 365.25));
                    const days = Math.floor((diff % (1000 * 60 * 60 * 24 * 365.25)) / (1000 * 60 * 60 * 24));
                    const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                    const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                    const seconds = Math.floor((diff % (1000 * 60)) / 1000);

                    document.getElementById('timerYears').innerText = years;
                    document.getElementById('timerDays').innerText = days;
                    document.getElementById('timerHours').innerText = hours;
                    document.getElementById('timerMinutes').innerText = minutes;
                    document.getElementById('timerSeconds').innerText = seconds;
                }
            }, 1000);
        }

        // --- EDIT MODE TOGGLE ---
        function toggleEditMode() {
            editMode = !editMode;
            const btnText = document.getElementById('editBtnText');
            const panel = document.getElementById('editSettingsPanel');
            const addTlBtn = document.getElementById('addTimelineBtn');
            const addPhotoBtn = document.getElementById('addPhotoBtn');

            if (editMode) {
                btnText.innerText = "إغلاق التعديل";
                panel.classList.remove('hidden');
                addTlBtn.classList.remove('hidden');
                addPhotoBtn.classList.remove('hidden');
            } else {
                btnText.innerText = "تعديل";
                panel.classList.add('hidden');
                addTlBtn.classList.add('hidden');
                addPhotoBtn.classList.add('hidden');
            }
            renderApp();
        }

        function saveGeneralSettings() {
            appData.name1 = document.getElementById('editName1').value.trim() || "عمر";
            appData.name2 = document.getElementById('editName2').value.trim() || "فاطمة";
            appData.startDate = document.getElementById('editStartDate').value + "T00:00:00";
            appData.pinCode = document.getElementById('editPinCode').value.trim() || "1234";
            appData.subtitle = document.getElementById('editHeroSubtitle').value.trim();
            
            const newMusic = document.getElementById('editMusicUrl').value.trim();
            if (newMusic !== appData.musicUrl) {
                appData.musicUrl = newMusic;
                document.getElementById('audioSource').src = newMusic;
                document.getElementById('bgAudio').load();
            }

            saveState();
            alert("تم حفظ التعديلات بنجاح! ❤");
        }

        function resetToDefaults() {
            if (confirm("هل أنت تأكد من إعادة ضبط الصفحة للوضع الافتراضي؟")) {
                appData = DEFAULT_STATE;
                saveState();
            }
        }

        // --- MODAL ACTIONS ---
        function openAddTimelineModal() { document.getElementById('timelineModal').classList.remove('hidden'); }
        function closeTimelineModal() { document.getElementById('timelineModal').classList.add('hidden'); }
        function saveTimelineItem() {
            const title = document.getElementById('tlTitleInput').value.trim();
            const date = document.getElementById('tlDateInput').value;
            const desc = document.getElementById('tlDescInput').value.trim();

            if (title && date) {
                appData.timeline.push({ id: Date.now(), title, date, desc });
                saveState();
                closeTimelineModal();
            }
        }
        function deleteTimelineItem(id) {
            appData.timeline = appData.timeline.filter(item => item.id !== id);
            saveState();
        }

        function triggerPhotoUpload() { document.getElementById('photoFileInput').click(); }
        function handlePhotoUpload(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(evt) {
                    const caption = prompt("اكتب تعليقاً على الصورة:") || "ذكرى جميلة";
                    appData.gallery.push({ id: Date.now(), url: evt.target.result, caption });
                    saveState();
                };
                reader.readAsDataURL(file);
            }
        }
        function deletePhotoItem(id) {
            appData.gallery = appData.gallery.filter(item => item.id !== id);
            saveState();
        }

        function openNoteModal() { document.getElementById('noteModal').classList.remove('hidden'); }
        function closeNoteModal() { document.getElementById('noteModal').classList.add('hidden'); }
        function saveLoveNote() {
            const author = document.getElementById('noteAuthorInput').value.trim() || appData.name1;
            const content = document.getElementById('noteContentInput').value.trim();

            if (content) {
                appData.notes.push({
                    id: Date.now(),
                    author,
                    content,
                    date: new Date().toISOString().split('T')[0]
                });
                saveState();
                closeNoteModal();
            }
        }
        function deleteLoveNote(id) {
            appData.notes = appData.notes.filter(n => n.id !== id);
            saveState();
        }

        // --- AUDIO PLAYER ---
        function toggleAudio() {
            const audio = document.getElementById('bgAudio');
            if (isAudioPlaying) {
                audio.pause();
                isAudioPlaying = false;
                updateAudioUI(false);
            } else {
                playAudio();
            }
        }

        function playAudio() {
            const audio = document.getElementById('bgAudio');
            audio.play().then(() => {
                isAudioPlaying = true;
                updateAudioUI(true);
            }).catch(() => {
                isAudioPlaying = false;
                updateAudioUI(false);
            });
        }

        function updateAudioUI(playing) {
            const mainIcon = document.getElementById('mainPlayIcon');
            const navIcon = document.getElementById('navMusicIcon');
            const discIcon = document.getElementById('musicDiscIcon');

            if (playing) {
                mainIcon.className = "fa-solid fa-pause text-lg";
                navIcon.className = "fa-solid fa-compact-disc animate-spin text-xs text-rose-400";
                discIcon.classList.add('animate-spin');
            } else {
                mainIcon.className = "fa-solid fa-play text-lg ml-0.5";
                navIcon.className = "fa-solid fa-music text-xs";
                discIcon.classList.remove('animate-spin');
            }
        }

        function setupAudioProgress() {
            const audio = document.getElementById('bgAudio');
            const progressBar = document.getElementById('audioProgressBar');

            audio.addEventListener('timeupdate', () => {
                if (audio.duration) {
                    const pct = (audio.currentTime / audio.duration) * 100;
                    progressBar.style.width = pct + '%';
                }
            });
        }

        function seekAudio(e) {
            const audio = document.getElementById('bgAudio');
            const rect = e.currentTarget.getBoundingClientRect();
            const clickPos = (e.clientX - rect.left) / rect.width;
            if (audio.duration) {
                audio.currentTime = clickPos * audio.duration;
            }
        }

        // --- ANIMATED FLOATING HEARTS ---
        function initParticles() {
            const container = document.getElementById('heartsContainer');
            const icons = ['fa-heart', 'fa-sparkles', 'fa-heart font-thin'];
            
            setInterval(() => {
                if (document.hidden) return;
                const particle = document.createElement('i');
                const randomIcon = icons[Math.floor(Math.random() * icons.length)];
                particle.className = `fa-solid ${randomIcon} heart-particle`;
                
                particle.style.left = Math.random() * 100 + 'vw';
                particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
                particle.style.fontSize = (Math.random() * 16 + 10) + 'px';
                
                container.appendChild(particle);

                setTimeout(() => {
                    particle.remove();
                }, 6000);
            }, 350);
        }
    </script>
</body>
</html>
```# jubilant-sniffle
موقع حب
