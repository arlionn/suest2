# suest2： Seemingly unrelated estimation with support for Panel data models

Type `ssc install suest, replace` to download the ado file. It will be saved as **D:\stata15\ado\plus\suest.ado**. 

You can open the adofile and rename it as **suest2.ado**.

```stata
. webuse nlswork.dta, clear
. xtset idcode year

. xtreg ln_wage hours i.year if union==1, fe
. est store m1
. xtreg ln_wage hours i.year if union==0, fe
. est store m0

. suest2 m1 m0

. test [m1_mean]hours=[m0_mean]hours
```

