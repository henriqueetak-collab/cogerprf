from pathlib import Path

root = Path("/mnt/data/coger_prf")
root.mkdir(exist_ok=True)

html = r'''<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>COGER • PRF | Canal de Denúncias</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header class="topbar">
    <div class="container nav">
      <a class="brand" href="#inicio">
        <span class="brand-mark">PRF</span>
        <span><strong>COGER</strong><small>Canal de Denúncias</small></span>
      </a>
      <button class="menu" aria-label="Abrir menu">☰</button>
      <nav>
        <a href="#inicio">Início</a>
        <a href="#denuncia">Registrar denúncia</a>
        <a href="#consulta">Consultar protocolo</a>
        <a href="#orientacoes">Orientações</a>
      </nav>
    </div>
  </header>

  <main id="inicio">
    <section class="hero">
      <div class="container hero-grid">
        <div>
          <div class="eyebrow">CORREGEDORIA • PRF</div>
          <h1>Canal de denúncias</h1>
          <p class="hero-text">Registre, de forma clara e segura, denúncias relacionadas à conduta de integrantes da PRF dentro do ambiente do servidor.</p>
          <div class="hero-actions">
            <a class="btn primary" href="#denuncia">Registrar denúncia <span>→</span></a>
            <a class="btn ghost" href="#consulta">Consultar protocolo</a>
          </div>
          <div class="notice"><span>●</span> Este portal é destinado exclusivamente ao ambiente virtual/FiveM e não representa um canal oficial da Polícia Rodoviária Federal.</div>
        </div>
        <div class="hero-card">
          <div class="shield">⚖</div>
          <h3>Tratamento responsável</h3>
          <p>As informações devem ser apresentadas com objetividade. Evidências podem auxiliar na apuração do fato.</p>
          <div class="mini-stats">
            <div><b>01</b><span>Protocolo individual</span></div>
            <div><b>02</b><span>Análise administrativa</span></div>
            <div><b>03</b><span>Acompanhamento</span></div>
          </div>
        </div>
      </div>
    </section>

    <section class="section" id="como">
      <div class="container">
        <div class="section-heading">
          <div><span class="eyebrow">COMO FUNCIONA</span><h2>Da denúncia à apuração</h2></div>
          <p>O sistema foi pensado para organizar o recebimento e o acompanhamento de ocorrências administrativas.</p>
        </div>
        <div class="steps">
          <article><span>01</span><h3>Registro</h3><p>Preencha o formulário com os dados disponíveis e descreva os fatos.</p></article>
          <article><span>02</span><h3>Protocolo</h3><p>Um número de protocolo é gerado para identificar a manifestação.</p></article>
          <article><span>03</span><h3>Análise</h3><p>A Corregedoria avalia as informações e as evidências apresentadas.</p></article>
          <article><span>04</span><h3>Conclusão</h3><p>O registro recebe uma situação final conforme a apuração administrativa.</p></article>
        </div>
      </div>
    </section>

    <section class="section light" id="denuncia">
      <div class="container form-layout">
        <div class="side-copy">
          <span class="eyebrow">NOVA MANIFESTAÇÃO</span>
          <h2>Registrar denúncia</h2>
          <p>Forneça somente informações relacionadas ao fato. Quanto mais objetiva for a descrição, mais fácil será compreender a ocorrência.</p>
          <div class="info-box"><strong>Denúncia anônima</strong><p>Você pode optar por não informar seu nome. Ainda assim, recomenda-se fornecer detalhes suficientes para análise.</p></div>
          <div class="info-box warning"><strong>Importante</strong><p>Não utilize o canal para emergências. Em situações que exijam ação imediata dentro do servidor, procure a autoridade responsável pelo atendimento operacional.</p></div>
        </div>

        <form id="complaintForm" class="card">
          <div class="form-title"><div><span>FORMULÁRIO</span><h3>Dados da manifestação</h3></div><span class="required">* obrigatório</span></div>

          <label class="checkline"><input type="checkbox" id="anonymous"> Desejo realizar uma denúncia anônima</label>

          <div class="fields two">
            <label>Nome do denunciante <span>*</span><input id="name" type="text" placeholder="Nome completo"></label>
            <label>Discord / ID <small>(opcional)</small><input id="discord" type="text" placeholder="Ex.: usuario#0000 / ID"></label>
          </div>

          <hr>

          <div class="fields two">
            <label>PRF denunciado <span>*</span><input id="officer" type="text" placeholder="Nome ou identificação"></label>
            <label>Classe / função <small>(se souber)</small><input id="class" type="text" placeholder="Ex.: Classe II"></label>
          </div>

          <div class="fields three">
            <label>Data <span>*</span><input id="date" type="date"></label>
            <label>Horário <span>*</span><input id="time" type="time"></label>
            <label>Local <span>*</span><input id="place" type="text" placeholder="Rodovia / região"></label>
          </div>

          <label>Tipo de ocorrência <span>*</span>
            <select id="category">
              <option value="">Selecione uma categoria</option>
              <option>Abuso de autoridade / conduta inadequada</option>
              <option>Uso indevido de viatura</option>
              <option>Conduta operacional</option>
              <option>Descumprimento de procedimento</option>
              <option>Uso indevido de equipamento</option>
              <option>Abordagem irregular</option>
              <option>Assédio / desrespeito</option>
              <option>Outra ocorrência administrativa</option>
            </select>
          </label>

          <label>Descrição dos fatos <span>*</span><textarea id="description" rows="7" maxlength="2000" placeholder="Descreva o que aconteceu, em ordem cronológica, incluindo nomes, local e circunstâncias relevantes."></textarea><small class="counter"><b id="count">0</b>/2000</small></label>

          <label>Evidência / link <small>(opcional)</small><input id="evidence" type="url" placeholder="https://..."></label>

          <label class="checkline"><input id="truth" type="checkbox"> Declaro que as informações fornecidas correspondem ao meu conhecimento dos fatos.</label>
          <button class="btn primary full" type="submit">Enviar denúncia <span>→</span></button>
          <p class="fine">Ao enviar, os dados são processados pelo protótipo local deste site. Para produção, conecte este formulário a um banco de dados/backend seguro.</p>
        </form>
      </div>
    </section>

    <section class="section" id="consulta">
      <div class="container narrow">
        <div class="section-heading centered"><span class="eyebrow">ACOMPANHAMENTO</span><h2>Consultar protocolo</h2><p>Informe o protocolo gerado após o envio de uma manifestação.</p></div>
        <div class="lookup card">
          <div class="lookup-row"><input id="protocolInput" placeholder="Ex.: COGER-2026-00001"><button class="btn primary" id="lookupBtn">Consultar</button></div>
          <div id="lookupResult"></div>
        </div>
      </div>
    </section>

    <section class="section light" id="orientacoes">
      <div class="container">
        <div class="section-heading"><div><span class="eyebrow">ORIENTAÇÕES</span><h2>Antes de registrar</h2></div></div>
        <div class="faq-grid">
          <article><h3>Seja objetivo</h3><p>Informe o que ocorreu, quando ocorreu e quem estava envolvido. Evite suposições sobre fatos que você não presenciou.</p></article>
          <article><h3>Apresente evidências</h3><p>Quando disponíveis, links ou registros relacionados à ocorrência podem facilitar a análise.</p></article>
          <article><h3>Evite denúncias de má-fé</h3><p>O canal deve ser utilizado para manifestações legítimas. Registros deliberadamente falsos podem ser avaliados administrativamente.</p></article>
          <article><h3>Guarde seu protocolo</h3><p>O número gerado permite consultar a situação do registro neste protótipo.</p></article>
        </div>
      </div>
    </section>

    <section class="cta">
      <div class="container cta-inner"><div><span class="eyebrow">COGER • PRF</span><h2>Canal destinado à integridade e à responsabilização administrativa.</h2></div><a class="btn white" href="#denuncia">Fazer uma denúncia →</a></div>
    </section>
  </main>

  <footer>
    <div class="container footer-grid">
      <div><div class="brand footer-brand"><span class="brand-mark">PRF</span><span><strong>COGER</strong><small>Canal de Denúncias</small></span></div><p>Portal administrativo desenvolvido para uso em ambiente virtual/FiveM.</p></div>
      <div><strong>Acesso rápido</strong><a href="#denuncia">Registrar denúncia</a><a href="#consulta">Consultar protocolo</a><a href="#orientacoes">Orientações</a></div>
      <div><strong>Informações</strong><span>Uso exclusivo do servidor</span><span>Não é um site oficial do Governo Federal</span></div>
    </div>
    <div class="copyright">© 2026 COGER • PRF — Projeto para ambiente virtual/FiveM.</div>
  </footer>

  <div id="modal" class="modal"><div class="modal-box"><button id="closeModal" class="close">×</button><div class="success-icon">✓</div><span class="eyebrow">DENÚNCIA REGISTRADA</span><h2>Protocolo gerado</h2><p>Guarde este número para consultar o andamento.</p><div class="protocol" id="protocol"></div><button id="copyProtocol" class="btn primary full">Copiar protocolo</button><a href="#consulta" id="goLookup" class="btn ghost full">Ir para consulta</a></div></div>
  <script src="script.js"></script>
</body>
</html>'''

