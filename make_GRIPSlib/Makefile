ORACLE_LIBS=/usr/lib/oracle/21/client64/lib
ORACLE_INCLUDE=/usr/include/oracle/21/client64

BOOST_1_74_INCLUDE=/usr/local/include/boost
QUANT_1_25_INCLUDE=/usr/local/include/QuantLib-1.25

LOG4CXX_0_13_INCLUDE=/usr/local/include/log4cxx
CRYPTOPP_8_7_0_INCLUDE=/usr/local/include/cryptopp

GRIPSdb_INCLUDE=/home/GRIPSdb

CXXFLAGS = -w -fPIC -std=c++17


OUT_LIB_DIR = ./lib
OBJ_DIR = ./obj
SRC_DIR = gl


INCLUDES = -I. \
	   -I$(ORACLE_INCLUDE) \
	   -I$(BOOST_1_74_INCLUDE) \
	   -I$(QUANT_1_25_INCLUDE) \
	   -I$(LOG4CXX_0_13_INCLUDE) \
	   -I$(CRYPTOPP_8_7_0_INCLUDE) \
	   -I$(GRIPSdb_INCLUDE)

LDFLAGS  = -L$(ORACLE_LIBS)

.PHONY : all
all: gripslib.so gripslib.a

CPP_FILES = $(shell find . -type f -name '*.cpp')
OBJ_FILES = $(patsubst ./$(SRC_DIR)/%.cpp, $(OBJ_DIR)/$(notdir %.o), $(CPP_FILES))


gripslib.so: $(OBJ_FILES)
	@mkdir -p $(OUT_LIB_DIR)
	$(CXX) -shared -o $(OUT_LIB_DIR)/$@ $^

gripslib.a: $(OBJ_FILES) 
	@mkdir -p $(OUT_LIB_DIR)
	ar cr $(OUT_LIB_DIR)/$@ $(OBJ_FILES)
	
$(OBJ_DIR)/%.o : $(SRC_DIR)/%.cpp
	@mkdir -p $(dir $@)
	$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@


.PHONY: clean
clean:
	rm -rf $(OBJ_DIR)	
	rm -rf $(OUT_LIB_DIR)
