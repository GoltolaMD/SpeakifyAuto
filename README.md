# 🗣️ Speakify Auto — Automatizador de Lições

Bookmarklet para acelerar e automatizar o processo de resolução das lições na plataforma **Speakify**.

Este script cria uma **interface flutuante elegante e interativa**, onde você pode escolher o **nível de 1 a 16** para concluir todas as lições automaticamente com poucos cliques.

---

## ⚙️ Funcionalidades

- UI fixa com botão de **fechar**.
- Grade de botões para iniciar do **Level 1 ao 16**.
- Clica automaticamente nas lições e nas opções de concluir todas.
- Feedback visual com alertas por nível.
- Estilo moderno em **roxo/violeta**.

---

## 🚀 Como usar

---

### 🔸 1. Copie o código abaixo e crie um favorito manualmente:

````javascript
javascript:(function(){if(document.getElementById('speakifyAutoUI'))return;const UI=document.createElement('div');UI.id='speakifyAutoUI';UI.style.position='fixed';UI.style.top='20px';UI.style.left='20px';UI.style.zIndex='999999';UI.style.background='#111';UI.style.padding='15px';UI.style.border='2px solid #a855f7';UI.style.borderRadius='12px';UI.style.color='#fff';UI.style.fontFamily='Arial, sans-serif';UI.style.maxWidth='300px';UI.style.boxShadow='0 0 10px #a855f7';const title=document.createElement('div');title.textContent='Speakify Auto';title.style.fontSize='18px';title.style.marginBottom='10px';title.style.textAlign='center';title.style.color='#c084fc';UI.appendChild(title);const grid=document.createElement('div');grid.style.display='grid';grid.style.gridTemplateColumns='repeat(4, 1fr)';grid.style.gap='5px';for(let i=1;i<=16;i++){const btn=document.createElement('button');btn.innerText=i;btn.style.background='#9333ea';btn.style.border='none';btn.style.color='#fff';btn.style.borderRadius='6px';btn.style.padding='6px';btn.style.cursor='pointer';btn.title='Level '+i;btn.onclick=async()=>{alert(`Iniciando Level ${i}...`);const levelBtn=Array.from(document.querySelectorAll('button')).find(b=>b.innerText.includes(`Level ${i}`));if(!levelBtn)return alert('Level não encontrado!');levelBtn.click();await new Promise(r=>setTimeout(r,1500));for(let r=0;r<6;r++){const concluir=[...document.querySelectorAll('button')].find(b=>b.innerText.toLowerCase().includes('concluir todas as lições'));if(concluir){concluir.click();await new Promise(r=>setTimeout(r,600));concluir.click();await new Promise(r=>setTimeout(r,1000));}const licoes=[...document.querySelectorAll('button')].filter(b=>b.innerText.toLowerCase().includes('lição'));for(const li of licoes){li.click();await new Promise(r=>setTimeout(r,1500));const again=[...document.querySelectorAll('button')].find(b=>b.innerText.toLowerCase().includes('concluir todas as lições'));if(again){again.click();await new Promise(r=>setTimeout(r,600));again.click();await new Promise(r=>setTimeout(r,800));}history.back();await new Promise(r=>setTimeout(r,1500));}}alert(`Level ${i} finalizado! Todas as lições concluídas.`);};grid.appendChild(btn);}UI.appendChild(grid);const fechar=document.createElement('button');fechar.innerText='Fechar';fechar.style.marginTop='10px';fechar.style.width='100%';fechar.style.background='#ef4444';fechar.style.color='#fff';fechar.style.border='none';fechar.style.padding='8px';fechar.style.borderRadius='6px';fechar.style.cursor='pointer';fechar.onclick=()=>UI.remove();UI.appendChild(fechar);document.body.appendChild(UI);})();
