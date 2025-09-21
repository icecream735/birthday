[birthday.html](https://github.com/user-attachments/files/22450915/birthday.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>生日盲盒抽奖</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a1a2e, #16213e);
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            padding: 20px;
        }
        
        .container {
            background: rgba(0, 0, 0, 0.7);
            border-radius: 20px;
            padding: 30px;
            width: 100%;
            max-width: 500px;
            box-shadow: 0 0 30px rgba(255, 105, 180, 0.5);
            text-align: center;
            position: relative;
            z-index: 10;
        }
        
        .birthday-text {
            font-size: 3.5rem;
            font-weight: bold;
            margin-bottom: 20px;
            background: linear-gradient(45deg, #ff6b6b, #ffa86b, #ffda6b, #6bff9e, #6bc7ff, #9d6bff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: gradientMove 5s ease infinite;
        }
.message {
    font-size: 1.2rem;
    margin-bottom: 25px;
    line-height: 1.6;
    color: #f0f0f0;
}

.btn-container {
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
}

.btn {
    background: linear-gradient(45deg, #ff6b6b, #ff9d6b);
    color: white;
    border: none;
    padding: 12px 25px;
    font-size: 1.1rem;
    border-radius: 50px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
}

.btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(255, 107, 107, 0.6);
}

.btn-alt {
    background: linear-gradient(45deg, #6b75ff, #6bc7ff);
    box-shadow: 0 5px 15px rgba(107, 117, 255, 0.4);
}

.hidden {
    display: none;
}

.progress-container {
    height: 10px;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 5px;
    margin: 20px 0;
    overflow: hidden;
}

.progress-bar {
    height: 100%;
    width: 0%;
    background: linear-gradient(45deg, #ff6b6b, #ff9d6b);
    border-radius: 5px;
    transition: width 0.5s ease;
}

.cake {
    font-size: 4rem;
    margin: 20px 0;
    text-shadow: 0 0 20px rgba(255, 107, 107, 0.8);
    animation: float 3s ease-in-out infinite;
}

.candle {
    font-size: 2rem;
    margin: 10px;
    cursor: pointer;
    transition: all 0.3s ease;
}

.wish-text {
    font-style: italic;
    color: #ffda6b;
    margin: 15px 0;
    padding: 15px;
    background: rgba(255, 218, 107, 0.1);
    border-radius: 10px;
    border-left: 4px solid #ffda6b;
}
.firework {
            position: absolute;
            width: 5px;
            height: 5px;
            border-radius: 50%;
            background: #ff6b6b;
            box-shadow: 0 0 10px #ff6b6b;
            animation: fireworkAnimation 1.5s ease-out forwards;
            z-index: 1;
        }
        
        @keyframes gradientMove {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        @keyframes fireworkAnimation {
            0% {
                transform: translate(0, 0) scale(0.5);
                opacity: 1;
            }
            100% {
                transform: translate(var(--tx), var(--ty)) scale(2);
                opacity: 0;
            }
        }
        
        @media (max-width: 600px) {
            .birthday-text {
                font-size: 2.5rem;
            }
            
            .message {
                font-size: 1rem;
            }
            
            .btn {
                padding: 10px 20px;
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="birthday-text">生日快乐！</h1>
        
        <div id="step1">
            <p class="message">鉴于今天是你的生日，为你准备了一个抽盲盒游戏，请问您是否参与？</p>
            <div class="btn-container">
                <button class="btn" onclick="nextStep(2)">是</button>
                <button class="btn btn-alt" onclick="nextStep(0)">否</button>
            </div>
        </div>
<div id="step2" class="hidden">
    <p class="message">请选择您中意的数字</p>
    <div class="btn-container">
        <button class="btn" onclick="selectNumber(3)">3</button>
        <button class="btn" onclick="selectNumber(7)">7</button>
        <button class="btn" onclick="selectNumber(9)">9</button>
    </div>
</div>

<div id="step3" class="hidden">
    <p class="message">即将为您打开盲盒，请稍候</p>
    <div class="progress-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>
</div>

<div id="step4" class="hidden">
    <div class="cake">🎂</div>
    <p class="message">恭喜您拆中一个蛋糕！请问需要为您插上蜡烛吗？</p>
    <div class="btn-container">
        <button class="btn" onclick="nextStep(5)">风吹走烦恼</button>
        <button class="btn btn-alt" onclick="nextStep(5)">自己就好</button>
    </div>
</div>

<div id="step5" class="hidden">
    <div class="cake">🎂</div>
    <p class="message">请问需要为您点上蜡烛吗？</p>
    <div class="btn-container">
        <button class="btn" onclick="lightCandle()">点</button>
    </div>
</div>
<div id="step6" class="hidden">
    <div class="cake">🎂</div>
    <div>
        <span class="candle" onclick="blowCandle(0)">🕯️</span>
        <span class="candle" onclick="blowCandle(1)">🕯️</span>
        <span class="candle" onclick="blowCandle(2)">🕯️</span>
    </div>
    <p class="message">请您许愿吧！</p>
    <div class="btn-container">
        <button class="btn" onclick="nextStep(7)">许好了</button>
    </div>
</div>

<div id="step7" class="hidden">
    <div class="cake">🎂</div>
    <p class="message">让我们吹蜡烛吧！</p>
    <div class="btn-container">
        <button class="btn" onclick="nextStep(8)">吹蜡烛</button>
    </div>
</div>

<div id="step8" class="hidden">
    <p class="wish-text">文字的开端当然是祝你生日快乐啦——岁有一岁的味道，一站有一站的风景。希望你与幸运撞个满怀，不论去哪儿，沿途都是风景。当然啦，也希望你可以永远奔赴在自己热爱中开心快乐。祝你的十八岁朗朗如风，行千山见朝阳，自成群峰巍峨。美好的事物一定会发生在新的一岁！</p>
    <p class="message">你的生日套餐服务已结束，满意请按1，不满意请按2</p>
    <div class="btn-container">
        <button class="btn" onclick="showRedPacket()">1</button>
        <button class="btn btn-alt" onclick="showRedPacket()">2</button>
    </div>
</div>
<div id="step9" class="hidden">
        <div class="cake">🎉</div>
        <p class="message">指令正确，系统奖金即将发放</p>
        <p class="message">恭喜发财，大吉大利</p>
        <div class="btn-container">
            <button class="btn" onclick="claimRedPacket()">领取红包</button>
        </div>
    </div>
    
    <div id="step10" class="hidden">
        <div class="cake">💰</div>
        <p class="message">已领取微信红包</p>
        <p class="wish-text">愿你拥有一个美好的生日！</p>
        <div class="btn-container">
            <button class="btn" onclick="restart()">再玩一次</button>
        </div>
    </div>
</div>
<script>
    // 简化版烟花效果
    function createFireworks() {
        setInterval(() => {
            const firework = document.createElement('div');
            firework.classList.add('firework');
            
            // 随机位置
            const startX = Math.random() * window.innerWidth;
            const startY = Math.random() * window.innerHeight;
            
            // 随机方向
            const angle = Math.random() * Math.PI * 2;
            const distance = 50 + Math.random() * 100;
            const tx = Math.cos(angle) * distance;
            const ty = Math.sin(angle) * distance;
            
            firework.style.left = startX + 'px';
            firework.style.top = startY + 'px';
            firework.style.setProperty('--tx', tx + 'px');
            firework.style.setProperty('--ty', ty + 'px');
            
            // 随机颜色
            const hue = Math.random() * 360;
            firework.style.background = `hsl(${hue}, 100%, 60%)`;
            firework.style.boxShadow = `0 0 10px hsl(${hue}, 100%, 60%)`;
            
            document.body.appendChild(firework);
            
            // 动画结束后移除元素
            setTimeout(() => {
                firework.remove();
            }, 1500);
        }, 200);
    }
    
    // 交互逻辑
    function hideAllSteps() {
        for (let i = 1; i <= 10; i++) {
            const step = document.getElementById(`step${i}`);
            if (step) step.classList.add('hidden');
        }
    }
    
    function nextStep(stepNum) {
        hideAllSteps();
        const nextStepElement = document.getElementById(`step${stepNum}`);
        if (nextStepElement) {
            setTimeout(() => {
                nextStepElement.classList.remove('hidden');
            }, 300);
            
            // 特殊步骤处理
            if (stepNum === 3) {
                simulateOpening();
            }
        }
    }
    
    function selectNumber(num) {
        hideAllSteps();
        setTimeout(() => {
            document.getElementById('step3').classList.remove('hidden');
            simulateOpening();
        }, 300);
    }
function simulateOpening() {
            const progressBar = document.getElementById('progressBar');
            let width = 0;
            const interval = setInterval(() => {
                if (width >= 100) {
                    clearInterval(interval);
                    setTimeout(() => {
                        hideAllSteps();
                        document.getElementById('step4').classList.remove('hidden');
                    }, 500);
                } else {
                    width += 2;
                    progressBar.style.width = width + '%';
                }
            }, 50);
        }
        
        function lightCandle() {
            hideAllSteps();
            setTimeout(() => {
                document.getElementById('step6').classList.remove('hidden');
            }, 300);
        }
        
        let candlesBlown = 0;
        function blowCandle(index) {
            const candles = document.querySelectorAll('.candle');
            if (candles[index].textContent === '🕯️') {
                candles[index].textContent = '💨';
                candles[index].style.opacity = '0.5';
                candlesBlown++;
                
                if (candlesBlown === 3) {
                    setTimeout(() => {
                        hideAllSteps();
                        document.getElementById('step7').classList.remove('hidden');
                    }, 800);
                }
            }
        }
        
        function showRedPacket() {
            hideAllSteps();
            setTimeout(() => {
                document.getElementById('step9').classList.remove('hidden');
            }, 300);
        }
        
        function claimRedPacket() {
            hideAllSteps();
            setTimeout(() => {
                document.getElementById('step10').classList.remove('hidden');
            }, 300);
        }
        
        function restart() {
            candlesBlown = 0;
            const candles = document.querySelectorAll('.candle');
            candles.forEach(candle => {
                candle.textContent = '🕯️';
                candle.style.opacity = '1';
            });
            
            hideAllSteps();
            setTimeout(() => {
                document.getElementById('step1').classList.remove('hidden');
            }, 300);
        }
        
        // 初始化
        window.onload = function() {
            createFireworks();
            // 确保第一步显示
            document.getElementById('step1').classList.remove('hidden');
        };
    </script>
</body>
</html>
