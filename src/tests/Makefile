CC=gcc
LDLIBS=../bitcloud.a `pkg-config --libs sqlite3`
INCLUDES=-I..
CFLAGS=-Wall -ansi `pkg-config --cflags sqlite3`

run_tests_and_clean: clean run_tests

run_tests: tests
	@echo -- STARTING TESTS --
	./tests
	@echo -- ALL TESTS PASSED --

logs:
	sqlite3 nodepool "select * from logs"

tests: main.c logs.c ../bitcloud.a
	$(CC) -o $@ $< $(INCLUDES) $(LDLIBS) $(CFLAGS)

clean:
	rm -f tests nodepool
