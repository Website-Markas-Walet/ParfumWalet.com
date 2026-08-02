---
site: parfumwalet.com
deploy: { host: unknown, cf_account: null, branch: main, deploy_hook: unknown }
url_patterns: { artikel: "/walet-untuk-{kondisi}.html", kota: "/parfum-walet-{kota}.html", page: "/{slug} (folder, mis. /kontak, /jangkauan-pengiriman)", desain: "/rumah-walet-{ukuran|material}.html" }
chrome: { header_lines: "95-170 (parfum-walet-medan.html, varian kanonik)", footer_lines: "257-338 (parfum-walet-medan.html, varian kanonik)", byte_identical: "variants:header7/footer8" }
analytics: { gtm: "GTM-K8F59DT", ga4_property_id: "", tiktok: "", fb_verify: "", adsense: "" }
brand: { primary: "#e1bb48", font: "Work Sans (body) / Poppins (heading)", logo: "/wp-content/uploads/2021/07/cropped-logo-parfumwalet.png", favicon: "/wp-content/uploads/2021/07/cropped-favicon-32x32.png" }
ecosystem_menu: absent
contact: { wa: "https://con.tact.my.id/fairuz-0196-parfumwaletcom (0877 2526 0196)", email: "sales@markaswalet.com" }
media: { local_mb: 67, hotlink: "blogspot:24unique/151pages, gravatar:36" }
content: { articles: 49, kota_unique: 102, kota_admin_level: kota }
cleanup:
  - "canonical & og:url masih menunjuk domain staging qsandbox.me -> normalkan ke https://parfumwalet.com"
  - "robots.txt & sitemap.xml tidak ada sebelumnya (disediakan di PR ini)"
  - "chrome drift: 7 varian header / 8 varian footer -> tetapkan 1 kanonik (varian bermenu, 113 hal)"
  - "36 halaman artikel TIDAK punya menu navigasi utama -> samakan ke chrome kanonik"
  - "gambar oversized (PNG s/d 8.6MB) + duplikat ukuran responsif WP -> optimasi"
  - "2 file prefix parfum-walet- BUKAN kota (burung-walet-betah, kunci-produktivitas-sarang-walet-meroket)"
blockers:
  - "Mekanisme deploy tidak diketahui dari repo (tidak ada config) -> butuh konfirmasi pemilik infra"
  - "Branch produksi diduga 'main' -> perlu konfirmasi"
  - "Metode akses tulis CMS (rekomendasi: GitHub App contents:write) -> keputusan pemilik"
---

Catatan (session parfumwalet.com):

- **Aku HTML statis hasil export WordPress (theme Kadence)** — tanpa DB, PHP, atau build step.
  Dilayani langsung dari isi repo `Website-Markas-Walet/ParfumWalet.com`.
- **Deploy = blocker utama.** Tidak ada jejak mekanisme deploy di dalam repo (tidak ada CNAME,
  workflow, config Cloudflare/Vercel). Match "cloudflare" hanya referensi CDN library, bukan
  hosting. `host: unknown` sampai pemilik infra mengonfirmasi.
- **Chrome:** cukup ditandai batasnya (lihat frontmatter). Varian kanonik = varian bermenu
  (113 halaman). TIDAK ada perubahan yang di-commit ke file situs — hanya penandaan.
- **url_patterns:** halaman konten pakai ekstensi `.html`; hanya 2 halaman utilitas berbentuk
  folder (`/kontak`, `/jangkauan-pengiriman`). Link internal root-relative.
- **Analytics:** hanya GTM-K8F59DT (di 118 halaman). Tidak ada GA4/TikTok/FB/AdSense langsung.
- **Media:** 67 MB lokal (435 gambar). Hotlink eksternal = 24 URL unik (Blogspot/Blogger)
  dipakai di 151 halaman + 36 avatar Gravatar -> rehome ke R2 (ringan, ~24 file).
- **Konten:** 49 artikel + 102 kota (dataset 1 template) + 1 home + 2 halaman utilitas = 154 hal.
- **ecosystem_menu: absent** — parfum belum punya menu jaringan lintas-brand.

Data pendukung terstruktur ada di repo: `site.config.json`, `url_patterns.json`,
`dataset-kota.json`, `media-inventory.json`, `sitemap.xml`, `robots.txt`, dan detail di
`RESPONS-BRIEF-CMS.md` / `KONDISI-AKTUAL-SITUS.md`.
