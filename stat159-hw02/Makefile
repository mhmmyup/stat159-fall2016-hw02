.PHONY: clean all data

all: report.pdf eda-output.txt regression.RData


data: 
	curl http://www-bcf.usc.edu/~gareth/ISL/Advertising.csv >> data/Advertising.csv


eda-output.txt: code/eda-script.R data/Advertising.csv
	Rscript code/eda-script.R

regression.RData: code/regression-script.R data/Advertising.csv
	Rscript code/regression-script.R

report.pdf: report/report.Rmd data/regression.RData images/scatterplot-tv-sales.png
	pandoc report/report.Rmd -s -o report/report.html

clean: report/report.pdf
	rm -f report/report.pdf