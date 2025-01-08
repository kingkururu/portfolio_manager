# Compiler and linker flags
CXX = g++
CXXFLAGS = -std=c++17 -Wall 

# Homebrew library paths (customizable via environment variables)
HOMEBREW_PREFIX ?= /opt/homebrew
SFML_INCLUDE ?= $(HOMEBREW_PREFIX)/include
SFML_LIB ?= $(HOMEBREW_PREFIX)/lib

# Add SFML include path dynamically
CXXFLAGS += -I$(SFML_INCLUDE)

# Linker flags for SFML
LDFLAGS = -L$(SFML_LIB) -lsfml-graphics -lsfml-window -lsfml-system -lsfml-audio

# Source files and target
SRC = main.cpp 
OBJ = $(SRC:.cpp=.o)
TARGET = run

# Build target
all: $(TARGET)

$(TARGET): $(OBJ)
	$(CXX) $(CXXFLAGS) -o $(TARGET) $(OBJ) $(LDFLAGS)

# Rule to build object files
%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

# Clean up
clean:
	rm -f $(TARGET) $(OBJ)

# Print message if SFML or Homebrew isn't installed
check_env:
	@if [ ! -d "$(HOMEBREW_PREFIX)" ]; then \
		echo "Homebrew not found! Install it from https://brew.sh"; \
	elif [ ! -d "$(SFML_LIB)" ]; then \
		echo "SFML not found! Install it using Homebrew: brew install sfml"; \
	fi
