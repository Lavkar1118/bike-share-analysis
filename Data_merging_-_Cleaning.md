Data_merging\_&\_cleaning
================
Lavanya Muthukumar
1/24/2022

\###Loading the libraries

``` r
library(tidyverse)
library(lubridate)
library(janitor)
library(ggplot2)
library(waldo) #compare col names across different dfs
library(chron)#convert time in character to time object
```

\###Loading the data (May 2020 - April 2021)

``` r
May_20 <- read_csv("Combined_data/May_20.csv")
```

    ## Rows: 200274 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Jun_20 <- read_csv("Combined_data/Jun_20.csv")
```

    ## Rows: 343005 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Jul_20 <- read_csv("Combined_data/Jul_20.csv")
```

    ## Rows: 551480 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Aug_20 <- read_csv("Combined_data/Aug_20.csv")
```

    ## Rows: 622361 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Sep_20 <- read_csv("Combined_data/Sep_20.csv")
```

    ## Rows: 532958 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Oct_20 <- read_csv("Combined_data/Oct_20.csv")
```

    ## Rows: 388653 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Nov_20 <- read_csv("Combined_data/Nov_20.csv")
```

    ## Rows: 259716 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (5): ride_id, rideable_type, start_station_name, end_station_name, memb...
    ## dbl  (6): start_station_id, end_station_id, start_lat, start_lng, end_lat, e...
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Dec_20 <- read_csv("Combined_data/Dec_20.csv")
```

    ## Rows: 131573 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Jan_21 <- read_csv("Combined_data/Jan_21.csv")
```

    ## Rows: 96834 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Feb_21 <- read_csv("Combined_data/Feb_21.csv")
```

    ## Rows: 49622 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Mar_21 <- read_csv("Combined_data/Mar_21.csv")
```

    ## Rows: 228496 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
Apr_21 <- read_csv("Combined_data/Apr_21.csv")
```

    ## Rows: 337230 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
    ## dbl  (4): start_lat, start_lng, end_lat, end_lng
    ## dttm (2): started_at, ended_at

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

\###Step 1: Checking data integrity and merging the data

\#The cyclistic data includes monthly ride informations in separate
files. We will first look at one of the datasets and get familiarized
with the column names, data types and missing values.

\#We will now merge the monthly data into a single file to create an
annaul dataset. However,before merging the data we need to check if the
column names and data types is similar across all of them.

\#We will remove NAs if any after merging the data

``` r
#get to know the col number, col names and data types in the df

