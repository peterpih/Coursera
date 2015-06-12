### Notes on knitr()

Use the RMarkdown facility in RStudio, or

.Rmd -> .md -> .html

```{R}
> library(knitr)
```
then
```{R}
> knitr2html("filename.Rmd")
```
or
```{R}
> browserURL("document.html")
```

results: asis, hide
echo: TRUE, FALSE

fig.height
fig.width
