<!DOCTYPE html>
<html lang="id"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Koding dan Kecerdasan Artifisial: Misi Teknisi AI</title>
<style>
html,body{margin:0;height:100%;background:#1e1b4b;font-family:system-ui,Arial,sans-serif}
body{display:flex;align-items:center;justify-content:center}
#st{width:min(100vw,177.78vh);aspect-ratio:16/9;container-type:inline-size;background:#eef2ff;color:#0f172a;overflow:hidden}
#A{height:100%;display:flex;flex-direction:column;font-size:2cqw}
.top{background:#3730a3;color:#fff;padding:.5em 1em;display:flex;justify-content:space-between;align-items:center;gap:1em;font-weight:600}
.mn{flex:1;overflow:auto;padding:.8em 1.4em}
.nv{padding:.5em 1em;display:flex;justify-content:space-between;gap:1em;border-top:2px solid #c7d2fe;background:#fff}
h1{font-size:2.2em;margin:.2em 0}h2{font-size:1.4em;margin:.2em 0}p{margin:.4em 0;line-height:1.4}
.b{font:inherit;min-height:2.4em;padding:.35em 1em;border-radius:.6em;border:2px solid #3730a3;background:#fff;color:#1e1b4b;cursor:pointer}
.b:disabled{opacity:.55;cursor:default}.p{background:#3730a3;color:#fff}
.g{display:grid;grid-template-columns:1fr 1fr;gap:.6em}.g .b{text-align:left}
.ok{background:#bbf7d0!important;border-color:#15803d!important;color:#052e16!important}
.no{background:#fecaca!important;border-color:#b91c1c!important;color:#450a0a!important}
.sel{background:#fde68a!important;border-color:#b45309!important;color:#451a03!important}
.fb{margin-top:.5em;padding:.4em .8em;border-radius:.6em;font-weight:600;min-height:1.4em;background:#e0e7ff}
pre{background:#0f172a;color:#f8fafc;padding:.6em 1em;border-radius:.6em;font-size:1.1em;margin:.4em 0;overflow:auto}
.c{text-align:center}.card{background:#fff;border:2px solid #c7d2fe;border-radius:.8em;padding:.6em .8em}
.mp{display:grid;grid-template-columns:repeat(5,1fr);gap:.6em;margin-top:.6em}
.mp .b{text-align:center;padding:.6em .3em;font-size:.95em}.ic{font-size:2em;display:block}
.pl{margin:.3em 0;padding:.4em .8em;border-radius:.5em;background:#e0e7ff}
</style></head><body><div id="st"><div id="A"></div></div>
<script>
const E=s=>String(s).replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;");
const sh=a=>[...a].sort(()=>Math.random()-.5);
const S={sc:0,dn:[0,0,0,0,0],st:[0,0,0,0,0],mute:false};
let cur=0,lives=3,M={},ac;
const A=document.getElementById("A");
const LV=[
{n:"Kenali Istilah",ic:"🧩",t:"match",tj:"Mencocokkan istilah KKA dengan artinya",x:"Pelanggan helpdesk bertanya tentang istilah teknologi. Pasangkan istilah dan artinya agar kamu bisa menjelaskannya.",
d:[["Kecerdasan Artifisial","Mesin yang meniru cara manusia berpikir"],["Algoritma","Langkah terurut untuk menyelesaikan masalah"],["Variabel","Wadah data yang diberi nama"],["Machine Learning","Komputer belajar pola dari data"]]},
{n:"Susun Algoritma",ic:"🔢",t:"order",tj:"Mengurutkan langkah algoritma",x:"Atasan memintamu menyusun alur login aplikasi sekolah. Pilih langkah dari yang pertama sampai terakhir.",
d:["Buka aplikasi","Masukkan username dan password","Sistem memeriksa data","Jika cocok, beranda tampil"]},
{n:"Lengkapi Kode",ic:"💻",t:"fill",tj:"Melengkapi kode Python (perulangan, percabangan, output)",x:"Kamu memprogram sensor suhu ruang server. Isi bagian kode yang kosong satu per satu.",
c:['for i in range({0}):','    print("Cek sensor")','suhu = 35','if suhu {1} 30:','    {2}("Kipas nyala")'],
b:[{o:["2","3","10"],a:"3",h:"Cek sensor harus diulang 3 kali."},{o:[">","<","="],a:">",h:"Kipas menyala jika suhu lebih dari 30."},{o:["print","input","def"],a:"print",h:"print menampilkan teks ke layar."}]},
{n:"Latih Mesin",ic:"🤖",t:"sort",tj:"Memberi label data untuk melatih machine learning",x:"Kamu melatih filter spam. Beri label tiap pesan: Aman atau Spam. Label yang benar membuat mesin pintar.",
d:[["Menangkan HP gratis, klik link sekarang!",1,"Hadiah palsu dan link mencurigakan adalah ciri spam."],["Jadwal ujian praktik dimajukan besok pagi.",0,"Informasi sekolah yang jelas termasuk pesan aman."],["Kirim kode OTP kamu untuk klaim hadiah.",1,"OTP tidak boleh dibagikan. Ini penipuan."],["Tugas koding dikumpulkan hari Jumat.",0,"Pesan tugas dari guru adalah pesan aman."],["Pinjaman cepat tanpa syarat, isi password di sini.",1,"Meminta password adalah ciri phishing."]]},
{n:"Bijak Memakai AI",ic:"⚖️",t:"dec",tj:"Mengambil keputusan etis saat memakai AI",x:"Sebagai teknisi, kamu sering memakai AI. Pilih tindakan paling tepat di tiap situasi.",
d:[["AI memberi jawaban yang terdengar meyakinkan, tetapi kamu ragu.",[["Langsung dikirim ke klien",0,"Jawaban AI bisa salah (halusinasi). Selalu verifikasi."],["Cek ke sumber tepercaya dulu",1,"Tepat! Verifikasi menjaga kualitas kerja."]]],
["Klien memberi data pelanggan lengkap untuk diolah AI.",[["Hapus identitas pribadi sebelum dimasukkan",1,"Tepat! Data pribadi wajib dilindungi (UU PDP)."],["Masukkan semuanya ke chatbot",0,"Data pribadi tidak boleh dibagikan sembarangan."]]],
["Tugas laporan dikerjakan AI sepenuhnya.",[["Kumpulkan tanpa mengubah dan mengaku buatan sendiri",0,"Itu melanggar integritas akademik."],["Pakai sebagai draf, pahami, lalu tulis dengan kata sendiri dan sebutkan bantuan AI",1,"Tepat! AI sebagai alat bantu belajar."]]]]}
];
const $=h=>{A.innerHTML=h};
const fr=(t,m,n)=>$(`<div class="top">${t}</div><div class="mn">${m}</div><div class="nv">${n}</div>`);
const bt=(l,f,c="",d="")=>`<button class="b ${c}" onclick="${f}" ${d}>${l}</button>`;
const hud=()=>`<span>Misi ${cur+1}/5: ${LV[cur].n}</span><span>${"❤️".repeat(lives)}${"🖤".repeat(3-lives)} · Skor ${S.sc}</span>`;
function snd(ok){if(S.mute)return;try{ac=ac||new AudioContext();const o=ac.createOscillator(),g=ac.createGain();o.connect(g);g.connect(ac.destination);o.frequency.value=ok?880:220;g.gain.value=.08;o.start();o.stop(ac.currentTime+.18)}catch(e){}}
function fb(ok,m){snd(ok);const f=document.getElementById("fb");f.className="fb "+(ok?"ok":"no");f.innerHTML=(ok?"✅ ":"❌ ")+m}
function ans(ok,m){if(ok)S.sc+=10;else lives--;fb(ok,m);document.querySelector(".top").innerHTML=hud();if(lives<=0){setTimeout(fail,1200);return false}return true}
function home(){fr("<span>🤖 KKA</span><span>Teknologi Informasi</span>",`<div class="c"><svg width="22%" viewBox="0 0 100 80"><rect x="25" y="20" width="50" height="40" rx="8" fill="#3730a3"/><circle cx="40" cy="38" r="6" fill="#fff"/><circle cx="60" cy="38" r="6" fill="#fff"/><rect x="38" y="50" width="24" height="4" rx="2" fill="#fde68a"/><rect x="48" y="8" width="4" height="12" fill="#3730a3"/><circle cx="50" cy="8" r="4" fill="#f59e0b"/></svg><h1>Koding dan Kecerdasan Artifisial: Misi Teknisi AI</h1><p>Jadilah teknisi di Pusat Layanan Digital sekolah dan selesaikan 5 misi!</p></div>`,bt("Panduan","guide()")+bt("Mulai Bermain ▶","map()","p"))}
function guide(){fr("<span>Panduan</span>","<h2>Cara Bermain</h2><div class='pl'>🎯 <b>Tujuan:</b> kamu mampu menjelaskan konsep KKA, menyusun algoritma, membaca kode dasar, memahami machine learning, dan memakai AI secara etis.</div><div class='pl'>🗺️ Ada 5 misi. Misi baru terbuka setelah misi sebelumnya selesai. Misi yang selesai boleh dimainkan ulang.</div><div class='pl'>❤️ Tiap misi punya 3 nyawa. Jawaban salah mengurangi nyawa. Nyawa habis berarti misi diulang.</div><div class='pl'>⭐ Jawaban benar +10 skor. Sisa nyawa di akhir misi menjadi bonus. Ada suara benar/salah (bisa dimatikan di peta).</div><div class='pl'>📱 Putar HP ke mode landscape agar tampilan lebih besar.</div>",bt("◀ Kembali","home()")+bt("Ke Peta Misi ▶","map()","p"))}
function map(){const all=S.dn.every(x=>x);fr("<span>Peta Misi</span><span>Skor "+S.sc+"</span>",`<p>Pilih misi. Bintang menunjukkan sisa nyawa terbaikmu.</p><div class="mp">${LV.map((l,i)=>{const o=i==0||S.dn[i-1];return bt(`<span class="ic">${o?l.ic:"🔒"}</span>${i+1}. ${l.n}<br>${S.dn[i]?"⭐".repeat(S.st[i]):o?"Siap dimainkan":"Terkunci"}`,`intro(${i})`,S.dn[i]?"ok":"",o?"":"disabled")}).join("")}</div>`,bt("◀ Kembali","guide()")+bt(S.mute?"🔇 Suara mati":"🔊 Suara hidup","S.mute=!S.mute;map()")+bt("Lihat Hasil ▶","res()","p",all?"":"disabled"))}
function intro(i){cur=i;lives=3;const l=LV[i];fr(hud(),`<div class="c"><span style="font-size:4em">${l.ic}</span><h2>Misi ${i+1}: ${l.n}</h2></div><div class="pl">📋 ${l.x}</div><div class="pl">🎯 Tujuan: ${l.tj}</div>`,bt("◀ Peta","map()")+bt("Mulai Misi ▶","play()","p"))}
function play(){M={};lives=3;({match:rM,order:rO,fill:rF,sort:rS,dec:rD})[LV[cur].t](true)}
function pg(m,extra=""){fr(hud(),m+`<div id="fb" class="fb">Pilih jawabanmu.</div><div id="nx"></div>`,bt("◀ Peta","map()")+extra)}
function win(){const b=lives*10;S.sc+=b;S.dn[cur]=1;S.st[cur]=Math.max(S.st[cur],lives);fr("<span>Misi Selesai!</span><span>Skor "+S.sc+"</span>",`<div class="c"><span style="font-size:4em">🎉</span><h2>Misi ${cur+1} selesai!</h2><p>Sisa nyawa ${"❤️".repeat(lives)} memberi bonus +${b}.</p></div>`,bt("◀ Peta","map()")+(cur<4?bt("Misi Berikutnya ▶","intro("+(cur+1)+")","p"):bt("Lihat Hasil ▶","res()","p")))}
function fail(){fr("<span>Nyawa Habis</span>",`<div class="c"><span style="font-size:4em">💥</span><h2>Coba lagi, ya!</h2><p>Baca umpan balik dengan teliti, lalu ulangi misi ini.</p></div>`,bt("◀ Peta","map()")+bt("Ulangi Misi ▶","play()","p"))}
function rM(){const l=LV[cur];if(!M.defs){M.defs=sh(l.d.map(x=>x[1]));M.t=null;M.dn=[]}
const doneD=M.dn.map(i=>l.d[i][1]);
pg(`<p>Pilih satu istilah, lalu pilih artinya.</p><div class="g"><div>${l.d.map((x,i)=>bt(x[0],`mt(${i})`,M.dn.includes(i)?"ok":M.t===i?"sel":"",M.dn.includes(i)?"disabled":"")).join("")}</div><div>${M.defs.map((x,j)=>bt(x,`md(${j})`,doneD.includes(x)?"ok":"",doneD.includes(x)?"disabled":"")).join("")}</div></div>`)}
function mt(i){M.t=i;rM();document.getElementById("fb").textContent="Sekarang pilih artinya."}
function md(j){const l=LV[cur];if(M.t===null){document.getElementById("fb").textContent="Pilih istilah dulu.";return}
const ok=l.d[M.t][1]===M.defs[j];if(ok)M.dn.push(M.t);const t=M.t;M.t=null;const alive=ans(ok,ok?"Benar! "+l.d[t][0]+" = "+l.d[t][1]+".":"Belum cocok. Coba istilah lain.");if(!alive)return;
if(M.dn.length==l.d.length){setTimeout(win,900);rM2()}else{const m=document.getElementById("fb").outerHTML;rM();document.getElementById("fb").outerHTML=m}}
function rM2(){}
function rO(){const l=LV[cur];if(!M.it){M.it=sh(l.d);M.p=[]}
pg(`<p>Urutkan langkah dari yang pertama:</p><div class="g"><div>${M.it.map((x,i)=>bt(x,`po(${i})`,M.p.includes(x)?"ok":"",M.p.includes(x)?"disabled":"")).join("")}</div><div class="card"><b>Urutanmu:</b>${M.p.map((x,i)=>`<div class="pl">${i+1}. ${x}</div>`).join("")}</div></div>`)}
function po(i){const l=LV[cur],x=M.it[i],ok=l.d[M.p.length]===x;if(ok)M.p.push(x);const alive=ans(ok,ok?"Tepat! Langkah ke-"+M.p.length+" benar.":"Bukan langkah ini. Pikirkan apa yang terjadi lebih dulu.");if(!alive)return;
const m=document.getElementById("fb").outerHTML;rO();document.getElementById("fb").outerHTML=m;if(M.p.length==l.d.length)setTimeout(win,900)}
function rF(){const l=LV[cur];M.c=M.c||0;
const code=l.c.map(s=>s.replace(/\{(\d)\}/g,(_,k)=>k<M.c?l.b[k].a:k==M.c?"[ ? ]":"[ … ]")).join("\n");
pg(`<pre>${E(code)}</pre><p>Isi bagian ${M.c+1} dari ${l.b.length}:</p><div class="g" style="grid-template-columns:repeat(3,1fr)">${l.b[M.c].o.map((o,k)=>bt(E(o),`pf(${k})`)).join("")}</div>`)}
function pf(k){const l=LV[cur],b=l.b[M.c],ok=b.o[k]===b.a;const alive=ans(ok,ok?"Benar! "+b.h:"Kurang tepat. Petunjuk: "+b.h);if(!alive)return;
if(ok){M.c++;const m=document.getElementById("fb").outerHTML;if(M.c>=l.b.length){rF();document.getElementById("fb").outerHTML=m;setTimeout(win,1000)}else{rF();document.getElementById("fb").outerHTML=m}}}
function rS(){const l=LV[cur];M.c=M.c||0;const it=l.d[M.c];
pg(`<p>Pesan ${M.c+1} dari ${l.d.length}:</p><div class="card c" style="font-size:1.3em">✉️ ${it[0]}</div><div class="g" style="margin-top:.6em">${bt("✅ Aman","ps(0)","c")}${bt("🚫 Spam","ps(1)","c")}</div>`)}
function ps(v){const l=LV[cur],it=l.d[M.c],ok=it[1]===v;const alive=ans(ok,(ok?"Benar! ":"Salah. ")+it[2]);if(!alive)return;
document.querySelectorAll(".g .b").forEach(b=>b.disabled=true);
document.getElementById("nx").innerHTML=bt(M.c+1<l.d.length?"Pesan berikutnya ▶":"Selesai ▶","pn()","p")}
function pn(){M.c++;if(M.c>=LV[cur].d.length)win();else rS()}
function rD(){const l=LV[cur];M.c=M.c||0;const s=l.d[M.c];
pg(`<p>Situasi ${M.c+1} dari ${l.d.length}:</p><div class="card" style="font-size:1.2em">💬 ${s[0]}</div><div style="margin-top:.6em">${s[1].map((o,k)=>bt(o[0],`pd(${k})`)).join("")}</div>`)}
function pd(k){const l=LV[cur],o=l.d[M.c][1][k];const alive=ans(!!o[1],o[2]);if(!alive)return;
document.querySelectorAll(".mn .b").forEach(b=>b.disabled=true);
if(!o[1]){document.getElementById("nx").innerHTML=bt("Coba lagi situasi ini","rD()");return}
document.getElementById("nx").innerHTML=bt(M.c+1<l.d.length?"Situasi berikutnya ▶":"Selesai ▶","pdn()","p")}
function pdn(){M.c++;if(M.c>=LV[cur].d.length)win();else rD()}
function res(){const t=S.sc,g=t>=230?"Teknisi AI Ahli":t>=170?"Teknisi AI Muda":"Teknisi AI Pemula";
fr("<span>Evaluasi Akhir</span><span>Skor "+t+"</span>",`<div class="c"><h1>🏆 ${g}</h1><p>Skor akhirmu: <b>${t}</b></p></div><div class="g">${LV.map((l,i)=>`<div class="pl">${l.ic} ${l.n}: ${"⭐".repeat(S.st[i])||"belum selesai"}</div>`).join("")}</div><div class="pl">💭 <b>Refleksi:</b> Pada pekerjaan apa di bidang TI kamu akan memakai AI, dan bagaimana kamu memastikan hasilnya benar dan aman?</div>`,bt("◀ Peta","map()")+bt("Informasi Kreator ▶","cr()","p"))}
function cr(){fr("<span>Informasi Kreator</span>",`<h2>Informasi Kreator</h2><div class="pl">Kreator: [isi nama kreator di sini]</div><div class="pl">Bantuan AI: konten dan kode dibuat dengan bantuan Claude AI (Anthropic). Ilustrasi (ikon dan robot) dibuat dengan emoji dan kode SVG, tanpa aset eksternal.</div>`,bt("◀ Hasil","res()")+bt("Main Lagi ↺","S.sc=0;S.dn=[0,0,0,0,0];S.st=[0,0,0,0,0];home()","p"))}
home();
</script></body></html>