colnames(May_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(May_20)
```

    ## spec_tbl_df [200,274 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:200274] "02668AD35674B983" "7A50CCAF1EDDB28F" "2FFCDFDB91FE9A52" "58991CF1DB75BA84" ...
    ##  $ rideable_type     : chr [1:200274] "docked_bike" "docked_bike" "docked_bike" "docked_bike" ...
    ##  $ started_at        : POSIXct[1:200274], format: "2020-05-27 10:03:52" "2020-05-25 10:47:11" ...
    ##  $ ended_at          : POSIXct[1:200274], format: "2020-05-27 10:16:49" "2020-05-25 11:05:40" ...
    ##  $ start_station_name: chr [1:200274] "Franklin St & Jackson Blvd" "Clark St & Wrightwood Ave" "Kedzie Ave & Milwaukee Ave" "Clarendon Ave & Leland Ave" ...
    ##  $ start_station_id  : num [1:200274] 36 340 260 251 261 206 261 180 331 219 ...
    ##  $ end_station_name  : chr [1:200274] "Wabash Ave & Grand Ave" "Clark St & Leland Ave" "Kedzie Ave & Milwaukee Ave" "Lake Shore Dr & Wellington Ave" ...
    ##  $ end_station_id    : num [1:200274] 199 326 260 157 206 22 261 180 300 305 ...
    ##  $ start_lat         : num [1:200274] 41.9 41.9 41.9 42 41.9 ...
    ##  $ start_lng         : num [1:200274] -87.6 -87.6 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:200274] 41.9 42 41.9 41.9 41.8 ...
    ##  $ end_lng           : num [1:200274] -87.6 -87.7 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:200274] "member" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(May_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##                  0                  0                321                321 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                321                321 
    ##      member_casual 
    ##                  0

``` r
colnames(Jun_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Jun_20)
```

    ## spec_tbl_df [343,005 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:343005] "8CD5DE2C2B6C4CFC" "9A191EB2C751D85D" "F37D14B0B5659BCF" "C41237B506E85FA1" ...
    ##  $ rideable_type     : chr [1:343005] "docked_bike" "docked_bike" "docked_bike" "docked_bike" ...
    ##  $ started_at        : POSIXct[1:343005], format: "2020-06-13 23:24:48" "2020-06-26 07:26:10" ...
    ##  $ ended_at          : POSIXct[1:343005], format: "2020-06-13 23:36:55" "2020-06-26 07:31:58" ...
    ##  $ start_station_name: chr [1:343005] "Wilton Ave & Belmont Ave" "Federal St & Polk St" "Daley Center Plaza" "Broadway & Cornelia Ave" ...
    ##  $ start_station_id  : num [1:343005] 117 41 81 303 327 327 41 115 338 84 ...
    ##  $ end_station_name  : chr [1:343005] "Damen Ave & Clybourn Ave" "Daley Center Plaza" "State St & Harrison St" "Broadway & Berwyn Ave" ...
    ##  $ end_station_id    : num [1:343005] 163 81 5 294 117 117 81 303 164 53 ...
    ##  $ start_lat         : num [1:343005] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:343005] -87.7 -87.6 -87.6 -87.6 -87.7 ...
    ##  $ end_lat           : num [1:343005] 41.9 41.9 41.9 42 41.9 ...
    ##  $ end_lng           : num [1:343005] -87.7 -87.6 -87.6 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:343005] "casual" "member" "member" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Jun_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##                  0                  0                468                468 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                468                468 
    ##      member_casual 
    ##                  0

``` r
colnames(Jul_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Jul_20)
```

    ## spec_tbl_df [551,480 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:551480] "762198876D69004D" "BEC9C9FBA0D4CF1B" "D2FD8EA432C77EC1" "54AE594E20B35881" ...
    ##  $ rideable_type     : chr [1:551480] "docked_bike" "docked_bike" "docked_bike" "docked_bike" ...
    ##  $ started_at        : POSIXct[1:551480], format: "2020-07-09 15:22:02" "2020-07-24 23:56:30" ...
    ##  $ ended_at          : POSIXct[1:551480], format: "2020-07-09 15:25:52" "2020-07-25 00:20:17" ...
    ##  $ start_station_name: chr [1:551480] "Ritchie Ct & Banks St" "Halsted St & Roscoe St" "Lake Shore Dr & Diversey Pkwy" "LaSalle St & Illinois St" ...
    ##  $ start_station_id  : num [1:551480] 180 299 329 181 268 635 113 211 176 31 ...
    ##  $ end_station_name  : chr [1:551480] "Wells St & Evergreen Ave" "Broadway & Ridge Ave" "Clark St & Wellington Ave" "Clark St & Armitage Ave" ...
    ##  $ end_station_id    : num [1:551480] 291 461 156 94 301 289 140 31 191 142 ...
    ##  $ start_lat         : num [1:551480] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:551480] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num [1:551480] 41.9 42 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:551480] -87.6 -87.7 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:551480] "member" "member" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Jul_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##                149                152                967                969 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                770                770 
    ##      member_casual 
    ##                  0

``` r
colnames(Aug_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Aug_20)
```

    ## spec_tbl_df [622,361 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:622361] "322BD23D287743ED" "2A3AEF1AB9054D8B" "67DC1D133E8B5816" "C79FBBD412E578A7" ...
    ##  $ rideable_type     : chr [1:622361] "docked_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:622361], format: "2020-08-20 18:08:14" "2020-08-27 18:46:04" ...
    ##  $ ended_at          : POSIXct[1:622361], format: "2020-08-20 18:17:51" "2020-08-27 19:54:51" ...
    ##  $ start_station_name: chr [1:622361] "Lake Shore Dr & Diversey Pkwy" "Michigan Ave & 14th St" "Columbus Dr & Randolph St" "Daley Center Plaza" ...
    ##  $ start_station_id  : num [1:622361] 329 168 195 81 658 658 196 67 153 177 ...
    ##  $ end_station_name  : chr [1:622361] "Clark St & Lincoln Ave" "Michigan Ave & 14th St" "State St & Randolph St" "State St & Kinzie St" ...
    ##  $ end_station_id    : num [1:622361] 141 168 44 47 658 658 49 229 225 305 ...
    ##  $ start_lat         : num [1:622361] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:622361] -87.6 -87.6 -87.6 -87.6 -87.7 ...
    ##  $ end_lat           : num [1:622361] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:622361] -87.6 -87.6 -87.6 -87.6 -87.7 ...
    ##  $ member_casual     : chr [1:622361] "member" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Aug_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##               7595               7691              10035              10110 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                938                938 
    ##      member_casual 
    ##                  0

``` r
colnames(Sep_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Sep_20)
```

    ## spec_tbl_df [532,958 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:532958] "2B22BD5F95FB2629" "A7FB70B4AFC6CAF2" "86057FA01BAC778E" "57F6DC9A153DB98C" ...
    ##  $ rideable_type     : chr [1:532958] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:532958], format: "2020-09-17 14:27:11" "2020-09-17 15:07:31" ...
    ##  $ ended_at          : POSIXct[1:532958], format: "2020-09-17 14:44:24" "2020-09-17 15:07:45" ...
    ##  $ start_station_name: chr [1:532958] "Michigan Ave & Lake St" "W Oakdale Ave & N Broadway" "W Oakdale Ave & N Broadway" "Ashland Ave & Belle Plaine Ave" ...
    ##  $ start_station_id  : num [1:532958] 52 NA NA 246 24 94 291 NA NA NA ...
    ##  $ end_station_name  : chr [1:532958] "Green St & Randolph St" "W Oakdale Ave & N Broadway" "W Oakdale Ave & N Broadway" "Montrose Harbor" ...
    ##  $ end_station_id    : num [1:532958] 112 NA NA 249 24 NA 256 NA NA NA ...
    ##  $ start_lat         : num [1:532958] 41.9 41.9 41.9 42 41.9 ...
    ##  $ start_lng         : num [1:532958] -87.6 -87.6 -87.6 -87.7 -87.6 ...
    ##  $ end_lat           : num [1:532958] 41.9 41.9 41.9 42 41.9 ...
    ##  $ end_lng           : num [1:532958] -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:532958] "casual" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Sep_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##              19691              19901              23373              23524 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                789                789 
    ##      member_casual 
    ##                  0

``` r
colnames(Oct_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Oct_20)
```

    ## spec_tbl_df [388,653 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:388653] "ACB6B40CF5B9044C" "DF450C72FD109C01" "B6396B54A15AC0DF" "44A4AEE261B9E854" ...
    ##  $ rideable_type     : chr [1:388653] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:388653], format: "2020-10-31 19:39:43" "2020-10-31 23:50:08" ...
    ##  $ ended_at          : POSIXct[1:388653], format: "2020-10-31 19:57:12" "2020-11-01 00:04:16" ...
    ##  $ start_station_name: chr [1:388653] "Lakeview Ave & Fullerton Pkwy" "Southport Ave & Waveland Ave" "Stony Island Ave & 67th St" "Clark St & Grace St" ...
    ##  $ start_station_id  : num [1:388653] 313 227 102 165 190 359 313 125 NA 174 ...
    ##  $ end_station_name  : chr [1:388653] "Rush St & Hubbard St" "Kedzie Ave & Milwaukee Ave" "University Ave & 57th St" "Broadway & Sheridan Rd" ...
    ##  $ end_station_id    : num [1:388653] 125 260 423 256 185 53 125 313 199 635 ...
    ##  $ start_lat         : num [1:388653] 41.9 41.9 41.8 42 41.9 ...
    ##  $ start_lng         : num [1:388653] -87.6 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:388653] 41.9 41.9 41.8 42 41.9 ...
    ##  $ end_lng           : num [1:388653] -87.6 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:388653] "casual" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Oct_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##              31198              31405              35631              35787 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                474                474 
    ##      member_casual 
    ##                  0

``` r
colnames(Nov_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Nov_20)
```

    ## spec_tbl_df [259,716 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:259716] "BD0A6FF6FFF9B921" "96A7A7A4BDE4F82D" "C61526D06582BDC5" "E533E89C32080B9E" ...
    ##  $ rideable_type     : chr [1:259716] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:259716], format: "2020-11-01 13:36:00" "2020-11-01 10:03:26" ...
    ##  $ ended_at          : POSIXct[1:259716], format: "2020-11-01 13:45:40" "2020-11-01 10:14:45" ...
    ##  $ start_station_name: chr [1:259716] "Dearborn St & Erie St" "Franklin St & Illinois St" "Lake Shore Dr & Monroe St" "Leavitt St & Chicago Ave" ...
    ##  $ start_station_id  : num [1:259716] 110 672 76 659 2 72 76 NA 58 394 ...
    ##  $ end_station_name  : chr [1:259716] "St. Clair St & Erie St" "Noble St & Milwaukee Ave" "Federal St & Polk St" "Stave St & Armitage Ave" ...
    ##  $ end_station_id    : num [1:259716] 211 29 41 185 2 76 72 NA 288 273 ...
    ##  $ start_lat         : num [1:259716] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:259716] -87.6 -87.6 -87.6 -87.7 -87.6 ...
    ##  $ end_lat           : num [1:259716] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:259716] -87.6 -87.7 -87.6 -87.7 -87.6 ...
    ##  $ member_casual     : chr [1:259716] "casual" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Nov_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##              24324              24434              26749              26826 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                284                284 
    ##      member_casual 
    ##                  0

``` r
colnames(Dec_20)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Dec_20)
```

    ## spec_tbl_df [131,573 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:131573] "70B6A9A437D4C30D" "158A465D4E74C54A" "5262016E0F1F2F9A" "BE119628E44F871E" ...
    ##  $ rideable_type     : chr [1:131573] "classic_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:131573], format: "2020-12-27 12:44:29" "2020-12-18 17:37:15" ...
    ##  $ ended_at          : POSIXct[1:131573], format: "2020-12-27 12:55:06" "2020-12-18 17:44:19" ...
    ##  $ start_station_name: chr [1:131573] "Aberdeen St & Jackson Blvd" NA NA NA ...
    ##  $ start_station_id  : chr [1:131573] "13157" NA NA NA ...
    ##  $ end_station_name  : chr [1:131573] "Desplaines St & Kinzie St" NA NA NA ...
    ##  $ end_station_id    : chr [1:131573] "TA1306000003" NA NA NA ...
    ##  $ start_lat         : num [1:131573] 41.9 41.9 41.9 41.9 41.8 ...
    ##  $ start_lng         : num [1:131573] -87.7 -87.7 -87.7 -87.7 -87.6 ...
    ##  $ end_lat           : num [1:131573] 41.9 41.9 41.9 41.9 41.8 ...
    ##  $ end_lng           : num [1:131573] -87.6 -87.7 -87.7 -87.7 -87.6 ...
    ##  $ member_casual     : chr [1:131573] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Dec_20))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##              11699              11699              13237              13237 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                111                111 
    ##      member_casual 
    ##                  0

``` r
colnames(Jan_21)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Jan_21)
```

    ## spec_tbl_df [96,834 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:96834] "E19E6F1B8D4C42ED" "DC88F20C2C55F27F" "EC45C94683FE3F27" "4FA453A75AE377DB" ...
    ##  $ rideable_type     : chr [1:96834] "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct[1:96834], format: "2021-01-23 16:14:19" "2021-01-27 18:43:08" ...
    ##  $ ended_at          : POSIXct[1:96834], format: "2021-01-23 16:24:44" "2021-01-27 18:47:12" ...
    ##  $ start_station_name: chr [1:96834] "California Ave & Cortez St" "California Ave & Cortez St" "California Ave & Cortez St" "California Ave & Cortez St" ...
    ##  $ start_station_id  : chr [1:96834] "17660" "17660" "17660" "17660" ...
    ##  $ end_station_name  : chr [1:96834] NA NA NA NA ...
    ##  $ end_station_id    : chr [1:96834] NA NA NA NA ...
    ##  $ start_lat         : num [1:96834] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num [1:96834] -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:96834] 41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num [1:96834] -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:96834] "member" "member" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Jan_21))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##               8625               8625              10277              10277 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                103                103 
    ##      member_casual 
    ##                  0

``` r
colnames(Feb_21)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Feb_21)
```

    ## spec_tbl_df [49,622 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:49622] "89E7AA6C29227EFF" "0FEFDE2603568365" "E6159D746B2DBB91" "B32D3199F1C2E75B" ...
    ##  $ rideable_type     : chr [1:49622] "classic_bike" "classic_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:49622], format: "2021-02-12 16:14:56" "2021-02-14 17:52:38" ...
    ##  $ ended_at          : POSIXct[1:49622], format: "2021-02-12 16:21:43" "2021-02-14 18:12:09" ...
    ##  $ start_station_name: chr [1:49622] "Glenwood Ave & Touhy Ave" "Glenwood Ave & Touhy Ave" "Clark St & Lake St" "Wood St & Chicago Ave" ...
    ##  $ start_station_id  : chr [1:49622] "525" "525" "KA1503000012" "637" ...
    ##  $ end_station_name  : chr [1:49622] "Sheridan Rd & Columbia Ave" "Bosworth Ave & Howard St" "State St & Randolph St" "Honore St & Division St" ...
    ##  $ end_station_id    : chr [1:49622] "660" "16806" "TA1305000029" "TA1305000034" ...
    ##  $ start_lat         : num [1:49622] 42 42 41.9 41.9 41.8 ...
    ##  $ start_lng         : num [1:49622] -87.7 -87.7 -87.6 -87.7 -87.6 ...
    ##  $ end_lat           : num [1:49622] 42 42 41.9 41.9 41.8 ...
    ##  $ end_lng           : num [1:49622] -87.7 -87.7 -87.6 -87.7 -87.6 ...
    ##  $ member_casual     : chr [1:49622] "member" "casual" "member" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Feb_21))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##               4046               4046               5358               5358 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                214                214 
    ##      member_casual 
    ##                  0

``` r
colnames(Mar_21)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Mar_21)
```

    ## spec_tbl_df [228,496 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:228496] "CFA86D4455AA1030" "30D9DC61227D1AF3" "846D87A15682A284" "994D05AA75A168F2" ...
    ##  $ rideable_type     : chr [1:228496] "classic_bike" "classic_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:228496], format: "2021-03-16 08:32:30" "2021-03-28 01:26:28" ...
    ##  $ ended_at          : POSIXct[1:228496], format: "2021-03-16 08:36:34" "2021-03-28 01:36:55" ...
    ##  $ start_station_name: chr [1:228496] "Humboldt Blvd & Armitage Ave" "Humboldt Blvd & Armitage Ave" "Shields Ave & 28th Pl" "Winthrop Ave & Lawrence Ave" ...
    ##  $ start_station_id  : chr [1:228496] "15651" "15651" "15443" "TA1308000021" ...
    ##  $ end_station_name  : chr [1:228496] "Stave St & Armitage Ave" "Central Park Ave & Bloomingdale Ave" "Halsted St & 35th St" "Broadway & Sheridan Rd" ...
    ##  $ end_station_id    : chr [1:228496] "13266" "18017" "TA1308000043" "13323" ...
    ##  $ start_lat         : num [1:228496] 41.9 41.9 41.8 42 42 ...
    ##  $ start_lng         : num [1:228496] -87.7 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:228496] 41.9 41.9 41.8 42 42.1 ...
    ##  $ end_lng           : num [1:228496] -87.7 -87.7 -87.6 -87.6 -87.7 ...
    ##  $ member_casual     : chr [1:228496] "casual" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Mar_21))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##              14848              14848              16727              16727 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                167                167 
    ##      member_casual 
    ##                  0

``` r
colnames(Apr_21)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Apr_21)
```

    ## spec_tbl_df [337,230 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:337230] "6C992BD37A98A63F" "1E0145613A209000" "E498E15508A80BAD" "1887262AD101C604" ...
    ##  $ rideable_type     : chr [1:337230] "classic_bike" "docked_bike" "docked_bike" "classic_bike" ...
    ##  $ started_at        : POSIXct[1:337230], format: "2021-04-12 18:25:36" "2021-04-27 17:27:11" ...
    ##  $ ended_at          : POSIXct[1:337230], format: "2021-04-12 18:56:55" "2021-04-27 18:31:29" ...
    ##  $ start_station_name: chr [1:337230] "State St & Pearson St" "Dorchester Ave & 49th St" "Loomis Blvd & 84th St" "Honore St & Division St" ...
    ##  $ start_station_id  : chr [1:337230] "TA1307000061" "KA1503000069" "20121" "TA1305000034" ...
    ##  $ end_station_name  : chr [1:337230] "Southport Ave & Waveland Ave" "Dorchester Ave & 49th St" "Loomis Blvd & 84th St" "Southport Ave & Waveland Ave" ...
    ##  $ end_station_id    : chr [1:337230] "13235" "KA1503000069" "20121" "13235" ...
    ##  $ start_lat         : num [1:337230] 41.9 41.8 41.7 41.9 41.7 ...
    ##  $ start_lng         : num [1:337230] -87.6 -87.6 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:337230] 41.9 41.8 41.7 41.9 41.7 ...
    ##  $ end_lng           : num [1:337230] -87.7 -87.6 -87.7 -87.7 -87.7 ...
    ##  $ member_casual     : chr [1:337230] "member" "casual" "casual" "member" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_character(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_character(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Apr_21))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##              26056              26056              28174              28174 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                267                267 
    ##      member_casual 
    ##                  0

``` r
#create list of all dfs

