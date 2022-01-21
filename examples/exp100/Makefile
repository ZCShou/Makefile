target1: dep1
	@echo "target1: dep1"
target1: dep2
	@echo "target1: dep2"

dep1:
	@echo "dep1"

dep2:
	@echo "dep2"

target3: dep3 := dep1 dep2

target3:
	@echo "target3: $(dep3)"
# Makefile: ;