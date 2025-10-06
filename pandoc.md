# pandoc

## Dependencias

```bash
sudo apt update
sudo apt install pandoc texlive-xetex texlive-latex-recommended \
  texlive-fonts-recommended texlive-latex-extra \
  fonts-texgyre fonts-dejavu fonts-liberation fonts-inconsolata
# opcional si está disponible
sudo apt install fonts-firacode
```

En arch:

```bash
sudo pacman -Syu texlive-core texlive-bin texlive-latex texlive-latexextra texlive-fontsextra texlive-lm
```

En arch he tenido que agregar esto en `/etc/texmf/web2c/fmtutil.cnf`:

```
xelatex xetex language.dat -etex xelatex.ini
```

## Regenerar fuentes

En muchas ocasiones si instalas fuentes nuevas, tendras que regenerar las que latex tiene disponibles:

```bash
fc-cache -fv
sudo fmtutil-sys --all
```

Luego tuve que lanzar: `sudo fmtutil-sys --byfmt xelatex`

## Convertir a pdf

```bash
pandoc doc.md -o output.pdf \
  --pdf-engine=xelatex \
  -V mainfont="DejaVu Sans Mono" \
  -V geometry:margin=2cm
```

## Página nueva

Podemos añadir el comando `\newpage` para generar una página nueva y ordenar mejor los contenidos.

## Mermaid filter

Puedes instalar este filtro:

```bash
npm install --global mermaid-filter
```

Y luego usarlo asi:

```bash
pandoc doc.md -o output.pdf \
  --pdf-engine=xelatex \
  -V mainfont="DejaVu Sans Mono" \
  -V geometry:margin=2cm \
  -F mermaid-filter
```

https://github.com/raghur/mermaid-filter