df_list <- list(May_20, Jun_20, Jul_20, Aug_20, Sep_20, Oct_20, Nov_20, Dec_20, Jan_21, Feb_21,Mar_21, Apr_21 )

##Define a function to get variable names and types
my_function_1 <- function(data_frame){
  require(dplyr)
  x <- tibble(`var_name` = colnames(data_frame),
              `var_type` = sapply(data_frame, class))
  return(x)
}

#storing the result in a separate df

col_verification <- lapply(1:length(df_list),function(i)my_function_1(df_list[[i]]) %>% 
mutate(element =i)) %>%
  bind_rows() %>%
  spread(element, var_type)

col_verification 
```

    ## # A tibble: 13 x 13
    ##    var_name  `1`    `2`    `3`   `4`   `5`   `6`   `7`   `8`   `9`   `10`  `11` 
    ##    <chr>     <list> <list> <lis> <lis> <lis> <lis> <lis> <lis> <lis> <lis> <lis>
    ##  1 end_lat   <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  2 end_lng   <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  3 end_stat~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  4 end_stat~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  5 ended_at  <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  6 member_c~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  7 ride_id   <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  8 rideable~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ##  9 start_lat <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ## 10 start_lng <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ## 11 start_st~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ## 12 start_st~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ## 13 started_~ <chr ~ <chr ~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~ <chr~
    ## # ... with 1 more variable: 12 <list>

``` r
# to directly get just the mismatching columns

