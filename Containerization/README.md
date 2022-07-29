# Containerization
## Project structure
Containerization/
|
|_ Dockerfile
|
|_ volume/ (a folder, put here an input_file for the Starspace + an output file must appear here after running the dockerfile)
|
|_ Readme.md
## Usage
1. build container
   ```bash
   docker build . -t starspace
   ```
2. run container
   ```bash
   docker run -v $(pwd)/volume:/app/volume starspace:latest ./value/{input_file}
   ```
   or
   ```bash
   docker run -v $(pwd)/volume:/app/volume starspace:latest
   ```
   with default input file ("./volume/starspace_input_file.txt")
