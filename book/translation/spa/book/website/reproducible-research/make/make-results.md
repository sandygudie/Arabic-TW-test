(rr-make-results)=
# Including numerical results and tables

En este punto puedes estar pensando "¡Es tan genial que ahora puedo incluir figuras en mis manuscritos! But how exactly does this work for numerical results?"

El papel reproducible enlazado arriba muestra una forma de hacerlo: Después de calcular los resultados, están escritos en forma de tabla LaTeX . Here is how one of these tables looks like right after it was computed:

```latex
\begin{tabular}{lrrr|rrrr}
Property & HypoParsr & Sniffer & Suitability & Pattern & Type & No Tie & Full\\
\hline
Delimiter & 87.48 & 86.82 & 65.41 & 92.61 & 88.33 & 91.38 & \textbf{94.92}\\
Quotechar & 82.90 & 92.36 & 44.60 & 95.23 & 90.10 & 93.80 & \textbf{97.36}\\
Escapechar & 87.96 & 94.37 & 74.85 & 97.95 & 96.26 & 95.44 & \textbf{99.25}\\
Overall & 80.60 & 85.45 & 38.19 & 90.99 & 83.61 & 90.61 & \textbf{93.75}\\
\hline
\end{tabular}
```

Para incluir esta tabla en tu manuscrito, puedes usar la función `\input{}` de LaTeX. Si el archivo con la tabla se llama `mytable.tex`, este comando puede insertarlo en tu manuscrito:

```latex
\begin{table}
\input{mytable}
\end{table}
```

An alternative is to make use of variables. En lugar de crear una tabla en un archivo separado, puede escribir un esqueleto de tabla y poblarlo con variables. Los resultados que calculas están asociados con las variables y, una vez que tu manuscrito está compilado, las variables se intercambian por resultados numéricos reales. Here is how such a table looks like in your manuscript:

```latex
\begin{table}
    \begin{tabular*}{ccc}
        \textbf{Variable} & \textbf{Mean}   & \textbf{Std. deviation} \
        \hline
        Variable 1        & \var1mean       & \var1std                \
        Variable 2        & \var2mean       & \var2std                \
    \end{tabular*}
\end{table}
```

Puede notar que `\var1mean` no es un comando LaTeX estándar: ¡Es una variable que puedes definir tú mismo! How is this done? Haz que tu script imprima los resultados que calculas dentro de una definición de `\newcommand{}{}` en un archivo, por ejemplo como este (ejemplo simplificado de Python):

```python
# this loops to data vectors of two variables (data1, data2), compute the
# mean and standard deviation, and print the results together with the
# variable name ('var1', 'var2')
for name, data in (['var1', data1], ['var2', data2]):
    mean = np.mean(data)
    std = np.mean(data)
    print('\\newcommand{\\%s }{ %f }' % (name + 'mean', mean))
    print('\\newcommand{\\%s }{ %f }' % (name + 'std', std))
```

Digamos que la media del primer conjunto de datos es 9.2, la definición se vería este: `\newcommand{\var1mean}{9.2}`. Ten en cuenta que este ejemplo utiliza Python, pero puedes usar cualquier idioma o método con el que estés familiarizado para imprimir definiciones como esta. Con esta definición, LaTeX intercambia la celda de la tabla con `\var1mean` con el resultado numérico del cálculo. Puede capturar las definiciones y escribirlas en un archivo usando la redirección con `>`. In this example, we write it to a file called `results_def.tex`

```makefile
results_def.tex: code/make_summary_stats.py
    python code/make_summary_stats.py > results_def.tex
```

Como alternativa a `>`, también podría redireccionar los resultados usando el Unix [pipe](https://en.wikipedia.org/wiki/Pipeline_(Unix)) y el comando [tee](https://en.wikipedia.org/wiki/Tee_(command)) (`python code/make_Texty_stats. y | tee results_def.tex`). Esto no solo redirigirá la salida del script a un archivo, sino que también imprimirá en tu terminal. Este útil truco puede ayudarte a observar si todo funciona como se esperaba durante la ejecución de tu script.

Finalmente, usa el comando `input{}` para incluir las nuevas variables en tu manuscrito y las variables en las tablas:

```latex
\begin{document}
\input{results_def.tex}
```

Los ejemplos mostrados aquí son simplistas, pero con un poco de pensamiento, puedes asegurarte de incluir resultados en tu manuscrito del mismo modo que se calculan. Esto te ayuda (no hay errores copiando resultados a las tablas, ¡aún!) y hace que tu investigación sea más accesible y reproducible.
