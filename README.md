# Card
Card lovers Interact

```html
<!doctype html>
<html lang="pt-BR"><head><script src="/_sdk/telemetry_sdk.js"></script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bom Dia</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&amp;display=swap" rel="stylesheet">
  <style>
        body { font-family: 'DM Sans', sans-serif; }
        #game-over { display: none; }
        #game-over.active { display: flex; }
        #victory { display: none; }
        #victory.active { display: flex; }
    </style>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js" type="text/javascript"></script>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/resizing_sdk.js" type="text/javascript"></script>
 </head>
 <body data-template-id="__page-root" class="min-h-screen flex flex-col items-center justify-center gap-6 relative overflow-hidden" style="background: linear-gradient(rgb(123, 45, 159), rgb(253, 216, 46));">
  <h1 data-template-id="page-title" class="canva-text text-center font-bold" style="color: rgb(26, 26, 46); font-weight: 700; font-style: normal; font-size: 28px;">Quer me dar bom dia? 🌞</h1>
  <div class="flex gap-4 flex-wrap justify-center relative">
   <button data-template-id="btn-bomdia" class="canva-button px-6 py-3 rounded-xl font-bold text-lg shadow-lg hover:scale-105 transition-transform" onclick="showVictory()" style="background: rgb(245, 158, 11); color: rgb(255, 255, 255); font-weight: 400; font-style: normal; font-size: 16px;">Bom Dia! ☀️</button> <button id="sim-btn" data-template-id="btn-sim" class="canva-button px-6 py-3 rounded-xl font-bold text-lg shadow-lg hover:scale-105 transition-transform" onclick="evadeSim()" style="background: rgb(16, 185, 129); color: rgb(255, 255, 255); font-weight: 400; font-style: normal; font-size: 16px;">Sim 😏</button> <button data-template-id="btn-nao" class="canva-button px-6 py-3 rounded-xl font-bold text-lg shadow-lg hover:scale-105 transition-transform" onclick="showGameOver()" style="background: rgb(239, 68, 68); color: rgb(255, 255, 255); font-weight: 400; font-style: normal; font-size: 16px;">Não 😐</button>
  </div>
  <div id="game-over" class="fixed inset-0 z-50 flex-col items-center justify-center bg-black/90">
   <p data-template-id="gameover-text" class="canva-text text-4xl md:text-6xl text-center font-bold mb-8" style="color: rgb(255, 255, 255); font-weight: 700; font-style: normal; font-size: 16px;">ah, ok então😡😒</p><button data-template-id="btn-voltar" class="canva-button px-6 py-3 rounded-xl font-bold" onclick="hideGameOver()" style="background: rgb(99, 102, 241); color: rgb(255, 255, 255); font-weight: 400; font-style: normal; font-size: 16px;">Voltar</button>
  </div>
  <div id="victory" class="fixed inset-0 z-50 flex flex-col items-center justify-center bg-gradient-to-b from-pink-200 to-red-200">
   <img data-template-id="corner-top-left" class="canva-image absolute top-2 left-2 w-32 h-32 md:w-48 md:h-48 object-cover" loading="lazy" src="canva://MAHNwoSNFMY/1" alt="Bart Simpson cake meme"> <img data-template-id="corner-top-right" class="canva-image absolute top-2 right-2 w-32 h-32 md:w-48 md:h-48 object-cover" loading="lazy" src="canva://MAHNwoBnFN4/1" alt="Cockroach meme face"> <img data-template-id="corner-bottom-left" class="canva-image absolute bottom-2 left-2 w-32 h-32 md:w-48 md:h-48 object-cover" loading="lazy" src="canva://MAHNwkw5YCk/1" alt="Holy Moly emoji surprised"> <img data-template-id="corner-bottom-right" class="canva-image absolute bottom-2 right-2 w-32 h-32 md:w-48 md:h-48 object-cover" loading="lazy" src="canva://MAHNwnEJ86I/1" alt="Green car meme">
   <p class="text-6xl mb-4">❤️</p>
   <p data-template-id="victory-text" class="canva-text text-4xl md:text-6xl text-center font-bold mb-8" style="color: rgb(220, 38, 38); font-weight: 700; font-style: normal; font-size: 16px;">IHUU levei um bom dia, que seu dia seja muito feliz
E feliz aniversário (não tenho certeza se e desculpa 👉👈)</p>
   <div class="flex gap-2 text-5xl animate-bounce"><span>❤️</span> <span style="animation-delay: 0.2s">❤️</span> <span style="animation-delay: 0.4s">❤️</span>
   </div><button data-template-id="btn-voltar-vitoria" class="canva-button px-6 py-3 rounded-xl font-bold mt-8" onclick="hideVictory()" style="background: rgb(236, 72, 153); color: rgb(255, 255, 255); font-weight: 400; font-style: normal; font-size: 16px;">Voltar</button>
  </div>
  <script src="/_sdk/editing_sdk.js"></script>
  <script>
        const simBtn = document.getElementById('sim-btn');
        let isEvading = false;

        function evadeSim() {
            isEvading = true;
            moveBtn();
            
            // Stop evading after 2 seconds
            setTimeout(() => {
                isEvading = false;
                simBtn.style.position = 'static';
            }, 2000);
        }

        function moveBtn() {
            const maxX = window.innerWidth - simBtn.offsetWidth - 20;
            const maxY = window.innerHeight - simBtn.offsetHeight - 20;
            
            simBtn.style.position = 'fixed';
            simBtn.style.left = Math.max(10, Math.random() * maxX) + 'px';
            simBtn.style.top = Math.max(10, Math.random() * maxY) + 'px';
            
            if (isEvading) {
                setTimeout(moveBtn, 150);
            }
        }

        function hideVictory() {
            document.getElementById('victory').classList.remove('active');
        }

        function showVictory() {
            document.getElementById('victory').classList.add('active');
        }

        function showGameOver() {
            document.getElementById('game-over').classList.add('active');
        }
        function hideGameOver() {
            document.getElementById('game-over').classList.remove('active');
        }
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'a123ec7fc49ccb34',t:'MTc4MjU1Nzc3Mi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
</body></html>
```
