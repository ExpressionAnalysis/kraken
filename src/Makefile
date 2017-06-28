CXX = g++
# CXXFLAGS = -std=c++0x -Wall -fopenmp  -DGZSTREAM_NAMESPACE=gz -O3 -I.
AR       = ar cr

PROGS = db_sort set_lcas classify make_seqid_to_taxid_map db_shrink

.PHONY: all install clean

all: $(PROGS)

install: $(PROGS)
	cp $(PROGS) $(KRAKEN_DIR)/

clean:
	rm -f $(PROGS) *.o *.a

db_shrink: libkraken.a db_shrink.o
	${CXX} ${CXXFLAGS} -o db_shrink db_shrink.o ${LDFLAGS}

db_sort: libkraken.a db_sort.o
	${CXX} ${CXXFLAGS} -o db_sort db_sort.o ${LDFLAGS}

set_lcas: libkraken.a set_lcas.o
	${CXX} ${CXXFLAGS} -o set_lcas set_lcas.o ${LDFLAGS}

classify: libkraken.a classify.o
	${CXX} ${CXXFLAGS} -o classify classify.o ${LDFLAGS}


make_seqid_to_taxid_map: quickfile.o

gzstream.o: gzstream.C gzstream.h
	${CXX} ${CXXFLAGS} -c -o gzstream.o gzstream.C

libkraken.a: krakendb.o quickfile.o krakenutil.o fqmapper.o seqreader.o gzstream.o
	${AR} libkraken.a krakendb.o krakenutil.o fqmapper.o seqreader.o quickfile.o gzstream.o

classify.o: classify.cpp 
	$(CXX) $(CXXFLAGS) -c classify.cpp

krakenutil.o: krakenutil.cpp krakenutil.hpp
	$(CXX) $(CXXFLAGS) -c krakenutil.cpp

krakendb.o: krakendb.cpp krakendb.hpp quickfile.hpp
	$(CXX) $(CXXFLAGS) -c krakendb.cpp

seqreader.o: seqreader.cpp seqreader.hpp quickfile.hpp gzstream.h
	$(CXX) $(CXXFLAGS) -c seqreader.cpp

quickfile.o: quickfile.cpp quickfile.hpp
	$(CXX) $(CXXFLAGS) -c quickfile.cpp

fqmapper.o: fqmapper.cpp fqmapper.hpp
	$(CXX) $(CXXFLAGS) -c fqmapper.cpp

