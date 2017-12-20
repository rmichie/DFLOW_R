# DFLOW_R

R function to find the design flow, such as the 7Q10, based on methodology used 
in EPA's DFLOW with a modificaton to account for missing flow data or days with zero flow. 
If there is missing flow data in any particular water year, all data from that water 
year is not used as recommended by [EPA] [1] and applied in USGS's [SWSTAT] [2] program.

I have double checked that this function produces values consistent 
with DFLOW 3.1 (in cases without missing data), but there still may be areas 
of the code that need improvement. Use at your own risk.

[1]: https://www.epa.gov/waterdata/technical-support-dflow#xqy
[2]: https://water.usgs.gov/software/SWSTAT/

References:
+ https://www.epa.gov/waterdata/dflow
+ https://nepis.epa.gov/Exe/ZyPDF.cgi/30001JEH.PDF?Dockey=30001JEH.PDF

## Usage

```R
dflow(x, m, r, period.start, period.end, wy.start, wy.end)
```

`x` = Data frame where,
	col 1 = POSIXct date,
	col 2 = numeric daily mean flow

`m` = Flow averaging period in days

`R` = Return period in years

`period.start` = Optional. Character date defining the start of the 
				calculation period in format "yyyy-mm-dd".
				Default is the minimum date in x.

`period.end` = 	Optional. Character date defining the end of the 
				calculation period in format "yyyy-mm-dd". 
				Default is the maximum date in x.

`wy.start` = Optional. Character date (excluding year) that begins 
			the water year in format "mm-dd". 
			Default is "10-01"

`wy.end` = Optional. Character date (excluding year) that ends 
			the water year in format "mm-dd". 
			Default is "09-30".