compare_df_cols(df_list, return = "mismatch")
```

    ##        column_name df_list_1 df_list_2 df_list_3 df_list_4 df_list_5 df_list_6
    ## 1   end_station_id   numeric   numeric   numeric   numeric   numeric   numeric
    ## 2 start_station_id   numeric   numeric   numeric   numeric   numeric   numeric
    ##   df_list_7 df_list_8 df_list_9 df_list_10 df_list_11 df_list_12
    ## 1   numeric character character  character  character  character
    ## 2   numeric character character  character  character  character

\##Looks like the columns start station id and end station id have
different data types in the 2020 vs the 2022 data, lets correct them and
maintain a single data type.

\##Having eliminated any incongruencies, lets now merge the data

``` r
#changing the data type from  integer  to character for start_station_id & end_station_id for dfs - Jun_20 - Dec_20

May_20 <- May_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Jun_20 <- Jun_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Jul_20 <- Jul_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Aug_20 <- Aug_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Sep_20 <- Sep_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Oct_20 <- Oct_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Nov_20 <- Nov_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

Dec_20 <- Dec_20 %>% mutate(start_station_id = as.character(start_station_id))%>% mutate(end_station_id = as.character(end_station_id))

#merging data by rows
Annual_data <- rbind(May_20, Jun_20,Jul_20,Aug_20,Sep_20,Oct_20,Nov_20, Dec_20,Jan_21,Feb_21,Mar_21,Apr_21)
```

\##We will recheck the NAs and data types

``` r
str(Annual_data)
```

    ## spec_tbl_df [3,742,202 x 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:3742202] "02668AD35674B983" "7A50CCAF1EDDB28F" "2FFCDFDB91FE9A52" "58991CF1DB75BA84" ...
    ##  $ rideable_type     : chr [1:3742202] "docked_bike" "docked_bike" "docked_bike" "docked_bike" ...
    ##  $ started_at        : POSIXct[1:3742202], format: "2020-05-27 10:03:52" "2020-05-25 10:47:11" ...
    ##  $ ended_at          : POSIXct[1:3742202], format: "2020-05-27 10:16:49" "2020-05-25 11:05:40" ...
    ##  $ start_station_name: chr [1:3742202] "Franklin St & Jackson Blvd" "Clark St & Wrightwood Ave" "Kedzie Ave & Milwaukee Ave" "Clarendon Ave & Leland Ave" ...
    ##  $ start_station_id  : chr [1:3742202] "36" "340" "260" "251" ...
    ##  $ end_station_name  : chr [1:3742202] "Wabash Ave & Grand Ave" "Clark St & Leland Ave" "Kedzie Ave & Milwaukee Ave" "Lake Shore Dr & Wellington Ave" ...
    ##  $ end_station_id    : chr [1:3742202] "199" "326" "260" "157" ...
    ##  $ start_lat         : num [1:3742202] 41.9 41.9 41.9 42 41.9 ...
    ##  $ start_lng         : num [1:3742202] -87.6 -87.6 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:3742202] 41.9 42 41.9 41.9 41.8 ...
    ##  $ end_lng           : num [1:3742202] -87.6 -87.7 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:3742202] "member" "casual" "casual" "casual" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
colSums(is.na(Annual_data))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##             148231             148857             171317             171778 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0               4906               4906 
    ##      member_casual 
    ##                  0

### Looks like except for the latitute and longitude columns all other columns have character type vectors. Also, there are missing values in start and end station id for over 150,000 trips which will have be to looked into. The missing values in latitute and longitude columns are not an issue as we will not be using them in this analysis.

\#Step 2: Wrangling the data

### As the data and time are combined into same columns, we will need indvidual columns for date, time, and time differnce between trips to calculte the length of each ride. Also, we need to obtain specific day of the week, month and date of the rides as well.

``` r
#create new col with just the dates

