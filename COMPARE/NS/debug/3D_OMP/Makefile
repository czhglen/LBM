OUTPUT  :=main
FAST    :=-parallel -xHOST -O3 -static -ipo 
OMP     :=-openmp
DEBUG   :=-check -traceback
COMP    :=ifort

#COMP :=$(COMP) $(DEBUG)
#COMP :=$(COMP) $(OMP)
#COMP :=$(COMP) $(FAST)
COMP :=$(COMP) $(FAST) $(OMP)

HEAD = prmtr.o vrble.o
SUB  = condition.o collision.o streaming.o output.o

all:$(OUTPUT)

prmtr.o: prmtr.f90
	$(COMP) -c $<
vrble.o: vrble.f90 prmtr.o
	$(COMP) -c $<
condition.o: condition.f90 $(HEAD)
	$(COMP) -c $<
collision.o: collision.f90 $(HEAD)
	$(COMP) -c $<
streaming.o: streaming.f90 $(HEAD)
	$(COMP) -c $<
output.o: output.f90 $(HEAD)
	$(COMP) -c $<
$(OUTPUT): $(OUTPUT).f90 $(HEAD) $(SUB)
	$(COMP) $^ -o $@

clean:
	rm -rf $(OUTPUT) a.out lbm *.o *.mod restart.bin vtk data/* *.png *.d
swp:
	rm -rf .*.swp
