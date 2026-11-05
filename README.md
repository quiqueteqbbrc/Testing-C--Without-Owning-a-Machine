# Testing-C++-Without-Owning-a-Machine
To test a C++ code and make it run on any platform 

# .github/workflows/build.yml
name: build
on: [push]
jobs:
  build:
    strategy:
      matrix:
        os: [windows-latest, macos-latest, ubuntu-latest]
    runs-on: ${{ matrix.os }}
    steps:
      - uses: actions/checkout@v4
      - run: cmake -S . -B build
      - run: cmake --build build --config Release
