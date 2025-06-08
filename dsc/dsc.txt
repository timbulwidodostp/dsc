# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Dynamic Synthetic Control Use dsc With (In) R Software
install.packages("remotes") 
remotes::install_github("conflictlab/dsc")
library("dsc")
dsc = read.csv("https://raw.githubusercontent.com/timbulwidodostp/dsc/main/dsc/dsc.csv",sep = ";")
# Estimation Dynamic Synthetic Control Use dsc With (In) R Software
colnames(dsc)[2:5] <- c("id", "unit", "time", "value")
dsc$invest_ratio <- dsc$invest / dsc$value
dsc$value_raw <- dsc$value
special_preds <- expression(list(
  list(dep.var, 1960:1969, c("mean")),
  list("invest_ratio", 1964:1969, c("mean")),
  list("popdens", 1969, c("mean")),
  list("sec.agriculture", 1961:1969, c("mean")),
  list("sec.energy", 1961:1969, c("mean")),
  list("sec.industry", 1961:1969, c("mean")),
  list("sec.construction", 1961:1969, c("mean")),
  list("sec.services.venta", 1961:1969, c("mean")),
  list("sec.services.nonventa", 1961:1969, c("mean")),
  list("school.illit", 1964:1969, c("mean")),
  list("school.prim", 1964:1969, c("mean")),
  list("school.med", 1964:1969, c("mean")),
  list("school.high", 1964:1969, c("mean")),
  list("school.post.high", 1964:1969, c("mean"))
))
dsc <- dsc(data = dsc, start.time = 1955, end.time = 1997, treat.time = 1970, dependent = "Basque Country (Pais Vasco)",
predictors = NULL, parallel = TRUE, special.predictors = special_preds, time.predictors.prior = 1955:1969, time.optimize.ssr = 1955:1969)
dsc$value
dsc$average
dsc$synthetic
# Dynamic Synthetic Control Use dsc With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished