FROM ubuntu:22.04

# Needed for Boost install not to hang up for indefinite time (checked experimentally)
ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

WORKDIR /app

# Install dependencies:
ARG BUILD_DEPS='tzdata \
		git \
        	make \
		build-essential \
		libboost-all-dev \
		'

RUN apt-get update && \
    apt-get install -yqq $BUILD_DEPS

# Clone startspace repo
RUN git clone https://github.com/facebookresearch/Starspace.git
    
RUN cd Starspace && \
    make && \
    cd ..

ENTRYPOINT ["./Starspace/starspace", "train", "-model", "./volume/modelSaveFile", "-trainFile"]
CMD ["./volume/starspace_input_file.txt"]
