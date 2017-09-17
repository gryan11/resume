filename = resume
outfile = GabrielRyanResume.pdf

all: 
	xelatex $(filename)
	cp $(filename).pdf $(outfile)

clean:
		rm -f $(filename).{ps,pdf,log,aux,out,dvi,bbl,blg}
