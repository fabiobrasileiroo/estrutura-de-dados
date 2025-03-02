# target : prerequisites
# <TAB>recipe
# Name of the project
PROJ_NAME = printy

# Find all .c files in the source folder
C_SOURCE = $(wildcard source/*.c)

# Create corresponding object files in the objects folder
OBJ = $(patsubst source/%.c, objects/%.o, $(C_SOURCE))

# Compiler and linker
CC = gcc

# Flags for the compiler
CC_FLAGS = -c -W -Wall -ansi -pedantic

# Default target
all: $(PROJ_NAME)

# Link all object files to create the final binary
$(PROJ_NAME): $(OBJ)
	@echo "Linking objects to build binary: $@"
	$(CC) $(OBJ) -o $(PROJ_NAME)
	@echo "Finished building binary: $@"

# Pattern rule to compile any .c file in source into an .o file in objects.
# The order-only prerequisite (after |) ensures the objects folder exists.
objects/%.o: source/%.c | objects
	@echo "Compiling $<..."
	$(CC) $(CC_FLAGS) $< -o $@

# Create the objects folder if it does not exist.
objects:
	mkdir -p objects

# Clean build files
clean:
	@echo "Cleaning up..."
	rm -rf objects $(PROJ_NAME)

.PHONY: all clean