Annual_data2 <- Annual_data %>% mutate(start_date = as.Date(started_at)) %>% mutate (end_date = as.Date(ended_at))

# individual cols for month, date, year and week of the day

Annual_data2 <- Annual_data2 %>% mutate(month_trip = format(as.Date(start_date), "%b")) %>% mutate(day_trip = format(as.Date(start_date), "%d")) %>% mutate(year_trip = format(as.Date(start_date), "%Y")) %>% mutate(day_of_week = format(as.Date(start_date), "%A")) %>% mutate(month_year = paste (month_trip, " ", year_trip))

#calculating the ride lengths in hours

Annual_data2 <- Annual_data2 %>% mutate(ride_length = round(difftime(ended_at, started_at, units = "hours"), digits = 2))

#converting the ride length in factors to numeric
Annual_data2 <- Annual_data2 %>% mutate(ride_length = as.numeric(as.character(ride_length)))


#extracting time into separate column

Annual_data2 <- Annual_data2 %>% mutate(start_time = format(started_at, "%T"))

#extracting start time (just the hour) into separate column

Annual_data2 <- Annual_data2 %>% mutate(start_time_hrs = format(started_at, "%H"))
#creating categorical variable for time of the day

Annual_data2 <- Annual_data2 %>% mutate(time_cat = cut(times(start_time) , breaks = (1/24) * c(0,5,12,16,19,24), 
    labels = c("past_midnight", "morning", "afternoon", "evening", "night")))

Annual_data2 <- Annual_data2 %>% filter(time_cat != "NA")

