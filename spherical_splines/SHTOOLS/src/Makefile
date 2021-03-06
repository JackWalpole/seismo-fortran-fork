######################################################################
#
#	make all
#		Compile program in the current directory. Optionally, one
#		can specify the parameters F95="my compiler" and 
#		F95FLAGS="my compiler flags". The default is to use "f95".
#
#	make all2
#		Compile program in the current directory. Optionally, one
#		can specify the parameters F95="my compiler" and 
#		F95FLAGS="my compiler flags". LAPACK subroutine names have
#		an underscore appended to them in the source code in order to use 
#		FFTW and LAPACK libraries with conflicting underscore conventions. 
# 		The default is to use "f95".
#
#	make all3
#		Compile program in the current directory. Optionally, one
#		can specify the parameters F95="my compiler" and 
#		F95FLAGS="my compiler flags". FFTW subroutine names have
#		an underscore appended to them in the source code in order to use 
#		FFTW and LAPACK libraries with conflicting underscore conventions. 
# 		The default is to use "f95".
#
#	make clean
#		Remove the lib and module files in the LOCAL directory.
#
#
#	Written by Mark Wieczorek (July 2006).
#
#######################################################################

SHELL=/bin/tcsh

F95 = f95

ifeq ($(F95),f95)
	# Default Absoft Pro Fortran flags
	#F95FLAGS ?= -O3 -YEXT_NAMES=LCS
	#F95FLAGS ?= -O3 -YEXT_NAMES=LCS -YEXT_SFX=_
	F95FLAGS ?= -O3 -YEXT_NAMES=LCS -YEXT_SFX=_ -m64
endif

ifeq ($(F95),g95)
	# Default g95 flags
	#F95FLAGS ?= -O3 -fno-underscoring
	F95FLAGS ?= -O3 -fno-second-underscore
	#F95FLAGS ?= -O3 -fno-second-underscore -m64
endif


LIBTOOL = libtool
LIBTOOLFLAGS = -static
AR = ar
ARFLAGS = -rcs
RLIB = ranlib
RLIBFLAGS =
LDFLAGS = -s
MAKE = make


PROG =	../lib/libSHTOOLS2.6.a

SRCS0 =	CilmPlus.f95 ComputeD0.f95 ComputeDG82.f95 ComputeDm.f95 DHaj.f95 \
	djpi2.f95 FFTW3.f95 Hilm.f95 MakeGrid2D.f95 \
	GLQGridCoord.f95 MakeGridPoint.f95 \
	MakeMagGrid2D.f95 PlanetsConstants.f95 PlBar.f95 PlBar_d1.f95 \
	PLegendre.f95 PLegendreA.f95 PLegendreA_d1.f95 PlmBar.f95 \
	PlmBar_d1.f95 PlmIndex.f95 PlmSchmidt.f95 PlmSchmidt_d1.f95 \
	PlSchmidt.f95 PlSchmidt_d1.f95 PreGLQ.f95 Random.f95 \
	SHAdmitCorr.f95 SHBias.f95 SHBiasK.f95 SHConvertCoef.f95 \
	SHFindLWin.f95 SHLocalizedAdmitCorr.f95 SHMultiply.f95 \
	SHMultiTaperCSE.f95 SHMultiTaperSE.f95 SHPowerSpectra.f95 SHRead.f95 \
	SHReadJPL.f95 SHReturnTapersM.f95 SHRotateCoef.f95 \
	SHRotateRealCoef.f95 SHTOOLS.f95 SphericalCapCoef.f95 \
	Wigner3j.f95 wl.f95 SHRead2.f95 MakeGeoidGrid.f95 \
	MakeCircleCoord.f95 SHSjkPG0.f95  \
	SHReturnTapers.f95 SHSjkPG.f95 PlON.f95 PlON_d1.f95 \
	PlmON.f95 PlmON_d1.f95 MakeGravGrid2D.f95 SHConfidence.f95 SHMagPowerSpectra.f95 \
	SHPowerSpectraC.f95 SHBiasAdmitCorr.f95 SHCimToVector.f95 YilmIndex.f95 \
	ComputeDMap.f95 SHReturnTapersMap.f95 Curve2Mask.f95 MakeEllipseCoord.f95

