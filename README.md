# nishinaripeacebreeze
西成ピースブリーズ公式サイト
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>西成ピースブリーズ</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        coffee: '#c0ffee',
                    }
                }
            }
        }
    </script>
    <style>
        ruby rt {
            font-size: 0.6em;
            color: #555;
        }
    </style>
</head>
<body class="bg-amber-50/30 text-stone-800 font-sans min-h-screen flex flex-col">

    <!-- ヘッダー -->
    <header class="bg-coffee shadow-md py-4 px-6 sticky top-0 z-50">
        <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4">
            <div>
                <h1 class="text-2xl md:text-3xl font-bold tracking-wide text-stone-900">
                    <ruby>Peace Breeze<rt>ぴーすぶりーず</rt></ruby> / <ruby>西成<rt>にしなり</rt></ruby>ピースブリーズ
                </h1>
            </div>

            <!-- 多言語ボタン（大きめでまあるい白いボタン） -->
            <div class="flex flex-wrap gap-2 justify-center" id="lang-buttons">
                <button onclick="changeLang('en')" class="bg-white hover:bg-stone-100 text-stone-800 font-bold px-5 py-2.5 rounded-full shadow transition text-sm">English</button>
                <button onclick="changeLang('zh')" class="bg-white hover:bg-stone-100 text-stone-800 font-bold px-5 py-2.5 rounded-full shadow transition text-sm">中文</button>
                <button onclick="changeLang('vi')" class="bg-white hover:bg-stone-100 text-stone-800 font-bold px-5 py-2.5 rounded-full shadow transition text-sm">Tiếng Việt</button>
                <button onclick="changeLang('ne')" class="bg-white hover:bg-stone-100 text-stone-800 font-bold px-5 py-2.5 rounded-full shadow transition text-sm">नेपाली</button>
            </div>

            <div>
                <button onclick="toggleEditMode()" id="edit-toggle-btn" class="bg-stone-900 text-white px-4 py-2 rounded-lg text-xs font-semibold shadow hover:bg-stone-800 transition">
                    ✏️ へんしゅうモード ON/OFF
                </button>
            </div>
        </div>
    </header>

    <!-- メインコンテンツ -->
    <main class="flex-grow max-w-6xl w-full mx-auto p-4 md:p-6 flex flex-col gap-6">

        <!-- 写真①・写真②（左右に動くカルーセル/スライダー） -->
        <section class="bg-white rounded-2xl shadow-sm p-4 overflow-hidden border border-coffee/30">
            <h2 class="text-sm font-bold text-stone-500 mb-2"><ruby>写真<rt>しゃしん</rt></ruby>①・<ruby>写真<rt>しゃしん</rt></ruby>②</h2>
            <div class="relative w-full overflow-hidden rounded-xl bg-stone-100 min-h-[250px] md:min-h-[380px] flex items-center justify-center">
                <!-- スライダー画像コンテナ -->
                <div id="slider-container" class="flex transition-transform duration-500 ease-in-out w-full h-full">
                    <div class="w-full flex-shrink-0 flex items-center justify-center p-2">
                        <img id="slide-img-0" src="FB_IMG_1793884997277.jpg" alt="写真1" class="max-h-[350px] object-contain rounded-lg shadow w-full">
                    </div>
                    <div class="w-full flex-shrink-0 flex items-center justify-center p-2">
                        <img id="slide-img-1" src="FB_IMG_1793887650556.jpg" alt="写真2" class="max-h-[350px] object-contain rounded-lg shadow w-full">
                    </div>
                </div>
                <!-- 左右切替ボタン -->
                <button onclick="prevSlide()" class="absolute left-3 bg-white/80 hover:bg-white text-stone-800 p-3 rounded-full shadow font-bold text-lg">&lt;</button>
                <button onclick="nextSlide()" class="absolute right-3 bg-white/80 hover:bg-white text-stone-800 p-3 rounded-full shadow font-bold text-lg">&gt;</button>
            </div>

            <!-- 編集モード時の画像変更機能 -->
            <div id="image-edit-section" class="hidden mt-3 p-3 bg-amber-50 rounded-lg border border-amber-200 text-xs">
                <p class="font-bold text-stone-700 mb-2">📷 写真の差し替え（お持ちのパソコンから画像ファイルを選べます）</p>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                    <div>
                        <label class="block text-stone-600 mb-1">写真①を変更:</label>
                        <input type="file" id="file-img-0" accept="image/*" onchange="uploadImage(event, 0)" class="w-full p-1 border rounded bg-white">
                    </div>
                    <div>
                        <label class="block text-stone-600 mb-1">写真②を変更:</label>
                        <input type="file" id="file-img-1" accept="image/*" onchange="uploadImage(event, 1)" class="w-full p-1 border rounded bg-white">
                    </div>
                </div>
            </div>
        </section>

        <!-- あなたの言葉 -->
        <section class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
            <h2 class="text-sm font-bold text-stone-400 mb-2"><ruby>言葉<rt>ことば</rt></ruby></h2>
            <div id="intro-text" class="text-lg md:text-xl leading-relaxed text-stone-800 font-medium">
                <ruby>西成区<rt>にしなりく</rt></ruby>で<ruby>住<rt>す</rt></ruby>んだり、<ruby>仕事<rt>しごと</rt></ruby>をしたり、<ruby>学校<rt>がっこう</rt></ruby>に<ruby>行<rt>い</rt></ruby>ったりしている、<ruby>子供<rt>こども</rt></ruby>や おとなや、<ruby>外国人<rt>がいこくじん</rt></ruby>の<ruby>方<rt>かた</rt></ruby>が <ruby>笑顔<rt>えがお</rt></ruby>で<ruby>暮<rt>く</rt></ruby>らせる<ruby>町<rt>まち</rt></ruby>を いっしょにつくって、その<ruby>平和<rt>へいわ</rt></ruby>な<ruby>空気<rt>くうき</rt></ruby>を<ruby>世界<rt>せかい</rt></ruby>に<ruby>広<rt>ひろ</rt></ruby>げたい、と<ruby>思<rt>おも</rt></ruby>う おとな<ruby>5人<rt>ごにん</rt></ruby>が<ruby>集<rt>あつ</rt></ruby>まった<ruby>団体<rt>だんたい</rt></ruby>です。
            </div>
        </section>

        <!-- ナビゲーションボタン群 -->
        <section class="grid grid-cols-2 md:grid-cols-3 gap-4">
            <a href="#oshirase-1" class="bg-coffee/40 hover:bg-coffee/70 p-4 rounded-xl text-center font-bold text-stone-950 shadow-sm transition block">
                <ruby>御知<rt>おし</rt></ruby>らせ
            </a>
            <a href="#nishinari" class="bg-coffee/40 hover:bg-coffee/70 p-4 rounded-xl text-center font-bold text-stone-950 shadow-sm transition block">
                <ruby>西成区<rt>にしなりく</rt></ruby>とは
            </a>
            <a href="#useful" class="bg-coffee/40 hover:bg-coffee/70 p-4 rounded-xl text-center font-bold text-stone-950 shadow-sm transition block">
                くらしに<ruby>役立<rt>やくだつ</rt></ruby>サイト
            </a>
            <a href="#kodomo" class="bg-coffee/40 hover:bg-coffee/70 p-4 rounded-xl text-center font-bold text-stone-950 shadow-sm transition block">
                こども<ruby>食堂<rt>しょくどう</rt></ruby>など
            </a>
            <a href="#about" class="bg-coffee/40 hover:bg-coffee/70 p-4 rounded-xl text-center font-bold text-stone-950 shadow-sm transition block">
                わたしたちについて
            </a>
            <a href="#contact" class="bg-coffee/40 hover:bg-coffee/70 p-4 rounded-xl text-center font-bold text-stone-950 shadow-sm transition block">
                <ruby>問合<rt>といあわ</rt></ruby>わせ
            </a>
        </section>

        <!-- おしらせ枠 ① と ② -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <section id="oshirase-1" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-lg font-bold text-stone-900 mb-3 border-b pb-2"><ruby>御知<rt>おし</rt></ruby>らせ ①</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="oshirase1">
                    <p>ここに おしらせ① の<ruby>内容<rt>ないよう</rt></ruby>がはいります。<ruby>編集<rt>へんしゅう</rt></ruby>モードをONにすると、この<ruby>文字<rt>もじ</rt></ruby>を<ruby>自由<rt>じゆう</rt></ruby>に<ruby>書き換<rt>かきか</rt></ruby>えられます。</p>
                </div>
            </section>

            <section id="oshirase-2" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-lg font-bold text-stone-900 mb-3 border-b pb-2"><ruby>御知<rt>おし</rt></ruby>らせ ②</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="oshirase2">
                    <p>ここに おしらせ② の<ruby>内容<rt>ないよう</rt></ruby>がはいります。</p>
                </div>
            </section>
        </div>

        <!-- 各セクション詳細 -->
        <div class="space-y-6">
            <section id="nishinari" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-xl font-bold text-stone-900 mb-2"><ruby>西成区<rt>にしなりく</rt></ruby>とは</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="sec_nishinari">
                    <p><ruby>西成区<rt>にしなりく</rt></ruby>の<ruby>魅力<rt>みりょく</rt></ruby>や<ruby>地域<rt>ちいき</rt></ruby>の<ruby>情報<rt>じょうほう</rt></ruby>をここに<ruby>書<rt>か</rt></ruby>きます。</p>
                </div>
            </section>

            <section id="useful" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-xl font-bold text-stone-900 mb-2">くらしに<ruby>役立<rt>やくだつ</rt></ruby>サイト</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="sec_useful">
                    <p><ruby>生活<rt>せいかつ</rt></ruby>に<ruby>役立<rt>やくだつ</rt></ruby>リンクや<ruby>情報<rt>じょうほう</rt></ruby>をここに<ruby>掲載<rt>けいさい</rt></ruby>します。</p>
                </div>
            </section>

            <section id="kodomo" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-xl font-bold text-stone-900 mb-2">こども<ruby>食堂<rt>しょくどう</rt></ruby>など</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="sec_kodomo">
                    <p>こども<ruby>食堂<rt>しょくどう</rt></ruby>や<ruby>地域<rt>ちいき</rt></ruby>の<ruby>活動<rt>かつどう</rt></ruby>の<ruby>情報<rt>じょうほう</rt></ruby>をここに<ruby>書<rt>か</rt></ruby>きます。</p>
                </div>
            </section>

            <section id="about" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-xl font-bold text-stone-900 mb-2">わたしたちについて</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="sec_about">
                    <p>おとな5人の<ruby>成員<rt>たから</rt></ruby>や<ruby>団体<rt>だんたい</rt></ruby>の<ruby>目的<rt>もくてき</rt></ruby>をさらに<ruby>詳<rt>くわ</rt></ruby>しく<ruby>紹介<rt>しょうかい</rt></ruby>します。</p>
                </div>
            </section>

            <section id="contact" class="bg-white rounded-2xl shadow-sm p-6 border border-coffee/30">
                <h3 class="text-xl font-bold text-stone-900 mb-2"><ruby>問合<rt>といあわ</rt></ruby>わせ</h3>
                <div class="editable-content text-stone-700" contenteditable="false" data-key="sec_contact">
                    <p><ruby>連絡先<rt>れんらくさき</rt></ruby>やメールアドレスなどをここに<ruby>記載<rt>きさい</rt></ruby>します。</p>
                </div>
            </section>
        </div>

    </main>

    <footer class="bg-stone-900 text-white text-center py-6 mt-12 text-sm">
        <p>&copy; Nishinari Peace Breeze</p>
    </footer>

    <!-- スクリプト制御 -->
    <script>
        // スライダー機能
        let currentSlide = 0;
        const totalSlides = 2;
        function updateSlide() {
            const container = document.getElementById('slider-container');
            container.style.transform = `translateX(-${currentSlide * 100}%)`;
        }
        function nextSlide() {
            currentSlide = (currentSlide + 1) % totalSlides;
            updateSlide();
        }
        function prevSlide() {
            currentSlide = (currentSlide - 1 + totalSlides) % totalSlides;
            updateSlide();
        }
        setInterval(nextSlide, 5000);

        // 多言語切り替え辞書
        const translations = {
            ja: {
                title: "Peace Breeze / 西成ピースブリーズ",
                intro: "西成区で住んだり、仕事をしたり、学校に行ったりしている、子どもや おとなや、外国人の方が 笑顔で暮らせる町を いっしょにつくって、その平和な空気を世界に広げたい、と思う おとな5人が集まった団体です。"
            },
            en: {
                title: "Peace Breeze / Nishinari Peace Breeze",
                intro: "We are a group of 5 adults who want to create a town where children, adults, and foreigners living, working, or going to school in Nishinari Ward can live with a smile, and spread that peaceful air to the world."
            },
            zh: {
                title: "Peace Breeze / 西成和平微风",
                intro: "我们是由5名成年人组成的团体，希望在西成区创造一个让生活、工作或上学的儿童、成人和外国居民都能微笑着生活的小镇，并将这种和平的氛围传播到世界。"
            },
            vi: {
                title: "Peace Breeze / Gió Bình Yên Nishinari",
                intro: "Chúng tôi là nhóm 5 người lớn mong muốn xây dựng một thị trấn nơi trẻ em, người lớn và người nước ngoài sinh sống, làm việc hoặc đi học tại Phường Nishinari có thể sống với nụ cười và lan tỏa bầu không khí hòa bình đó ra thế giới."
            },
            ne: {
                title: "Peace Breeze / निसिनारी पिस ब्रिज",
                intro: "हामी ५ जना वयस्कहरूको समूह हौं जसले निसिनारी वार्डमा बसोबास गर्ने, काम गर्ने वा पढ्ने बालबालिका, वयस्क र विदेशीहरू मुस्कानका साथ बाच्न सक्ने सहर बनाउन र त्यो शान्त वातावरणलाई विश्वमा फैलाउन चाहन्छौं।"
            }
        };

        function changeLang(lang) {
            const t = translations[lang];
            if (!t) return;
            document.querySelector('header h1').innerHTML = `<ruby>${t.title}</ruby>`;
            document.getElementById('intro-text').innerText = t.intro;
        }

        // 編集モード切り替え
        let isEditMode = false;
        function toggleEditMode() {
            isEditMode = !isEditMode;
            const editables = document.querySelectorAll('.editable-content');
            const imgSection = document.getElementById('image-edit-section');
            const btn = document.getElementById('edit-toggle-btn');

            if (isEditMode) {
                btn.classList.add('bg-amber-600');
                btn.innerText = "💾 編集中 (クリックで保存)";
                imgSection.classList.remove('hidden');
                editables.forEach(el => {
                    el.setAttribute('contenteditable', 'true');
                    el.classList.add('border', 'border-amber-400', 'bg-amber-50/50', 'p-2', 'rounded');
                });
            } else {
                btn.classList.remove('bg-amber-600');
                btn.innerText = "✏️ へんしゅうモード ON/OFF";
                imgSection.classList.add('hidden');
                editables.forEach(el => {
                    el.setAttribute('contenteditable', 'false');
                    el.classList.remove('border', 'border-amber-400', 'bg-amber-50/50', 'p-2', 'rounded');
                    localStorage.setItem(el.getAttribute('data-key'), el.innerHTML);
                });
                alert("変更内容をブラウザに保存しました！");
            }
        }

        // ローカル画像ファイルのアップロードと保存処理
        function uploadImage(event, index) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const result = e.target.result;
                    document.getElementById(`slide-img-${index}`).src = result;
                    try {
                        localStorage.setItem(`img_${index}`, result);
                        alert(`写真${index + 1}を更新・保存しました！`);
                    } catch(err) {
                        alert(`写真${index + 1}を画面上に反映しました（ブラウザの記憶制限により永続保存は画像サイズを小さくする必要があります）。`);
                    }
                };
                reader.readAsDataURL(file);
            }
        }

        // ページ読み込み時に保存されたデータを復元
        window.onload = function() {
            document.querySelectorAll('.editable-content').forEach(el => {
                const saved = localStorage.getItem(el.getAttribute('data-key'));
                if(saved) el.innerHTML = saved;
            });
            const savedImg0 = localStorage.getItem('img_0');
            const savedImg1 = localStorage.getItem('img_1');
            if(savedImg0) document.getElementById('slide-img-0').src = savedImg0;
            if(savedImg1) document.getElementById('slide-img-1').src = savedImg1;
        };
    </script>
</body>
</html>