str(Annual_data2)
```

    ## spec_tbl_df [3,742,190 x 24] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ ride_id           : chr [1:3742190] "02668AD35674B983" "7A50CCAF1EDDB28F" "2FFCDFDB91FE9A52" "58991CF1DB75BA84" ...
    ##  $ rideable_type     : chr [1:3742190] "docked_bike" "docked_bike" "docked_bike" "docked_bike" ...
    ##  $ started_at        : POSIXct[1:3742190], format: "2020-05-27 10:03:52" "2020-05-25 10:47:11" ...
    ##  $ ended_at          : POSIXct[1:3742190], format: "2020-05-27 10:16:49" "2020-05-25 11:05:40" ...
    ##  $ start_station_name: chr [1:3742190] "Franklin St & Jackson Blvd" "Clark St & Wrightwood Ave" "Kedzie Ave & Milwaukee Ave" "Clarendon Ave & Leland Ave" ...
    ##  $ start_station_id  : chr [1:3742190] "36" "340" "260" "251" ...
    ##  $ end_station_name  : chr [1:3742190] "Wabash Ave & Grand Ave" "Clark St & Leland Ave" "Kedzie Ave & Milwaukee Ave" "Lake Shore Dr & Wellington Ave" ...
    ##  $ end_station_id    : chr [1:3742190] "199" "326" "260" "157" ...
    ##  $ start_lat         : num [1:3742190] 41.9 41.9 41.9 42 41.9 ...
    ##  $ start_lng         : num [1:3742190] -87.6 -87.6 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num [1:3742190] 41.9 42 41.9 41.9 41.8 ...
    ##  $ end_lng           : num [1:3742190] -87.6 -87.7 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr [1:3742190] "member" "casual" "casual" "casual" ...
    ##  $ start_date        : Date[1:3742190], format: "2020-05-27" "2020-05-25" ...
    ##  $ end_date          : Date[1:3742190], format: "2020-05-27" "2020-05-25" ...
    ##  $ month_trip        : chr [1:3742190] "May" "May" "May" "May" ...
    ##  $ day_trip          : chr [1:3742190] "27" "25" "02" "02" ...
    ##  $ year_trip         : chr [1:3742190] "2020" "2020" "2020" "2020" ...
    ##  $ day_of_week       : chr [1:3742190] "Wednesday" "Monday" "Saturday" "Saturday" ...
    ##  $ month_year        : chr [1:3742190] "May   2020" "May   2020" "May   2020" "May   2020" ...
    ##  $ ride_length       : num [1:3742190] 0.22 0.31 1.62 0.23 0.62 0.79 0.92 0.76 0.32 0.5 ...
    ##  $ start_time        : chr [1:3742190] "10:03:52" "10:47:11" "14:11:03" "16:25:36" ...
    ##  $ start_time_hrs    : chr [1:3742190] "10" "10" "14" "16" ...
    ##  $ time_cat          : Factor w/ 5 levels "past_midnight",..: 2 2 3 4 3 3 3 4 4 2 ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   ride_id = col_character(),
    ##   ..   rideable_type = col_character(),
    ##   ..   started_at = col_datetime(format = ""),
    ##   ..   ended_at = col_datetime(format = ""),
    ##   ..   start_station_name = col_character(),
    ##   ..   start_station_id = col_double(),
    ##   ..   end_station_name = col_character(),
    ##   ..   end_station_id = col_double(),
    ##   ..   start_lat = col_double(),
    ##   ..   start_lng = col_double(),
    ##   ..   end_lat = col_double(),
    ##   ..   end_lng = col_double(),
    ##   ..   member_casual = col_character()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

\##Lets select only columns needed for further analysis and perform
basic summary statistics based on the member type (casual vs membership
riders)

``` r
Annual_data3 <- Annual_data2 %>% select(- c(start_lat, start_lng, end_lat, end_lng))

#renaming the rideable type and member_casual columns for easier understanding

Annual_data3 <- Annual_data3 %>% rename(ride_type = rideable_type,  membership_type = member_casual )

