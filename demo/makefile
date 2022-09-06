# Address-sanitizer library
ASAN_FLAGS := -lasan
ifneq ($(OS),Windows_NT)
	UNAME_S := $(shell uname -s)
	ifeq ($(UNAME_S),Darwin)
		# macOS requires different a flag
		ASAN_FLAGS := -fsanitize=address
	endif
endif

# gpmfdemo : GPMF_demo.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o
# 		gcc -o gpmfdemo GPMF_demo.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o $(ASAN_FLAGS)

all: gpmfdemo gpmfdemo_cori gpmfdemo_gyro gpmfdemo_accl gpmfdemo_gps

gpmfdemo : GPMF_demo_csv.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o
		gcc -o gpmfdemo GPMF_demo_csv.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o $(ASAN_FLAGS)

gpmfdemo_cori : GPMF_demo_csv_cori.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o
		gcc -o gpmfdemo_cori GPMF_demo_csv_cori.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o $(ASAN_FLAGS)

gpmfdemo_gyro : GPMF_demo_csv_gyro.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o
		gcc -o gpmfdemo_gyro GPMF_demo_csv_gyro.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o $(ASAN_FLAGS)

gpmfdemo_accl : GPMF_demo_csv_accl.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o
		gcc -o gpmfdemo_accl GPMF_demo_csv_accl.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o $(ASAN_FLAGS)
		
gpmfdemo_gps : GPMF_demo_csv_gps.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o
		gcc -o gpmfdemo_gps GPMF_demo_csv_gps.o GPMF_parser.o GPMF_utils.o GPMF_mp4reader.o GPMF_print.o $(ASAN_FLAGS)

# GPMF_demo.o : GPMF_demo.c
# 		gcc -g -c GPMF_demo.c
GPMF_demo_csv.o : GPMF_demo_csv.c
		gcc -g -c GPMF_demo_csv.c
GPMF_demo_csv_cori.o : GPMF_demo_csv_cori.c
		gcc -g -c GPMF_demo_csv_cori.c
GPMF_demo_csv_gyro.o : GPMF_demo_csv_gyro.c
		gcc -g -c GPMF_demo_csv_gyro.c
GPMF_demo_csv_accl.o : GPMF_demo_csv_accl.c
		gcc -g -c GPMF_demo_csv_accl.c
GPMF_demo_csv_gps.o : GPMF_demo_csv_gps.c
		gcc -g -c GPMF_demo_csv_gps.c
GPMF_mp4reader.o : GPMF_mp4reader.c ../GPMF_parser.h
		gcc -g -c GPMF_mp4reader.c
GPMF_print.o : GPMF_print.c ../GPMF_parser.h
		gcc -g -c GPMF_print.c
GPMF_parser.o : ../GPMF_parser.c ../GPMF_parser.h
		gcc -g -c ../GPMF_parser.c
GPMF_utils.o : ../GPMF_utils.c ../GPMF_utils.h
		gcc -g -c ../GPMF_utils.c
clean :
		rm gpmfdemo *.o