css = r''':root{--navy:#071827;--navy2:#0d263b;--blue:#0b5fa5;--blue2:#0876c9;--gold:#d8a83e;--bg:#f5f7fa;--line:#dce3e9;--text:#17232e;--muted:#667482;--white:#fff;--shadow:0 18px 45px rgba(7,24,39,.10)}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;font-family:Inter,Segoe UI,Arial,sans-serif;color:var(--text);background:var(--white);line-height:1.55}a{text-decoration:none;color:inherit}.container{width:min(1160px,calc(100% - 40px));margin:auto}
.topbar{position:sticky;top:0;z-index:20;background:rgba(7,24,39,.97);color:#fff;border-bottom:1px solid rgba(255,255,255,.08)}.nav{height:76px;display:flex;align-items:center;justify-content:space-between}.brand{display:flex;align-items:center;gap:11px}.brand-mark{width:43px;height:43px;border:2px solid var(--gold);display:grid;place-items:center;font-weight:900;font-size:12px;letter-spacing:.5px;transform:skew(-5deg)}.brand strong{display:block;font-size:17px;letter-spacing:1px}.brand small{display:block;color:#aab8c5;font-size:10px;text-transform:uppercase;letter-spacing:1.4px}nav{display:flex;gap:26px;font-size:13px;color:#cdd8e1}nav a:hover{color:#fff}.menu{display:none;background:none;border:0;color:white;font-size:25px}
.hero{background:linear-gradient(135deg,var(--navy),#0c2b44);color:#fff;padding:90px 0 84px;position:relative;overflow:hidden}.hero:after{content:"";position:absolute;width:520px;height:520px;border:1px solid rgba(216,168,62,.18);border-radius:50%;right:-180px;top:-200px}.hero-grid{display:grid;grid-template-columns:1.3fr .7fr;gap:70px;align-items:center}.eyebrow{font-size:11px;letter-spacing:2px;font-weight:800;color:var(--gold)}h1{font-size:58px;line-height:1.04;margin:13px 0 20px;letter-spacing:-2px}h2{font-size:34px;line-height:1.15;margin:8px 0 14px;letter-spacing:-.8px}h3{margin:7px 0 8px;font-size:18px}.hero-text{font-size:18px;max-width:650px;color:#c9d5df}.hero-actions{display:flex;gap:12px;margin:28px 0}.btn{display:inline-flex;justify-content:center;align-items:center;gap:13px;border:0;border-radius:4px;padding:13px 20px;font-weight:750;font-size:13px;cursor:pointer;transition:.2s}.btn.primary{background:var(--blue2);color:#fff}.btn.primary:hover{background:#0965aa;transform:translateY(-1px)}.btn.ghost{border:1px solid #aebdca;color:var(--text);background:#fff}.hero .btn.ghost{background:transparent;color:#fff;border-color:#597082}.btn.white{background:#fff;color:var(--navy)}.full{width:100%}.notice{font-size:12px;color:#9fb0bd;max-width:680px}.notice span{color:var(--gold);margin-right:7px}.hero-card{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.13);padding:31px;border-radius:7px;backdrop-filter:blur(8px)}.shield{width:54px;height:62px;display:grid;place-items:center;border:1px solid var(--gold);color:var(--gold);font-size:25px;clip-path:polygon(50% 0,90% 13%,86% 67%,50% 100%,14% 67%,10% 13%)}.hero-card p{color:#b6c5d0;font-size:14px}.mini-stats{border-top:1px solid rgba(255,255,255,.1);margin-top:22px;padding-top:17px;display:grid;gap:13px}.mini-stats div{display:flex;gap:12px;align-items:center}.mini-stats b{color:var(--gold);font-size:12px}.mini-stats span{font-size:12px;color:#c4d0d8}
.section{padding:82px 0}.light{background:var(--bg)}.section-heading{display:flex;justify-content:space-between;gap:40px;align-items:end;margin-bottom:35px}.section-heading>p{max-width:470px;color:var(--muted);margin:0}.centered{display:block;text-align:center}.centered p{margin:0 auto;max-width:600px}.steps{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--line);border:1px solid var(--line)}.steps article{background:#fff;padding:28px}.steps span{color:var(--blue);font-weight:900;font-size:12px}.steps p,.faq-grid p{color:var(--muted);font-size:14px;margin:0}
.form-layout{display:grid;grid-template-columns:.75fr 1.25fr;gap:60px;align-items:start}.side-copy{padding-top:10px}.side-copy>p{color:var(--muted);font-size:15px}.info-box{border-left:3px solid var(--blue);padding:15px 17px;background:#fff;margin-top:18px;box-shadow:0 5px 20px rgba(0,0,0,.04)}.info-box p{font-size:13px;color:var(--muted);margin:4px 0 0}.info-box.warning{border-left-color:var(--gold)}.card{background:#fff;border:1px solid var(--line);border-radius:7px;padding:28px;box-shadow:var(--shadow)}.form-title{display:flex;justify-content:space-between;align-items:end;border-bottom:1px solid var(--line);padding-bottom:17px;margin-bottom:20px}.form-title span:first-child{font-size:10px;color:var(--blue);font-weight:900;letter-spacing:1.5px}.form-title h3{font-size:23px;margin:2px 0 0}.required{font-size:10px!important;color:var(--muted)!important}.fields{display:grid;gap:15px;margin:15px 0}.two{grid-template-columns:1fr 1fr}.three{grid-template-columns:.65fr .65fr 1.7fr}label{display:block;font-size:12px;font-weight:750;color:#364652;margin-bottom:15px}label>span{color:#bd3e3e}label small{font-weight:500;color:#87939c}input,select,textarea{display:block;width:100%;border:1px solid #cfd8df;background:#fff;border-radius:4px;margin-top:7px;padding:12px 13px;font:inherit;font-size:13px;color:var(--text);outline:none}textarea{resize:vertical;min-height:150px}input:focus,select:focus,textarea:focus{border-color:var(--blue);box-shadow:0 0 0 3px rgba(11,95,165,.08)}hr{border:0;border-top:1px solid var(--line);margin:23px 0}.checkline{display:flex;align-items:center;gap:9px;font-weight:600;margin:0 0 20px}.checkline input{width:auto;margin:0}.counter{display:block;text-align:right;color:#8996a0;font-weight:500;font-size:10px;margin-top:-10px}.fine{font-size:10px;color:#8a959e;text-align:center;margin:12px 0 0}
.narrow{max-width:780px}.lookup{margin:auto}.lookup-row{display:flex;gap:10px}.lookup-row input{margin:0}.lookup-row .btn{min-width:130px}.lookup-result{margin-top:18px}.result{border:1px solid var(--line);padding:18px;background:#f8fafb}.status{display:inline-block;background:#eaf3fb;color:var(--blue);font-size:10px;font-weight:900;text-transform:uppercase;padding:5px 9px;border-radius:20px}.result-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:14px}.result-grid div{font-size:12px}.result-grid b{display:block;font-size:10px;color:#84909a;text-transform:uppercase;letter-spacing:.8px}.faq-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px}.faq-grid article{background:#fff;border:1px solid var(--line);padding:24px}.cta{background:var(--blue);color:#fff;padding:48px 0}.cta-inner{display:flex;align-items:center;justify-content:space-between;gap:30px}.cta h2{max-width:700px;margin:6px 0 0}
footer{background:var(--navy);color:#d6e0e7;padding-top:48px}.footer-grid{display:grid;grid-template-columns:1.5fr 1fr 1fr;gap:50px;padding-bottom:42px}.footer-grid p,.footer-grid span,.footer-grid a{display:block;color:#91a2af;font-size:12px;margin-top:8px}.footer-grid a:hover{color:#fff}.footer-brand{margin-bottom:13px}.copyright{border-top:1px solid rgba(255,255,255,.08);text-align:center;padding:17px;font-size:10px;color:#718492}
.modal{display:none;position:fixed;inset:0;background:rgba(2,10,17,.72);z-index:50;align-items:center;justify-content:center;padding:20px}.modal.open{display:flex}.modal-box{width:min(430px,100%);background:#fff;border-radius:8px;padding:35px;text-align:center;position:relative;box-shadow:0 30px 80px rgba(0,0,0,.3)}.close{position:absolute;right:14px;top:10px;border:0;background:none;font-size:28px;color:#77838c;cursor:pointer}.success-icon{width:54px;height:54px;border-radius:50%;display:grid;place-items:center;background:#e8f5ee;color:#16834b;font-size:26px;font-weight:900;margin:0 auto 18px}.protocol{font-size:22px;font-weight:900;letter-spacing:1px;background:#f0f4f7;padding:14px;margin:20px 0}.modal-box .ghost{margin-top:9px}
@media(max-width:850px){nav{display:none}.menu{display:block}.hero-grid,.form-layout{grid-template-columns:1fr}.hero{padding:65px 0}.hero-card{display:none}h1{font-size:45px}.steps,.faq-grid{grid-template-columns:1fr 1fr}.section-heading{display:block}.section-heading>p{margin-top:12px}.form-layout{gap:35px}.footer-grid{grid-template-columns:1fr 1fr}}
@media(max-width:560px){.container{width:min(100% - 26px,1160px)}.hero-actions{flex-direction:column}.btn{width:100%}.steps,.faq-grid,.two,.three,.result-grid{grid-template-columns:1fr}.card{padding:20px}.lookup-row{flex-direction:column}.lookup-row .btn{width:100%}.cta-inner{display:block}.cta .btn{margin-top:20px}.footer-grid{grid-template-columns:1fr}h1{font-size:38px}}
'''