OBJS0 =	CilmPlus.o ComputeD0.o ComputeDG82.o ComputeDm.o DHaj.o djpi2.o \
	FFTW3.o Hilm.o MakeGrid2D.o GLQGridCoord.o \
	MakeGridPoint.o MakeMagGrid2D.o PlanetsConstants.o PlBar.o PlBar_d1.o \
	PLegendre.o PLegendreA.o PLegendreA_d1.o PlmBar.o PlmBar_d1.o \
	PlmIndex.o PlmSchmidt.o PlmSchmidt_d1.o PlSchmidt.o PlSchmidt_d1.o \
	PreGLQ.o Random.o SHAdmitCorr.o SHBias.o SHBiasK.o SHConvertCoef.o  \
	SHFindLWin.o SHLocalizedAdmitCorr.o  \
	SHMultiply.o SHMultiTaperCSE.o SHMultiTaperSE.o SHPowerSpectra.o \
	SHRead.o SHReadJPL.o SHReturnTapersM.o SHRotateCoef.o \
	SHRotateRealCoef.o SHTOOLS.o SphericalCapCoef.o Wigner3j.o \
	wl.o SHRead2.o MakeGeoidGrid.o  \
	MakeCircleCoord.o SHSjkPG0.o SHReturnTapers.o SHSjkPG.o \
	PlON.o PlON_d1.o PlmON.o PlmON_d1.o MakeGravGrid2D.o \
	SHConfidence.o SHMagPowerSpectra.o \
	SHPowerSpectra.o SHBiasAdmitCorr.o SHCilmToVector.o \
	YilmIndex.o ComputeDMap.o SHReturnTapersMap.o Curve2Mask.o MakeEllipseCoord.o
	
SRCSLAPACK1 = EigValSym.f95 EigValVecSym.f95 EigValVecSymTri.f95 SHExpandLSQ.f95 SHMTDebias.f95  \
	SHMTVarOpt.f95 SHMTVarOpt0.f95
	
OBJSLAPACK1 = EigValSym.o EigValVecSym.o EigValVecSymTri.o SHExpandLSQ.o SHMTDebias.o \
	SHMTVarOpt0.o SHMTVarOpt.o

SRCSLAPACK2 = EigValSym2.f95 EigValVecSym2.f95 EigValVecSymTri2.f95 SHExpandLSQ2.f95 SHMTDebias2.f950 \
	SHMTVarOpt2.f95 SHMTVarOpt02.f95

OBJSLAPACK2 = EigValSym2.o EigValVecSym2.o EigValVecSymTri2.o SHExpandLSQ2.o SHMTDebias2.o \
	SHMTVarOpt02.o SHMTVarOpt2.o
	
SRCSFFTW1 = MakeGridDH.f95 MakeGridDHC.f95 MakeGridGLQ.f95 MakeGridGLQC.f95 PreCompute.f95 \
	ReadWisdom.f95 SHExpandDH.f95 SHExpandDHC.f95 SHExpandGLQ.f95 SHExpandGLQC.f95
	
OBJSFFTW1 = MakeGridDH.o MakeGridDHC.o MakeGridGLQ.o MakeGridGLQC.o PreCompute.o \
	ReadWisdom.o SHExpandDH.o SHExpandDHC.o SHExpandGLQ.o SHExpandGLQC.o

SRCSFFTW2 = MakeGridDH2.f95 MakeGridDHC2.f95 MakeGridGLQ2.f95 MakeGridGLQC2.f95 PreCompute2.f95 \
	ReadWisdom2.f95 SHExpandDH2.f95 SHExpandDHC2.f95 SHExpandGLQ2.f95 SHExpandGLQC2.f95
	
OBJSFFTW2 = MakeGridDH2.o MakeGridDHC2.o MakeGridGLQ2.o MakeGridGLQC2.o PreCompute2.o \
	ReadWisdom2.o SHExpandDH2.o SHExpandDHC2.o SHExpandGLQ2.o SHExpandGLQC2.o


ifeq ($(MAKECMDGOALS),all)
	SRCS = $(SRCS0) $(SRCSLAPACK1) $(SRCSFFTW1)
	OBJS = $(OBJS0) $(OBJSLAPACK1) $(OBJSFFTW1)
endif

ifeq ($(MAKECMDGOALS),all2)
	SRCS = $(SRCS0) $(SRCSLAPACK2) $(SRCSFFTW1)
	OBJS = $(OBJS0) $(OBJSLAPACK2) $(OBJSFFTW1)
endif

ifeq ($(MAKECMDGOALS),all3)
	SRCS = $(SRCS0) $(SRCSLAPACK1) $(SRCSFFTW2)
	OBJS = $(OBJS0) $(OBJSLAPACK1) $(OBJSFFTW2)
endif

all: $(PROG) 

all2: $(PROG)

all3: $(PROG)

$(PROG): $(OBJS) 
	@echo
	@echo Compilation of source files successful.
	@echo
	@rm -f $(PROG)
