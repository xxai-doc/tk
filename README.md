<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Ilki bilen nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) gurmak maslahat berilýär, we `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) kataloga girenden soň awtomatiki ýerine ýetiriler).

Manysy: Hytaý diline ýapon, koreý, iňlis, iňlis diline terjime. Diňe hytaý we iňlis dillerini goldamak isleseňiz, diňe `zh: en` ýazyp bilersiňiz.

## öňdäki kody

* [öňdäki kody](https://github.com/xxai-art/web)
* [Tutuşlygyna sahypa üçin dil paketleri](https://github.com/xxai-art/web/tree/main/i18n)
* [Giriş modullary üçin dil paketleri](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Web sahypasy köp dilli resminamalar](https://github.com/xxai-doc)

Öňdäki programmirleme dili, kofe ýazgysynyň sintaksisine esaslanýan käbir aýratynlyklary goşýan [@ w5 / coffee_plus](http://npmjs.com/@w5/coffee_plus) , serediň [./coffee_plus.md](./coffee_plus.md) .

## Web sahypalarynyň we resminamalaryň halkaralaşmagy

Aşakdaky 3 taslama guruň

* [@ w5 / mdt](https://www.npmjs.com/package/@w5/mdt)

  Goşundy `.mdt` , daşarky faýllara salgylanmak we `.md` goşulmasy bilen bellik döretmek üçin `<+ ./coffee_plus/import.js>` meňzeş sintaksis ulanyp bilersiňiz.

* [@ w5 / trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown terjimesi kodlary we baglanyşyklary terjime etmez we terjime edilen sözlemleri keş eder. Terjime üýtgedilen bolsa, ýöne asyl tekst üýtgedilmedik bolsa, ony gaýtadan ýerine ýetirmek terjimäniň üýtgemegine ýazylmaz.

* [@ w5 / i18n](https://www.npmjs.com/package/@w5/i18n)

  `yaml` döredilen web sahypalaryny terjime etmek üçin dil faýllary.

### Resminamanyň terjimesini awtomatlaşdyrmak boýunça görkezmeler

Kod ammaryna serediň [xxai-art / doc](https://github.com/xxai-art/doc)

Ilki bilen nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) gurmak maslahat berilýär, we `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) kataloga girenden soň awtomatiki ýerine ýetiriler).

Hundredsüzlerçe dile terjime edilen uly kod bazasynyň öňüni almak üçin her dil üçin aýratyn kod bazasyny döretdim we kod bazasyny saklamak üçin bir gurama döretdim.

Daşky gurşaw üýtgeýjisini `GITHUB_ACCESS_TOKEN` düzmek we soňra [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) işletmek kod ammaryny awtomatiki döreder.

Elbetde, ony kod bazasyna hem goýup bilersiňiz.

Terjime skriptine salgylanma [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Scriptazuw kody aşakdaky ýaly düşündirilýär:

[bunx](https://bun.sh/docs/cli/bunx) has çalt npx üçin çalyşma. Elbetde, çörek gurulmadyk bolsa, ýerine `npx` ulanyp bilersiňiz.

`bunx mdt zh` .hd katalogynda `.mdt` görkezýär `.md` , aşakdaky 2 baglanyşyk faýlyna serediň

* [kofe_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [kofe_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` terjime üçin esasy koddyr (diňe `nodejs` gurlan bolsa, `bun` we `direnv` gurulmadyk bolsa, terjime etmek üçin `npx i18n` hem işledip bilersiňiz).

[I18n.yml-y](https://github.com/xxai-art/doc/blob/main/i18n.yml) derňär, bu resminamadaky `i18n.yml` konfigurasiýasy aşakdaky ýaly:

```
en:
zh: ja ko en
```

Manysy: Hytaý diline ýapon, koreý, iňlis, iňlis diline terjime. Diňe hytaý we iňlis dillerini goldamak isleseňiz, diňe `zh: en` ýazyp bilersiňiz.

Iň soňkusy [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) bolup, `README.md` ýazgysyny döretmek üçin her diliň `README.md` sözbaşysynyň baş ady bilen birinji subtitriniň arasyndaky mazmuny çykarýar. Kod gaty ýönekeý, oňa özüňiz seredip bilersiňiz.

Google API mugt terjime üçin ulanylýar. Google-a girip bilmeýän bolsaňyz, proksi düzüň we aşakdaky ýaly proksi düzüň:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Terjime skripti `.i18n` katalogynda terjime edilen keş keşbini döreder, `git status` bilen barlaň we gaýtalanýan terjimelerden gaça durmak üçin kod ammaryna goşuň.

Keşi täzelemek üçin her gezek terjimäni üýtgedeniňizde `bunx i18n` işlediň.

Asyl tekst we terjime şol bir wagtda üýtgedilen bolsa, keş keşi bulaşar, şonuň üçin üýtgetmek isleseňiz, diňe birini üýtgedip bilersiňiz we keş keşini täzelemek üçin `bunx i18n` işledip bilersiňiz.
