<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>AZRA'S GARDEN</title>
    <style>
        body { margin: 0; background: #000; color: #fff; font-family: sans-serif; overflow: hidden; touch-action: none; }
        #hud { position: fixed; top: 0; width: 100%; height: 60px; background: #222; display: flex; justify-content: space-around; align-items: center; z-index: 100; border-bottom: 2px solid #FFD700; }
        #game-area { position: relative; width: 100vw; height: calc(100dvh - 60px - env(safe-area-inset-bottom)); margin-top: 60px; padding-bottom: env(safe-area-inset-bottom); overflow: hidden; }
        .tile { position: absolute; width: 60px; height: 60px; border: 5px solid #FFD700; border-radius: 18px; cursor: pointer; transition: transform 0.2s; box-shadow: 4px 4px 10px rgba(0,0,0,0.5); }
        #overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); z-index: 200; display: none; justify-content: center; align-items: center; flex-direction: column; overflow: auto; }
        #lib-grid { display: grid; grid-template-columns: repeat(5, 60px); gap: 5px; padding: 20px; }
        #lib-grid img { width: 60px; height: 60px; border: 1px solid #555; cursor: pointer; }
    </style>
</head>
<body>

<div id="hud">
    <div id="iq">IQ: 100</div>
    <div id="stage">Stage: 1</div>
    <button onclick="toggleLibrary()">Library</button>
</div>

<div id="game-area"></div>
<div id="overlay"></div>

<script>
    const state = { 
        stage: parseInt(localStorage.getItem('azraStage')) || 1, 
        iq: parseInt(localStorage.getItem('azraIQ')) || 100, 
        lives: 3, tiles: [], rewardPool: [], 
        library: JSON.parse(localStorage.getItem('azraLibrary') || '[]'), 
        pairsRemaining: 0, active: true 
    };
    const gameArea = document.getElementById('game-area');

    async function initGame() {
        const img = new Image(); img.src = 'P50.png';
        const img2 = new Image(); img2.src = 'A2.png';
        await Promise.all([img.decode(), img2.decode()]);
        
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        const w = img.width / 7, h = img.height / 7;
        for(let i=0; i<49; i++) {
            canvas.width = w; canvas.height = h;
            ctx.drawImage(img, (i%7)*w, Math.floor(i/7)*h, w, h, 0, 0, w, h);
            state.tiles.push(canvas.toDataURL());
        }
        const rw = img2.width / 5, rh = img2.height / 5;
        for(let i=0; i<25; i++) {
            canvas.width = rw; canvas.height = rh;
            ctx.drawImage(img2, (i%5)*rw, Math.floor(i/5)*rh, rw, rh, 0, 0, rw, rh);
            state.rewardPool.push(canvas.toDataURL());
        }
        updateHUD();
        renderStage();
    }

    function renderStage() {
        state.active = true;
        gameArea.innerHTML = '';
        let numTiles = 30 + (2 * (state.stage - 1));
        state.pairsRemaining = numTiles / 2;
        let selection = state.tiles.slice(0, numTiles/2);
        let deck = [...selection, ...selection].sort(() => Math.random() - 0.5);

        deck.forEach((src) => {
            const el = document.createElement('div');
            el.className = 'tile';
            el.style.backgroundImage = `url(${src})`;
            el.style.left = Math.random() * (window.innerWidth - 70) + 'px';
            el.style.top = Math.random() * (window.innerHeight - 130) + 'px';
            el.style.transform = `rotate(${(Math.random()*40)-20}deg)`;
            el.onclick = () => handleTap(el, src);
            gameArea.appendChild(el);
        });
        document.getElementById('stage').innerText = `Stage: ${state.stage}`;
    }

    let selected = [];
    function handleTap(el, src) {
        if(!state.active || selected.length >= 2 || el.style.visibility === 'hidden') return;
        el.style.borderColor = '#fff';
        selected.push({el, src});
        
        if(selected.length === 2) {
            state.active = false;
            setTimeout(() => {
                if(selected[0].src === selected[1].src) {
                    selected.forEach(s => s.el.style.visibility = 'hidden');
                    state.iq += 15;
                    state.pairsRemaining--;
                    if(state.pairsRemaining === 0) completeStage();
                    else state.active = true;
                } else {
                    selected.forEach(s => s.el.style.borderColor = '#FFD700');
                    state.lives--;
                    state.iq = Math.max(50, state.iq - 5);
                    state.active = true;
                }
                selected = [];
                updateHUD();
                saveProgress();
            }, 600);
        }
    }

    function completeStage() {
        const piece = state.rewardPool[state.stage - 1];
        if (piece && !state.library.includes(piece)) {
            state.library.push(piece);
        }
        state.stage++;
        saveProgress();
        
        const overlay = document.getElementById('overlay');
        overlay.innerHTML = `<img src="${piece}" style="width:100vw; height:100vh; object-fit:fill; display:block;">`;
        overlay.style.display = 'flex';
        setTimeout(() => {
            overlay.style.display = 'none';
            renderStage();
        }, 5000);
    }

    function saveProgress() {
        localStorage.setItem('azraLibrary', JSON.stringify(state.library));
        localStorage.setItem('azraStage', state.stage);
        localStorage.setItem('azraIQ', state.iq);
    }

    function updateHUD() {
        document.getElementById('iq').innerText = `IQ: ${state.iq}`;
        if(state.lives <= 0) { alert("Game Over!"); state.lives = 3; state.iq = 100; saveProgress(); location.reload(); }
    }

    function toggleLibrary() {
        const overlay = document.getElementById('overlay');
        if (overlay.style.display === 'flex') { overlay.style.display = 'none'; return; }
        
        let html = '<h1>Library</h1><div id="lib-grid">';
        state.library.forEach(src => html += `<img src="${src}" onclick="showFull('${src}')">`);
        html += '</div><br><button onclick="toggleLibrary()">Close</button>';
        overlay.innerHTML = html;
        overlay.style.display = 'flex';
    }

    function showFull(src) {
        const overlay = document.getElementById('overlay');
        overlay.innerHTML = `<img src="${src}" style="width:100vw; height:100vh; object-fit:fill;" onclick="toggleLibrary()">`;
    }

    initGame();
</script>
</body>
</html>
