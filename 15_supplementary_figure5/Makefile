RMDS := $(wildcard *.Rmd)
CORES=32

all: create_R_files_from_Rmds
	ls -1 *.R | xargs -P ${CORES} -I{} bash -c "R -f {} >{}.out 2>{}.err"

clean:
	rm -rf *.out *.err *_files

create_R_files_from_Rmds: clean
	for RMD in $(RMDS); do \
		echo $$RMD; \
		echo "library(knitr); purl('$$RMD')" | R --vanilla; \
	done
