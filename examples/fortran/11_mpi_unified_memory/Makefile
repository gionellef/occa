PROJ_DIR := $(dir $(abspath $(lastword $(MAKEFILE_LIST))))

ifndef OCCA_DIR
  OCCA_DIR=$(PROJ_DIR)/../../..
endif
include $(OCCA_DIR)/scripts/Makefile


#---[ COMPILATION ]-------------------------------
all: main

%: %.f90
	@mkdir -p $(abspath $(dir $@))
	$(fCompiler) $(fCompilerFlags) -o $@ $^ $(flags) $(fPaths) $(fLinkerFlags)

clean:
	rm -rf $(PROJ_DIR)/main
#=================================================


#---[ RUN ]---------------------------------------
run: main
	mpiexec -np 2 $(PROJ_DIR)/main
#=================================================