js = r'''const $ = (id) => document.getElementById(id);

const anonymous = $("anonymous");
const nameInput = $("name");
anonymous.addEventListener("change", () => {
  nameInput.disabled = anonymous.checked;
  nameInput.required = !anonymous.checked;
  nameInput.placeholder = anonymous.checked ? "Não informado (anônimo)" : "Nome completo";
  if (anonymous.checked) nameInput.value = "";
});

const desc = $("description");
desc.addEventListener("input", () => $("count").textContent = desc.value.length);

function getRecords(){
  try { return JSON.parse(localStorage.getItem("coger_records") || "{}"); }
  catch { return {}; }
}
function saveRecords(records){ localStorage.setItem("coger_records", JSON.stringify(records)); }

function newProtocol(){
  const year = new Date().getFullYear();
  const records = getRecords();
  const n = Object.keys(records).length + 1;
  return `COGER-${year}-${String(n).padStart(5,"0")}`;
}

$("complaintForm").addEventListener("submit", (e) => {
  e.preventDefault();
  if (!anonymous.checked && !nameInput.value.trim()) return alert("Informe o nome ou selecione a opção de denúncia anônima.");
  if (!$("officer").value.trim() || !$("date").value || !$("time").value || !$("place").value.trim() || !$("category").value || !desc.value.trim() || !$("truth").checked) {
    return alert("Preencha os campos obrigatórios e confirme a declaração.");
  }
  const protocol = newProtocol();
  const records = getRecords();
  records[protocol] = {
    protocol,
    name: anonymous.checked ? "Denúncia anônima" : nameInput.value.trim(),
    discord: $("discord").value.trim() || "Não informado",
    officer: $("officer").value.trim(),
    className: $("class").value.trim() || "Não informado",
    date: $("date").value,
    time: $("time").value,
    place: $("place").value.trim(),
    category: $("category").value,
    description: desc.value.trim(),
    evidence: $("evidence").value.trim() || "Não informado",
    status: "Recebida",
    created: new Date().toISOString()
  };
  saveRecords(records);
  $("protocol").textContent = protocol;
  $("modal").classList.add("open");
  e.target.reset();
  $("count").textContent = "0";
  nameInput.disabled = false;
  nameInput.required = true;
});

$("copyProtocol").addEventListener("click", async () => {
  try { await navigator.clipboard.writeText($("protocol").textContent); $("copyProtocol").textContent = "Protocolo copiado ✓"; }
  catch { alert("Copie o protocolo manualmente: " + $("protocol").textContent); }
});

$("closeModal").addEventListener("click", () => $("modal").classList.remove("open"));
$("goLookup").addEventListener("click", () => $("modal").classList.remove("open"));
$("modal").addEventListener("click", e => { if(e.target === $("modal")) $("modal").classList.remove("open"); });

$("lookupBtn").addEventListener("click", () => {
  const key = $("protocolInput").value.trim().toUpperCase();
  const record = getRecords()[key];
  const box = $("lookupResult");
  if (!record) {
    box.innerHTML = '<div class="result"><strong>Protocolo não localizado.</strong><p style="color:#667482;margin-bottom:0">Confira o número informado e tente novamente.</p></div>';
    return;
  }
  const d = new Date(record.created);
  box.innerHTML = `<div class="result">
    <span class="status">${record.status}</span>
    <h3>${record.protocol}</h3>
    <div class="result-grid">
      <div><b>Denunciado</b>${escapeHtml(record.officer)}</div>
      <div><b>Categoria</b>${escapeHtml(record.category)}</div>
      <div><b>Local</b>${escapeHtml(record.place)}</div>
      <div><b>Registro</b>${d.toLocaleDateString("pt-BR")} às ${d.toLocaleTimeString("pt-BR",{hour:"2-digit",minute:"2-digit"})}</div>
    </div>
  </div>`;
});

function escapeHtml(s){
  return String(s).replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;'}[m]));
}

document.querySelector(".menu").addEventListener("click", () => {
  const nav = document.querySelector("nav");
  const open = nav.style.display === "flex";
  nav.style.display = open ? "" : "flex";
  if(!open){ nav.style.position="absolute"; nav.style.top="76px"; nav.style.left="0"; nav.style.right="0"; nav.style.background="#071827"; nav.style.padding="18px 20px"; nav.style.flexDirection="column"; }
});
'''

(root/"index.html").write_text(html, encoding="utf-8")
(root/"style.css").write_text(css, encoding="utf-8")
(root/"script.js").write_text(js, encoding="utf-8")

# zip for easy hosting
import zipfile
zip_path = Path("/mnt/data/COGER_PRF_site.zip")
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for p in root.iterdir():
        z.write(p, p.name)

print(f"Arquivos criados em {root}")
print(f"ZIP: {zip_path}")
