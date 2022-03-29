FROM ubuntu:21.10
ENV DEBIAN_FRONTEND noninteractive
ENV DEBCONF_NOWARNINGS yes
ENV TZ America/Los_Angeles
ENV HOME /home
WORKDIR /home
RUN set -x && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
    apt-get update && \
    apt-get install -yq apt-utils ca-certificates git cmake llvm-13 clang-13 lld-13 && \
    apt-get clean && \
    ln -s /usr/bin/lld-13 /usr/bin/lld && \
    ln -s /usr/bin/clang++-13 /usr/bin/clang++ && \
    ln -s /usr/bin/llvm-config-13 /usr/bin/llvm-config && \
    git clone https://github.com/fujita-y/ypsilon.git && \
    mkdir ypsilon/build && \
    cd ypsilon/build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    cmake --build . && \
    cmake --install .
CMD [ "ypsilon", "--r7rs" ]
