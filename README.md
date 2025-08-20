
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>耳鳴緩解小助手</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#4F46E5',
                        secondary: '#10B981',
                        neutral: '#F3F4F6',
                        dark: '#1F2937'
                    },
                    fontFamily: {
                        sans: ['Helvetica', 'Arial', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto {
                content-visibility: auto;
            }
            .step-active {
                @apply bg-primary text-white;
            }
            .audio-wave {
                @apply h-2 bg-primary/30 rounded-full inline-block animate-pulse;
            }
            .card-shadow {
                @apply shadow-lg rounded-2xl overflow-hidden transform transition-all duration-300 hover:scale-[1.02];
            }
        }
    </style>
</head>
<body class="bg-neutral min-h-screen font-sans text-dark">
    <!-- 頂部進度條 -->
    <div class="fixed top-0 left-0 right-0 bg-white shadow-sm z-50">
        <div class="container mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-1">
                <div id="step1-indicator" class="w-8 h-8 rounded-full flex items-center justify-center step-active">1</div>
                <div class="h-1 bg-gray-200 flex-1 max-w-[50px]">
                    <div id="progress1" class="h-full bg-primary w-0 transition-all duration-500"></div>
                </div>
                <div id="step2-indicator" class="w-8 h-8 rounded-full flex items-center justify-center bg-gray-200 text-gray-500">2</div>
                <div class="h-1 bg-gray-200 flex-1 max-w-[50px]">
                    <div id="progress2" class="h-full bg-primary w-0 transition-all duration-500"></div>
                </div>
                <div id="step3-indicator" class="w-8 h-8 rounded-full flex items-center justify-center bg-gray-200 text-gray-500">3</div>
            </div>
            <div class="text-sm text-gray-500" id="step-text">聽聲音</div>
        </div>
    </div>

    <!-- 主內容區 -->
    <main class="container mx-auto px-4 pt-24 pb-20">
        <!-- 步驟1：聽聲音 -->
        <section id="step1" class="transition-all duration-500 opacity-100">
            <h2 class="text-[clamp(1.5rem,5vw,2.5rem)] font-bold text-center mb-8">你聽到的聲音是？</h2>
            
            <div class="grid gap-6 mb-10">
                <!-- 蟬鳴聲選項 -->
                <div class="bg-white rounded-xl p-6 card-shadow">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-xl font-semibold">蟬鳴聲</h3>
                        <div class="sound-player">
                            <button class="play-btn w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary" data-sound="cicada">
                                <i class="fa fa-play"></i>
                            </button>
                            <audio class="sound" id="cicada-sound" preload="auto">
                                <source src="https://assets.mixkit.co/sfx/preview/mixkit-cicada-calling-1293.mp3" type="audio/mpeg">
                            </audio>
                        </div>
                    </div>
                    <div class="sound-visualizer hidden" data-for="cicada">
                        <div class="audio-wave w-2" style="animation-delay: 0ms;"></div>
                        <div class="audio-wave w-4 mx-1" style="animation-delay: 100ms;"></div>
                        <div class="audio-wave w-6 mx-1" style="animation-delay: 200ms;"></div>
                        <div class="audio-wave w-4 mx-1" style="animation-delay: 300ms;"></div>
                        <div class="audio-wave w-2" style="animation-delay: 400ms;"></div>
                    </div>
                    <button class="select-sound w-full mt-4 py-3 bg-primary/10 hover:bg-primary/20 text-primary rounded-lg transition-colors duration-300 font-medium" data-sound="cicada">
                        這是我常聽到的聲音
                    </button>
                </div>

                <!-- 嗡嗡聲選項 -->
                <div class="bg-white rounded-xl p-6 card-shadow">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-xl font-semibold">嗡嗡聲</h3>
                        <div class="sound-player">
                            <button class="play-btn w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary" data-sound="buzz">
                                <i class="fa fa-play"></i>
                            </button>
                            <audio class="sound" id="buzz-sound" preload="auto">
                                <source src="https://assets.mixkit.co/sfx/preview/mixkit-electricity-buzz-1542.mp3" type="audio/mpeg">
                             Âudio
                        </div>
                    </div>
                    <div class="sound-visualizer hidden" data-for="buzz">
                        <div class="audio-wave w-4" style="animation-delay: 0ms;"></div>
                        <div class="audio-wave w-4 mx-1" style="animation-delay: 150ms;"></div>
                        <div class="audio-wave w-4 mx-1" style="animation-delay: 300ms;"></div>
                        <div class="audio-wave w-4 mx-1" style="animation-delay: 450ms;"></div>
                        <div class="audio-wave w-4" style="animation-delay: 600ms;"></div>
                    </div>
                    <button class="select-sound w-full mt-4 py-3 bg-primary/10 hover:bg-primary/20 text-primary rounded-lg transition-colors duration-300 font-medium" data-sound="buzz">
                        這是我常聽到的聲音
                    </button>
                </div>

                <!-- 電流聲選項 -->
                <div class="bg-white rounded-xl p-6 card-shadow">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-xl font-semibold">電流聲</h3>
                        <div class="sound-player">
                            <button class="play-btn w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary" data-sound="electric">
                                <i class="fa fa-play"></i>
                            </button>
                            <audio class="sound" id="electric-sound" preload="auto">
                                <source src="https://assets.mixkit.co/sfx/preview/mixkit-high-voltage-electricity-arc-1934.mp3" type="audio/mpeg">
                             Âudio
                        </div>
                    </div>
                    <div class="sound-visualizer hidden" data-for="electric">
                        <div class="audio-wave w-3" style="animation-delay: 0ms;"></div>
                        <div class="audio-wave w-6 mx-1" style="animation-delay: 50ms;"></div>
                        <div class="audio-wave w-2 mx-1" style="animation-delay: 100ms;"></div>
                        <div class="audio-wave w-5 mx-1" style="animation-delay: 150ms;"></div>
                        <div class="audio-wave w-3" style="animation-delay: 200ms;"></div>
                    </div>
                    <button class="select-sound w-full mt-4 py-3 bg-primary/10 hover:bg-primary/20 text-primary rounded-lg transition-colors duration-300 font-medium" data-sound="electric">
                        這是我常聽到的聲音
                    </button>
                </div>
            </div>

            <div class="text-center text-gray-500 text-sm">
                提示：點擊播放按鈕聽取聲音，選擇與你相似的耳鳴聲
            </div>
        </section>

        <!-- 步驟2：看案例 -->
        <section id="step2" class="transition-all duration-500 opacity-0 absolute inset-0 pointer-events-none">
            <h2 class="text-[clamp(1.5rem,5vw,2.5rem)] font-bold text-center mb-6">類似的情況</h2>
            
            <div class="bg-white rounded-2xl overflow-hidden card-shadow mb-8">
                <div id="case-image" class="h-56 bg-cover bg-center" style="background-image: url('https://picsum.photos/id/1074/800/400');"></div>
                <div class="p-6">
                    <h3 class="text-xl font-semibold mb-4" id="case-title">王爺爺的故事</h3>
                    <p class="text-gray-700 mb-6" id="case-description">
                        王爺爺和你一樣聽蟬鳴聲，他用"睡前聽10分鐘雨聲白噪音"，1個月後耳鳴頻率減少。
                    </p>
                    <div class="bg-secondary/10 p-4 rounded-lg border-l-4 border-secondary">
                        <p class="font-medium text-secondary">專家提示：</p>
                        <p class="text-gray-700 text-sm mt-1">白噪音可以掩蓋耳鳴聲，幫助大腦逐漸適應並減少對耳鳴的關注，從而緩解不適感。</p>
                    </div>
                </div>
            </div>

            <button id="to-step3" class="w-full py-4 bg-primary text-white rounded-xl font-medium shadow-md hover:bg-primary/90 transition-colors duration-300">
                獲取我的緩解建議
            </button>
        </section>

        <!-- 步驟3：存建議 -->
        <section id="step3" class="transition-all duration-500 opacity-0 absolute inset-0 pointer-events-none">
            <h2 class="text-[clamp(1.5rem,5vw,2.5rem)] font-bold text-center mb-6">你的耳鳴緩解小卡片</h2>
            
            <div class="mb-8 flex justify-center">
                <div id="advice-card" class="w-[90%] max-w-md bg-white rounded-2xl overflow-hidden card-shadow">
                    <div class="h-3 bg-primary"></div>
                    <div class="p-6 text-center">
                        <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fa fa-volume-up text-2xl text-primary"></i>
                        </div>
                        <h3 class="text-xl font-bold mb-2" id="advice-title">耳鳴緩解建議</h3>
                        <p class="text-gray-600 mb-6" id="advice-method">
                            睡前聽10分鐘雨聲白噪音，幫助減輕耳鳴帶來的不適。
                        </p>
                        <div class="text-xs text-gray-400">
                            堅持1個月，可能會看到改善
                        </div>
                    </div>
                    <div class="bg-gray-50 py-3 text-center text-xs text-gray-500">
                        耳鳴緩解小助手 · 建議僅供參考
                    </div>
                </div>
            </div>

            <button id="save-card" class="w-full py-4 bg-secondary text-white rounded-xl font-medium shadow-md hover:bg-secondary/90 transition-colors duration-300 mb-4">
                <i class="fa fa-download mr-2"></i> 保存到相冊
            </button>
            
            <div class="text-center text-gray-500 text-sm">
                <p>保存後可隨時查看你的專屬建議</p>
                <p class="mt-1">分享給有需要的朋友</p>
            </div>
        </section>
    </main>

    <!-- 底部提示 -->
    <div class="fixed bottom-0 left-0 right-0 bg-white py-3 text-center text-xs text-gray-500 shadow-[0_-1px_3px_rgba(0,0,0,0.1)]">
        注意：本工具僅提供參考建議，不能替代專業醫療診斷
    </div>

    <!-- 成功提示彈窗 -->
    <div id="toast" class="fixed top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-dark/80 text-white px-6 py-4 rounded-lg opacity-0 pointer-events-none transition-opacity duration-300 z-50">
        卡片已保存到相冊
    </div>

    <script>
        // 全局變量存儲用戶選擇
        let selectedSound = null;
        
        // 案例數據
        const cases = {
            cicada: {
                title: "王爺爺的故事",
                description: "王爺爺和你一樣聽蟬鳴聲，他用'睡前聽10分鐘雨聲白噪音'，1個月後耳鳴頻率減少。",
                image: "https://picsum.photos/id/1074/800/400",
                advice: "睡前聽10分鐘雨聲白噪音，幫助減輕耳鳴帶來的不適。"
            },
            buzz: {
                title: "李女士的經歷",
                description: "李女士經常聽到嗡嗡聲，她嘗試'每天冥想15分鐘放鬆身心'，堅持2個月後感覺耳鳴減輕了。",
                image: "https://picsum.photos/id/1062/800/400",
                advice: "每天冥想15分鐘放鬆身心，有助於減輕嗡嗡聲帶來的困擾。"
            },
            electric: {
                title: "張先生的方法",
                description: "張先生受到電流聲困擾，他採用'避免長時間戴耳機，調低電子設備音量'的方法，症狀有所改善。",
                image: "https://picsum.photos/id/1066/800/400",
                advice: "避免長時間戴耳機，調低電子設備音量，減少對聽覺系統的刺激。"
            }
        };

        // DOM元素
        const step1 = document.getElementById('step1');
        const step2 = document.getElementById('step2');
        const step3 = document.getElementById('step3');
        const stepText = document.getElementById('step-text');
        const progress1 = document.getElementById('progress1');
        const progress2 = document.getElementById('progress2');
        const step1Indicator = document.getElementById('step1-indicator');
        const step2Indicator = document.getElementById('step2-indicator');
        const step3Indicator = document.getElementById('step3-indicator');
        const toast = document.getElementById('toast');

        // 音頻播放功能
        document.querySelectorAll('.play-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                const soundType = this.getAttribute('data-sound');
                const audio = document.getElementById(`${soundType}-sound`);
                const visualizer = document.querySelector(`.sound-visualizer[data-for="${soundType}"]`);
                const icon = this.querySelector('i');
                
                // 停止其他正在播放的音頻
                document.querySelectorAll('.sound').forEach(sound => {
                    if (sound !== audio && !sound.paused) {
                        sound.pause();
                        sound.currentTime = 0;
                        const otherIcon = document.querySelector(`.play-btn[data-sound="${sound.id.split('-')[0]}"] i`);
                        otherIcon.classList.remove('fa-pause');
                        otherIcon.classList.add('fa-play');
                        document.querySelector(`.sound-visualizer[data-for="${sound.id.split('-')[0]}"]`).classList.add('hidden');
                    }
                });
                
                // 控制當前音頻播放/暫停
                if (audio.paused) {
                    audio.play();
                    icon.classList.remove('fa-play');
                    icon.classList.add('fa-pause');
                    visualizer.classList.remove('hidden');
                } else {
                    audio.pause();
                    icon.classList.remove('fa-pause');
                    icon.classList.add('fa-play');
                    visualizer.classList.add('hidden');
                }
                
                // 音頻結束時重置狀態
                audio.onended = function() {
                    icon.classList.remove('fa-pause');
                    icon.classList.add('fa-play');
                    visualizer.classList.add('hidden');
                };
            });
        });

        // 選擇聲音
        document.querySelectorAll('.select-sound').forEach(btn => {
            btn.addEventListener('click', function() {
                selectedSound = this.getAttribute('data-sound');
                
                // 更新按鈕樣式
                document.querySelectorAll('.select-sound').forEach(b => {
                    b.classList.remove('bg-primary', 'text-white');
                    b.classList.add('bg-primary/10', 'text-primary');
                });
                this.classList.remove('bg-primary/10', 'text-primary');
                this.classList.add('bg-primary', 'text-white');
                
                // 延遲後進入下一步
                setTimeout(() => {
                    goToStep(2);
                    // 更新案例內容
                    document.getElementById('case-title').textContent = cases[selectedSound].title;
                    document.getElementById('case-description').textContent = cases[selectedSound].description;
                    document.getElementById('case-image').style.backgroundImage = `url('${cases[selectedSound].image}')`;
                }, 500);
            });
        });

        // 前往步驟3
        document.getElementById('to-step3').addEventListener('click', function() {
            goToStep(3);
            // 更新建議內容
            document.getElementById('advice-method').textContent = cases[selectedSound].advice;
        });

        // 保存卡片到相冊
        document.getElementById('save-card').addEventListener('click', function() {
            // 顯示保存提示
            showToast();
        });

        // 步驟切換函數
        function goToStep(step) {
            // 重置所有步驟
            [step1, step2, step3].forEach(el => {
                el.classList.add('opacity-0', 'absolute', 'inset-0', 'pointer-events-none');
                el.classList.remove('opacity-100', 'relative');
            });
            
            // 顯示目標步驟
            const targetStep = document.getElementById(`step${step}`);
            targetStep.classList.remove('opacity-0', 'absolute', 'inset-0', 'pointer-events-none');
            targetStep.classList.add('opacity-100', 'relative');
            
            // 更新步驟指示器
            [step1Indicator, step2Indicator, step3Indicator].forEach((el, i) => {
                if (i + 1 < step) {
                    el.classList.remove('bg-gray-200', 'text-gray-500');
                    el.classList.add('step-active');
                } else if (i + 1 === step) {
                    el.classList.remove('bg-gray-200', 'text-gray-500');
                    el.classList.add('step-active');
                } else {
                    el.classList.remove('step-active');
                    el.classList.add('bg-gray-200', 'text-gray-500');
                }
            });
            
            // 更新進度條
            if (step > 1) progress1.style.width = '100%';
            else progress1.style.width = '0';
            
            if (step > 2) progress2.style.width = '100%';
            else progress2.style.width = '0';
            
            // 更新步驟文本
            const stepTexts = ['聽聲音', '看案例', '存建議'];
            stepText.textContent = stepTexts[step - 1];
            
            // 滾動到頂部
            window.scrollTo(0, 0);
        }

        // 顯示提示彈窗
        function showToast() {
            toast.classList.remove('opacity-0', 'pointer-events-none');
            toast.classList.add('opacity-100', 'pointer-events-auto');
            
            setTimeout(() => {
                toast.classList.remove('opacity-100', 'pointer-events-auto');
                toast.classList.add('opacity-0', 'pointer-events-none');
            }, 2000);
        }

        // 初始化頁面
        window.addEventListener('DOMContentLoaded', () => {
            goToStep(1);
        });
    </script>
</body>
</html>
