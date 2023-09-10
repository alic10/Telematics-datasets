## Telematics-datasets

### Create simulated telematics dataset 1
set.seed(123)

n <- 10000  # number of rows

dataset1 <- tibble(
  Timestamp = seq(from = as.POSIXct("2023-01-01 00:00"), by = "min", length.out = n),
  Speed = round(runif(n, 20, 90), 0),
  BrakingPattern = sample(c("Sudden", "Gradual"), n, replace = TRUE),
)

### Generate acceleration values based on BrakingPattern

dataset1$Acceleration <- ifelse(
  dataset1$BrakingPattern == "Sudden",
  round(runif(n, 10, 35), 1),  # higher range for sudden brakes
  round(runif(n, 0, 20), 1)   # normal range for gradual brakes
)

### Create simulated telematics dataset 2

set.seed(123)

dataset2 <- tibble(
  Timestamp = seq(from = as.POSIXct("2023-01-01 00:00"), by = "min", length.out = n),
  Location = sample(c("Urban", "Suburban", "Rural"), n, replace = TRUE),
  Cornering = round(runif(n, 0, 1), 2),
  Mileage = round(runif(n, 0, 150), 0)
)
 
