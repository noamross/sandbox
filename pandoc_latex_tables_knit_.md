<!--begin.rcode
render_gfm()
end.rcode-->

We can use xtable to produce latex table formatted in the output. 
<!--begin.rcode results="asis"
library(xtable)
ctl <- c(4.17,5.58,5.18,6.11,4.50,4.61,5.17,4.53,5.33,5.14)
trt <- c(4.81,4.17,4.41,3.59,5.87,3.83,6.03,4.89,4.32,4.69)
group <- gl(2,10,20, labels=c("Ctl","Trt"))
weight <- c(ctl, trt)
mytable <- summary(lm(weight ~ group))
xtable(mytable)
end.rcode-->

Though the output is markdown, pandoc can regonize the resulting latex block, and render the table. 
Unfortunately, pandoc doesn't like the math markup that comes out in this data table title. 
Consequently,

    pandoc -S pandoc_latex_tables.md -o pandoc_latex.pdf 

fails.  Deleting the math markup in the table title fixes this. 
