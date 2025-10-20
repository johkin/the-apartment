# Lägenheten i Åre – webbplats

Detta repo innehåller en GitHub Pages-sajt byggd med Jekyll och temat Minimal Mistakes. Nedan hittar du enkla steg för att köra sajten lokalt på din dator.

## Starta sajten lokalt

1. Förkrav
   - Ruby (2.7+ rekommenderas, 3.x fungerar bra)
   - Bundler (Rubygem för att installera beroenden)
   - Git (för att klona repot)

2. Klona repot och gå in i mappen
   - git clone <din-repo-url>
   - cd the-apartment

3. Installera beroenden
   - bundler: kör `gem install bundler` om du inte redan har det
   - installera projektets gems: `bundle install`

4. Starta utvecklingsservern
   - kör: `bundle exec jekyll serve`
   - öppna: http://localhost:4000 i webbläsaren
   - servern uppdaterar sidan automatiskt när du sparar filer

Tips: Om du använder en organisations- eller projektsida med baseurl (t.ex. /the-apartment) kommer servern även skriva ut rätt lokalt URL i terminalen. Följ den länk som skrivs ut.

## Göra ändringar
- Innehållet finns i index.md och i mappen `_pages/` (boka, galleri, info).
- Bilder ligger i `assets/images/`.
- Site-inställningar finns i `_config.yml` och navigation i `_data/navigation.yml`.

## Vanliga problem
- Meddelande om saknat plugin (t.ex. jekyll-include-cache): kör `bundle install` igen och starta om `jekyll serve`.
- Fel på Windows kring UTF-8/ikonv: säkerställ att du kör i en terminal med UTF-8 och att rätt Ruby är installerad (t.ex. via RubyInstaller).
- PORT redan upptagen: starta med annan port: `bundle exec jekyll serve --port 4001`.

## Docker (valfritt)
Om du inte vill installera Ruby lokalt kan du köra med Docker:
- Bygg/kör i en container (engångsserve):
  - `docker run --rm -it -p 4000:4000 -v "$PWD":/srv/jekyll -w /srv/jekyll jekyll/jekyll:4 bash -lc "bundle install && bundle exec jekyll serve --host 0.0.0.0"`
- Öppna http://localhost:4000

## Publicering
- GitHub Pages bygger sajten automatiskt när du pushar till main/master (beroende på din repo-inställning).
- Tänk på att fältet `baseurl` i `_config.yml` ska motsvara din publiceringsväg om du inte publicerar på en användarsida (t.ex. `/the-apartment`).