summary(Annual_data3)
```

    ##    ride_id           ride_type           started_at                 
    ##  Length:3742190     Length:3742190     Min.   :2020-05-01 00:02:07  
    ##  Class :character   Class :character   1st Qu.:2020-07-23 19:27:14  
    ##  Mode  :character   Mode  :character   Median :2020-09-09 15:51:13  
    ##                                        Mean   :2020-10-03 00:35:51  
    ##                                        3rd Qu.:2020-11-15 17:49:27  
    ##                                        Max.   :2021-04-30 23:59:53  
    ##     ended_at                   start_station_name start_station_id  
    ##  Min.   :2020-05-01 00:13:03   Length:3742190     Length:3742190    
    ##  1st Qu.:2020-07-23 19:59:58   Class :character   Class :character  
    ##  Median :2020-09-09 16:08:31   Mode  :character   Mode  :character  
    ##  Mean   :2020-10-03 01:00:18                                        
    ##  3rd Qu.:2020-11-15 18:05:29                                        
    ##  Max.   :2021-05-05 22:14:39                                        
    ##  end_station_name   end_station_id     membership_type      start_date        
    ##  Length:3742190     Length:3742190     Length:3742190     Min.   :2020-05-01  
    ##  Class :character   Class :character   Class :character   1st Qu.:2020-07-23  
    ##  Mode  :character   Mode  :character   Mode  :character   Median :2020-09-09  
    ##                                                           Mean   :2020-10-02  
    ##                                                           3rd Qu.:2020-11-15  
    ##                                                           Max.   :2021-04-30  
    ##     end_date           month_trip          day_trip          year_trip        
    ##  Min.   :2020-05-01   Length:3742190     Length:3742190     Length:3742190    
    ##  1st Qu.:2020-07-23   Class :character   Class :character   Class :character  
    ##  Median :2020-09-09   Mode  :character   Mode  :character   Mode  :character  
    ##  Mean   :2020-10-02                                                           
    ##  3rd Qu.:2020-11-15                                                           
    ##  Max.   :2021-05-05                                                           
    ##  day_of_week         month_year         ride_length         start_time       
    ##  Length:3742190     Length:3742190     Min.   :-484.1700   Length:3742190    
    ##  Class :character   Class :character   1st Qu.:   0.1300   Class :character  
    ##  Mode  :character   Mode  :character   Median :   0.2400   Mode  :character  
    ##                                        Mean   :   0.4076                     
    ##                                        3rd Qu.:   0.4400                     
    ##                                        Max.   : 904.7200                     
    ##  start_time_hrs              time_cat      
    ##  Length:3742190     past_midnight:  89017  
    ##  Class :character   morning      : 876653  
    ##  Mode  :character   afternoon    :1059875  
    ##                     evening      :1054710  
    ##                     night        : 661935  
    ## 

``` r
Annual_data3%>% filter(ride_length < 0)
```

    ## # A tibble: 3,802 x 20
    ##    ride_id   ride_type started_at          ended_at            start_station_na~
    ##    <chr>     <chr>     <dttm>              <dttm>              <chr>            
    ##  1 DD903077~ docked_b~ 2020-05-30 16:55:14 2020-05-30 16:54:55 Wentworth Ave & ~
    ##  2 CF73228D~ docked_b~ 2020-05-20 09:44:47 2020-05-20 09:44:19 Clarendon Ave & ~
    ##  3 4244D2EE~ docked_b~ 2020-05-13 03:01:51 2020-05-13 03:00:32 Indiana Ave & 26~
    ##  4 60FE7C6D~ docked_b~ 2020-05-15 21:20:32 2020-05-15 21:20:03 Spaulding Ave & ~
    ##  5 CB5F3B26~ docked_b~ 2020-05-08 06:59:29 2020-05-08 06:58:58 Rush St & Hubbar~
    ##  6 D40633CA~ docked_b~ 2020-05-14 19:41:50 2020-05-14 19:40:02 Western Ave & Di~
    ##  7 369DF9CF~ docked_b~ 2020-05-28 16:53:46 2020-05-28 16:53:27 Western Ave & Di~
    ##  8 BC1D096C~ docked_b~ 2020-05-11 09:19:09 2020-05-11 09:18:37 Broadway & Barry~
    ##  9 B0483582~ docked_b~ 2020-05-19 16:09:59 2020-05-19 16:09:30 Michigan Ave & 1~
    ## 10 7E2349CC~ docked_b~ 2020-05-11 07:10:39 2020-05-11 07:10:06 Wells St & Everg~
    ## # ... with 3,792 more rows, and 15 more variables: start_station_id <chr>,
    ## #   end_station_name <chr>, end_station_id <chr>, membership_type <chr>,
    ## #   start_date <date>, end_date <date>, month_trip <chr>, day_trip <chr>,
    ## #   year_trip <chr>, day_of_week <chr>, month_year <chr>, ride_length <dbl>,
    ## #   start_time <chr>, start_time_hrs <chr>, time_cat <fct>

\###There were 3802 rows with negative values in the ride length, these
indicate rides in which th bike company removed the bikes from the docks
for quality checks and did not return to the docking stations. Hence
these negative values were removed from the data.

``` r
Annual_data3 <-  Annual_data3 %>% filter(ride_length >= 0.00 )
```

\##Creating summary tables to access ride lengths and ride counts to
access the riding trends and storing results in indvidual tables for
further analysis.

### Rider type vs ride length summary

``` r
Membership_vs_ridetype <- Annual_data3 %>% group_by(membership_type, ride_type) %>% summarise(mean(ride_length), max(ride_length), min(ride_length))
```

    ## `summarise()` has grouped output by 'membership_type'. You can override using the `.groups` argument.

``` r
Membership_vs_ridetype
```

    ## # A tibble: 6 x 5
    ## # Groups:   membership_type [2]
    ##   membership_type ride_type  `mean(ride_lengt~ `max(ride_lengt~ `min(ride_lengt~
    ##   <chr>           <chr>                  <dbl>            <dbl>            <dbl>
    ## 1 casual          classic_b~             0.521            26                   0
    ## 2 casual          docked_bi~             0.853           905.                  0
    ## 3 casual          electric_~             0.357             8.01                0
    ## 4 member          classic_b~             0.243            26                   0
    ## 5 member          docked_bi~             0.281           688.                  0
    ## 6 member          electric_~             0.224             8.01                0

``` r
                                                                                              write_csv(Membership_vs_ridetype,"Membership_vs_ridetype.csv")
```

### Rider type total number of rides based on days of the week

``` r
Membership_vs_dayofweek <- Annual_data3 %>% group_by(membership_type, day_of_week) %>% summarise(number_of_rides = n(), average_duration = mean(ride_length)) %>% 
  arrange(desc(number_of_rides),.by_group = TRUE)
```

    ## `summarise()` has grouped output by 'membership_type'. You can override using the `.groups` argument.

``` r
Membership_vs_dayofweek
```

    ## # A tibble: 14 x 4
    ## # Groups:   membership_type [2]
    ##    membership_type day_of_week number_of_rides average_duration
    ##    <chr>           <chr>                 <int>            <dbl>
    ##  1 casual          Saturday             359390            0.763
    ##  2 casual          Sunday               281445            0.829
    ##  3 casual          Friday               229299            0.697
    ##  4 casual          Thursday             176547            0.687
    ##  5 casual          Wednesday            168826            0.664
    ##  6 casual          Monday               164732            0.731
    ##  7 casual          Tuesday              162214            0.655
    ##  8 member          Saturday             341729            0.291
    ##  9 member          Friday               335325            0.259
    ## 10 member          Wednesday            324179            0.252
    ## 11 member          Thursday             319901            0.248
    ## 12 member          Tuesday              307635            0.247
    ## 13 member          Monday               287489            0.253
    ## 14 member          Sunday               279677            0.295

``` r
write_csv(Membership_vs_dayofweek,"Membership_vs_dayofweek")
```

\##Earlier we saw that both start and end station names and id columns
had NAs, below table shows that most of these belong to riders with
electric bikes. We need further details regarding if riders were to
directly drop off/pick up a bike from a charging station, results in a
missing value in the station name and id

``` r
colSums(is.na(Annual_data3))
```

    ##            ride_id          ride_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##             148182             148808             171248             171709 
    ##    membership_type         start_date           end_date         month_trip 
    ##                  0                  0                  0                  0 
    ##           day_trip          year_trip        day_of_week         month_year 
    ##                  0                  0                  0                  0 
    ##        ride_length         start_time     start_time_hrs           time_cat 
    ##                  0                  0                  0                  0

``` r
Missing_data <- Annual_data3 %>% select(start_station_name, start_station_id, end_station_name, end_station_id, ride_type, membership_type) %>% group_by(membership_type, ride_type) %>%
  summarize(start_station_name= sum(is.na(start_station_name)),
            end_station_name = sum(is.na(end_station_name)),
            start_station_id =sum(is.na(start_station_id)),
              end_station_id = sum( is.na(end_station_id)))
```

    ## `summarise()` has grouped output by 'membership_type'. You can override using the `.groups` argument.

``` r
Missing_data
```

    ## # A tibble: 6 x 6
    ## # Groups:   membership_type [2]
    ##   membership_type ride_type   start_station_n~ end_station_name start_station_id
    ##   <chr>           <chr>                  <int>            <int>            <int>
    ## 1 casual          classic_bi~                0              642                0
    ## 2 casual          docked_bike                0             1926                0
    ## 3 casual          electric_b~            56918            68768            57272
    ## 4 member          classic_bi~                0             1107                0
    ## 5 member          docked_bike                0             2144                0
    ## 6 member          electric_b~            91264            96661            91536
    ## # ... with 1 more variable: end_station_id <int>

``` r
write_csv(Missing_data, "Missing_data.csv")
```

\###Finding the most famous/frequently visited stations

``` r
Start_st_data <- Annual_data3 %>% filter(start_station_name != "NA") %>% group_by( start_station_name) %>% summarise(number_of_rides = n(), average_duration = mean(ride_length)) %>%
  arrange(desc(number_of_rides)) %>% head(n =20)

Start_st_data
```

    ## # A tibble: 20 x 3
    ##    start_station_name             number_of_rides average_duration
    ##    <chr>                                    <int>            <dbl>
    ##  1 Streeter Dr & Grand Ave                  38507            0.751
    ##  2 Clark St & Elm St                        34167            0.343
    ##  3 Lake Shore Dr & Monroe St                33534            0.760
    ##  4 Theater on the Lake                      32188            0.509
    ##  5 Lake Shore Dr & North Blvd               28984            0.558
    ##  6 Wells St & Concord Ln                    27222            0.321
    ##  7 Millennium Park                          26725            1.06 
    ##  8 Indiana Ave & Roosevelt Rd               26114            0.680
    ##  9 Broadway & Barry Ave                     25480            0.345
    ## 10 Dearborn St & Erie St                    25476            0.383
    ## 11 Wells St & Elm St                        25234            0.355
    ## 12 Clark St & Armitage Ave                  25206            0.368
    ## 13 Michigan Ave & Oak St                    24344            0.675
    ## 14 Wells St & Huron St                      24126            0.307
    ## 15 Clark St & Lincoln Ave                   24001            0.408
    ## 16 Columbus Dr & Randolph St                23591            0.517
    ## 17 Wabash Ave & Grand Ave                   22981            0.561
    ## 18 St. Clair St & Erie St                   22762            0.465
    ## 19 Lake Shore Dr & Wellington Ave           22563            0.462
    ## 20 Kingsbury St & Kinzie St                 22073            0.285

``` r
write_csv(Start_st_data, "Start_st_data.csv")


End_st_data <- Annual_data3 %>% filter(end_station_name != "NA") %>% group_by(end_station_name) %>% summarise(number_of_rides = n(), average_duration = mean(ride_length)) %>%
  arrange(desc(number_of_rides)) %>% head(n =20)

End_st_data 
```

    ## # A tibble: 20 x 3
    ##    end_station_name               number_of_rides average_duration
    ##    <chr>                                    <int>            <dbl>
    ##  1 Streeter Dr & Grand Ave                  40537            0.712
    ##  2 Clark St & Elm St                        33952            0.374
    ##  3 Theater on the Lake                      33690            0.557
    ##  4 Lake Shore Dr & Monroe St                32713            0.714
    ##  5 Lake Shore Dr & North Blvd               29492            0.563
    ##  6 Millennium Park                          27960            0.711
    ##  7 Wells St & Concord Ln                    27742            0.300
    ##  8 Broadway & Barry Ave                     26119            0.348
    ##  9 Dearborn St & Erie St                    25977            0.349
    ## 10 Indiana Ave & Roosevelt Rd               25573            0.609
    ## 11 Michigan Ave & Oak St                    24982            0.615
    ## 12 St. Clair St & Erie St                   24904            0.377
    ## 13 Wabash Ave & Grand Ave                   24011            0.491
    ## 14 Clark St & Lincoln Ave                   23903            0.416
    ## 15 Wells St & Elm St                        23885            0.267
    ## 16 Clark St & Armitage Ave                  23719            0.389
    ## 17 Wabash Ave & Roosevelt Rd                23610            0.501
    ## 18 Lake Shore Dr & Wellington Ave           22988            0.450
    ## 19 Wells St & Huron St                      22727            0.278
    ## 20 Larrabee St & Webster Ave                22230            0.312

``` r
write_csv(End_st_data, "End_st_data.csv")
```

#### Rider type vs number of rides / week/ month

``` r
#calculate number of trips on a given day in a week per month

Ride_cnt_month <- Annual_data3 %>% group_by(day_of_week, month_year, membership_type) %>% summarise(total_trip_per_day = n())
```

    ## `summarise()` has grouped output by 'day_of_week', 'month_year'. You can override using the `.groups` argument.

``` r
Ride_cnt_month
```

    ## # A tibble: 168 x 4
    ## # Groups:   day_of_week, month_year [84]
    ##    day_of_week month_year membership_type total_trip_per_day
    ##    <chr>       <chr>      <chr>                        <int>
    ##  1 Friday      Apr   2021 casual                       22929
    ##  2 Friday      Apr   2021 member                       35795
    ##  3 Friday      Aug   2020 casual                       39240
    ##  4 Friday      Aug   2020 member                       46081
    ##  5 Friday      Dec   2020 casual                        3460
    ##  6 Friday      Dec   2020 member                       12401
    ##  7 Friday      Feb   2021 casual                        1496
    ##  8 Friday      Feb   2021 member                        6594
    ##  9 Friday      Jan   2021 casual                        2838
    ## 10 Friday      Jan   2021 member                       12645
    ## # ... with 158 more rows

``` r
write_csv(Ride_cnt_month, "Ride_cnt_month.csv")
```

\##Step3: Exporting data for further analysis

``` r
#exporting the cleaned dataframe as csv file for visual analysis in Tableau
write_csv(Annual_data3, "Annual_data3.csv")
```
