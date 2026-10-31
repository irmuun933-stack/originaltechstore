# Original Tech Store — вэбсайт (originaltechstore.mn)

Dyson-ийн бүтээгдэхүүн, засвар, сэлбэгийн дэлгүүр. Сакура тауэр, 1 давхар, Улаанбаатар.

| Хаяг | Хуудас |
|---|---|
| `/` (`index.html`) | Нүүр хуудас — хар дэвсгэртэй хувилбар |

Бэлэн статик сайт: build хийх шаардлагагүй. Vercel файлуудыг шууд тараана.

## Бүтэц
```
index.html                нүүр хуудас (код, фонт, React/three.js дотор нь)
media/video/              барааны бичлэг: ai/ — бодит хэрэглээ, proc/ — дотоод бичлэг, *.mp4 — «Үйл явц»
products/ map/ store/ journey/ models/   зураг, 3D загвар
og.jpg, favicon.svg       Facebook-т хуваалцах зураг, таб дээрх тэмдэг
vercel.json               цэвэр хаяг, зураг/видеоны кэш
.vercelignore             source/ болон README сайт дээр нийтлэгдэхгүй
source/                   эх код (React) — засварлаад дахин гаргахад
```

## Vercel дээр deploy хийх (GitHub-аар)
1. **GitHub-д репо үүсгэх** — github.com → New repository → нэр: `originaltechstore` → Create.
2. **Файлуудаа оруулах** — файл олон (~280) тул **GitHub Desktop** ашиглахыг зөвлөе
   (вэбээр бол нэг удаад 100 файл хүртэл чирэх боломжтой).
   GitHub Desktop: File → Clone repository → `originaltechstore` → энэ ZIP-ийн доторх бүх зүйлийг
   клон хийсэн хавтас руу хуулна → Commit to main → Push origin.
3. **Vercel-д холбох** — vercel.com → Add New… → Project → Import Git Repository → `originaltechstore` → Import.
   - Framework Preset: **Other**
   - Build Command: хоосон (Override асаалттай бол устгана)
   - Output Directory: хоосон орхино
   - **Deploy** дарна → `originaltechstore.vercel.app` дээр сайт нээгдэнэ.
4. **Домэйн нэмэх** — Project → Settings → Domains → `originaltechstore.mn` нэмнэ (www-г ч нэмэхийг санал болгоно — зөвшөөрнө).
   Vercel тухайн төслийн DNS утгуудыг харуулна.
5. **Datacom-ийн DNS** — manage.datacom.mn → домэйн → DNS:
   - Төрөл **A**, хост `@` (эсвэл хоосон), утга — Vercel-ийн харуулсан IP (ихэвчлэн `76.76.21.21`)
   - Төрөл **CNAME**, хост `www`, утга — Vercel-ийн харуулсан `....vercel-dns-0xx.com`
   - `@` / `www` дээрх хуучин A/CNAME бичлэгийг устгана.
6. **Хүлээх** — DNS хэдэн цагаас 24 цагт тархана. Vercel-ийн Domains хэсэгт «Valid Configuration» болмогц
   HTTPS гэрчилгээ автоматаар гарна.

## Шинэчлэх
Сайтын файлыг солиод GitHub руу push хийхэд Vercel автоматаар дахин deploy хийнэ.
Кодоос дахин гаргах: `source/` → `HOME_V=v1 sh build_web.sh` (зураг, видеог `source/public/` дотор
`media products map store journey models` хавтсуудаар хуулсан байх ёстой) → `dist/`-ийн агуулгыг энд хуулна.
