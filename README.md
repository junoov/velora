# Velora — Astro Rebuild (1:1 Framer Template)

Rebuild 1:1 dari template portfolio **Velora** ([velora-template.framer.website](https://velora-template.framer.website/)) menggunakan **Astro**, **Lenis**, dan **GSAP**.

Dibangun dengan semantic markup bersih, modular Astro components, asset lokal lengkap di `public/assets/`, dan animasi scrolling yang identik 1:1 dengan versi live.

## Stack

- [Astro](https://astro.build) (static output)
- [Lenis](https://lenis.darkroom.engineering) (smooth scrolling)
- [GSAP](https://gsap.com) + ScrollTrigger (motion runtime & synchronization)
- Inter & Inter Display fonts

## Struktur Proyek

```
velora/
├── public/
│   └── assets/               # Gambar karya, foto profil, video background, avatar
├── src/
│   ├── components/
│   │   ├── Nav.astro         # Sticky frosted glass navbar + mobile drawer
│   │   ├── Hero.astro        # Headline "Welcome.", bio, portrait Rizky Noviansyah, scroll link
│   │   ├── Works.astro       # 2x2 grid selected works (Korda, Folira, Modio, Revana)
│   │   ├── Services.astro    # Sticky stacking cards (Graphic, Lifestyle, Digital, Social)
│   │   ├── About.astro       # Sticky summary bio + career experience timeline
│   │   ├── Reviews.astro     # Interactive testimonial slideshow & quote cards
│   │   ├── Footer.astro      # Dark theme, big "Stay connected", CTA button, nav
│   │   └── FloatingWidget.astro # Bottom-right template preview card dengan video loop
│   ├── layouts/
│   │   └── BaseLayout.astro  # Meta tags, typography, dan inisialisasi Lenis + GSAP
│   ├── pages/
│   │   └── index.astro       # Single-page portfolio composition
│   └── styles/
│       └── global.css        # Reset, color tokens, typography & layout utilities
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

## Fitur & Animasi yang Direplikasi 1:1

1. **Header & Navigasi**: Sticky frosted glass (`backdrop-filter: blur(12px)`), logo Velora, smooth anchor scrolling ke setiap section (`#works`, `#services`, `#about`, `#review`), dan mobile hamburger drawer.
2. **Hero Section**: Typographic layout dengan H1 "Welcome.", deskripsi bio, foto potret Rizky Noviansyah dengan hover zoom, dan link scroll to more.
3. **Selected Works**: Grid 2x2 responsif dengan kartu karya (Korda, Folira, Modio, Revana), border radius, hover zoom, dan metadata.
4. **Services (Sticky Stacking)**: Fitur scrolling andalan Velora di mana tiap baris servis bertumpuk secara sticky (`top: calc(...)`) saat halaman di-scroll ke bawah.
5. **About & Experience**: Layout 2 kolom dengan kolom kiri profil Rizky Noviansyah yang sticky di viewport, sementara 5 riwayat karir di kanan scroll ke atas.
6. **Reviews Slideshow**: Carousel testimoni interaktif dengan tombol navigasi Prev/Next, kutipan, avatar profil, dan role.
7. **Footer / Contact**: Footer hitam kontras tinggi dengan typography masif "Stay connected", tombol "Get in touch", dan navigasi lengkap.
8. **Floating Preview Widget**: Widget melayang di pojok kanan bawah dengan video loop preview (`footer-video.mp4`) dan tombol "Use Template".

## Cara Menjalankan

```bash
npm install
npm run dev        # Jalankan server lokal → http://localhost:4321
npm run build      # Build static bundle ke dist/
npm run preview    # Preview hasil build
```
