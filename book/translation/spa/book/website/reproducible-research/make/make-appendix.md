(rr-make-appendix)=
# Appendix

(rr-make-appendix-dag)=
## Directed Acyclic Graph

A Directed Acyclic Graph (DAG) is a *graph* of nodes and edges that is:

1. *dirigido*: los bordes tienen una dirección y solo puedes caminar la gráfica en esa dirección
2. *acyclic*: does not contain cycles: A can't depend on B when B depends on A.

The latter property is of course quite handy for a build system. Puede encontrar más información sobre DAG en [Wikipedia](https://en.wikipedia.org/wiki/Directed_acyclic_graph).

(rr-make-appendix-installing)=
## Installing Make

First, check if you have GNU Make installed already. In a terminal type:

```bash
$ make
```

If you get `make: command not found` (or similar), you don't have Make. Si obtienes `: *** No se encontraron objetivos especificados ni makefile.  Parada.` tú tienes Make.

We'll be using **GNU Make** in this tutorial. Verifique que esto es lo que usted tiene escribiendo:

```bash
$ make --version
```

Si no tienes GNU Make pero tienes la versión BSD, es posible que algunas cosas no funcionen como se esperaba y recomendamos instalar GNU Make.

To install GNU Make, please follow these instructions:

- **Linux**: Use your package manager to install Make. Por ejemplo en Arch Linux:

  ```bash
  $ sudo pacman -S make
  ```

  Ubuntu:
  ```bash
  $ sudo apt-get install build-essential
  ```

- **MacOS**: If you have [Homebrew](https://brew.sh/) installed, it's simply:

  ```bash
  $ brew install make
  ```

  Si tienes una implementación de Make incorporada, por favor asegúrate de que es GNU Make marcando `make --version`.

(rr-make-appendix-advancedgr)=
## Advanced: Generating Rules using Call

*Esta sección continúa el tutorial anterior y muestra una característica de Hacer para la generación automática de reglas.*

En un pipeline de ciencias de datos, puede ser bastante común aplicar múltiples scripts a los mismos datos (por ejemplo cuando se comparan métodos o se prueban parámetros diferentes). En ese caso, puede volverse tedioso escribir una regla separada para cada script cuando solo el nombre del script cambie. Para simplificar este proceso, podemos dejar que expandamos una [*receta enlatada* ](https://www.gnu.org/software/make/manual/make.html#Canned-Recipes).

To follow along, switch to the `canned` branch:

```bash
$ make clean
$ git stash --all        # note the '--all' flag so we also stash the Makefile
$ git checkout canned
```

En esta rama notarás que hay un nuevo script en el directorio **scripts** llamado `generate_qqplot.py`. Este script funciona de forma similar al generate_histogram`. y` script (tiene la misma sintaxis de línea de comandos), pero genera un [QQ-plot](https://en.wikipedia.org/wiki/Q%E2%80%93Q_plot). El archivo **report.tex** también ha sido actualizado para incorporar estas parcelas.

Después de cambiar a la rama `enlatada` , habrá un Makefile en el repositorio que contiene una regla separada para generar los gráficos QQ. Este Makefile se ve así:

```makefile
# Makefile for analysis report
#

ALL_CSV = $(wildcard data/*.csv)
DATA = $(filter-out $(wildcard data/input_file_*.csv),$(ALL_CSV))
HISTOGRAMS = $(patsubst data/%.csv,output/figure_%.png,$(DATA))
QQPLOTS = $(patsubst data/%.csv,output/qqplot_%.png,$(DATA))

.PHONY: all clean

all: output/report.pdf

$(HISTOGRAMS): output/histogram_%.png: data/%.csv scripts/generate_histogram.py
    python scripts/generate_histogram.py -i $< -o $@

$(QQPLOTS): output/qqplot_%.png: data/%.csv scripts/generate_qqplot.py
    python scripts/generate_qqplot.py -i $< -o $@

output/report.pdf: report/report.tex $(FIGURES)
    cd report/ && pdflatex report.tex && mv report.pdf ../$@

clean:
    rm -f output/report.pdf
    rm -f $(HISTOGRAMS) $(QQPLOTS)
```

You'll notice that the rules for histograms and QQ-plots are very similar.

A medida que crece el número de scripts que desea ejecutar en sus datos, esto puede llevar a un gran número de reglas en el Makefile que son casi exactamente las mismas. We can simplify this by creating a [*canned recipe*](https://www.gnu.org/software/make/manual/html_node/Canned-Recipes.html) that takes both the name of the script and the name of the genre as input:

```makefile
define run-script-on-data
output/$(1)_$(2).png: data/$(2).csv scripts/generate_$(1).py
    python scripts/generate_$(1).py -i $$< -o $$@
endef
```

Ten en cuenta que en esta receta usamos `$(1)` para `histograma` o `qqqplot` y `$(2)` para el género. Estos corresponden a los argumentos de función esperados a la receta enlatada de `run-script-on-data`. Además, nota que usamos `$$<` y `$$@` en la receta real, con dos símbolos `$` para escapar. Para crear realmente todos los objetivos, necesitamos una línea que llame esta receta enlatada.  En nuestro caso, utilizamos un doble para bucle sobre los géneros y los scripts:

```makefile
$(foreach genre,$(GENRES),\
    $(foreach script,$(SCRIPTS),\
        $(eval $(call run-script-on-data,$(script),$(genre))) \
    ) \
)
```

In these lines the `\` character is used for continuing long lines.

The full Makefile then becomes:

```makefile
# Makefile for analysis report
#

ALL_CSV = $(wildcard data/*.csv)
DATA = $(filter-out $(wildcard data/input_file_*.csv),$(ALL_CSV))
HISTOGRAMS = $(patsubst %,output/histogram_%.png,$(GENRES))
QQPLOTS = $(patsubst %,output/qqplot_%.png,$(GENRES))

GENRES = $(patsubst data/%.csv,%,$(DATA))
SCRIPTS = histogram qqplot

.PHONY: all clean

all: output/report.pdf

define run-script-on-data
output/$(1)_$(2).png: data/$(2).csv scripts/generate_$(1).py
    python scripts/generate_$(1).py -i $$< -o $$@
endef

$(foreach genre,$(GENRES),\
    $(foreach script,$(SCRIPTS),\
        $(eval $(call run-script-on-data,$(script),$(genre)))\
    )\
)

output/report.pdf: report/report.tex $(HISTOGRAMS) $(QQPLOTS)
    cd report/ && pdflatex report.tex && mv report.pdf ../$@

clean:
    rm -f output/report.pdf
    rm -f $(HISTOGRAMS) $(QQPLOTS)
```

Ten en cuenta que hemos añadido una variable `SCRIPTS` con el histograma `` y `nombres de qqplot`. Si tuviéramos que añadir otro script que siga el mismo patrón que estos dos, solo necesitaríamos añadirlo a la variable `SCRIPTS` .

To build all of this, run

```bash
$ make -j 4
```