#	@$(LIBTOOL) $(LIBTOOLFLAGS) -o $(PROG) $(OBJS)
#	If you prefer to use libtool, uncomment the above line, and comment the two lines below (AR and RLIB)
	$(AR) $(ARFLAGS) $(PROG) $(OBJS) 
	$(RLIB) $(RLIBFLAGS) $(PROG) 
	@echo
	@echo Creation of static library successful.
#	@rm -f $(OBJS)
#	@mv -f *.mod ../modules/
	@cp -f *.mod ../modules/
	@echo Library and module files moved to ../lib and ../modules
	@echo
	@echo Archive successfully created


.PHONY: clean

clean:
	rm -f $(PROG)
	rm -f $(OBJS0) 
	rm -f $(OBJSLAPACK1) 
	rm -f $(OBJSLAPACK2) 
	rm -f $(OBJSFFTW1) 
	rm -f $(OBJSFFTW2) 
	rm -f *.mod 
	rm -f ../modules/*.mod


.SUFFIXES: $(SUFFIXES) .f95 


.f95.o:
	$(F95) -c $(F95FLAGS) $<
	


CilmPlus.o: SHTOOLS.o
ComputeD0.o: SHTOOLS.o
ComputeDm.o: SHTOOLS.o
Hilm.o: SHTOOLS.o
MakeGrid2D.o: SHTOOLS.o
GLQGridCoord.o: SHTOOLS.o
MakeGridGLQ.o: FFTW3.o SHTOOLS.o
MakeGridGLQ2.o: FFTW3.o SHTOOLS.o
MakeGridGLQC.o: FFTW3.o SHTOOLS.o
MakeGridGLQC2.o: FFTW3.o SHTOOLS.o
MakeGridDH.o: FFTW3.o SHTOOLS.o
MakeGridDH2.o: FFTW3.o SHTOOLS.o
MakeGridDHC.o: FFTW3.o SHTOOLS.o
MakeGridDHC2.o: FFTW3.o SHTOOLS.o
MakeGridPoint.o: SHTOOLS.o
MakeMagGrid2D.o: SHTOOLS.o
PreCompute.o: SHTOOLS.o
PreCompute2.o: SHTOOLS.o
SHAdmitCorr.o: SHTOOLS.o
SHBias.o: SHTOOLS.o
SHBiasK.o: SHTOOLS.o
SHDeltaX.o: SHTOOLS.o
SHExpandDH.o: FFTW3.o SHTOOLS.o
SHExpandDH2.o: FFTW3.o SHTOOLS.o
SHExpandDHC.o: FFTW3.o SHTOOLS.o
SHExpandDHC2.o: FFTW3.o SHTOOLS.o
SHExpandGLQ.o: FFTW3.o SHTOOLS.o
SHExpandGLQ2.o: FFTW3.o SHTOOLS.o
SHExpandGLQC.o: FFTW3.o SHTOOLS.o
SHExpandGLQC2.o: FFTW3.o SHTOOLS.o
SHExpandLSQ.o: SHTOOLS.o
SHExpandLSQ2.o: SHTOOLS.o
SHFindLWin.o: SHTOOLS.o
SHLocalizedAdmitCorr.o: SHTOOLS.o
SHMultiply.o: SHTOOLS.o
SHMultiTaperCSE.o: SHTOOLS.o
SHMultiTaperSE.o: SHTOOLS.o
SHReturnTapersM.o: SHTOOLS.o
SHReturnTapers.o : SHTOOLS.o
SHRotateRealCoef.o: SHTOOLS.o
SHSjkPG0.o: SHTOOLS.o
SHSjkPG.o: SHTOOLS.o
SphericalCapCoef.o: SHTOOLS.o
MakeGeoidGrid.o: SHTOOLS.o
SHMTVarOpt0.o : SHTOOLS.o
SHMTVarOpt.o : SHTOOLS.o
PLegendreA.o  : SHTOOLS.o
PLegendreA_d1.o : SHTOOLS.o
PlmBar.o : SHTOOLS.o
PlmBar_d1.o : SHTOOLS.o
PlmSchmidt.o : SHTOOLS.o
PlmSchmidt_d1.o : SHTOOLS.o
PlmON.0 : SHTOOLS.o
PlmON_d1.o : SHTOOLS.o
SHMTDebias.o : SHTOOLS.o
SHMTDebias2.o : SHTOOLS.o
MakeGravGrid2d.o : SHTOOLS.o
SHBiasAdmitCorr.o : SHTOOLS.o
ComputeDMap.o : SHTOOLS.o
SHReturnTapersMap.o : SHTOOLS.o
