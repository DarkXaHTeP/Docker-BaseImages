FROM arm32v7/node:8.9.2-stretch

WORKDIR /build
COPY ../../qemu/qemu-arm-static /usr/bin/qemu-arm-static

RUN mkdir bcm2835 && cd bcm2835 \
    && curl http://www.airspayce.com/mikem/bcm2835/bcm2835-1.52.tar.gz -o bcm2835.tar.gz \
    && tar zxvf bcm2835.tar.gz -C ./ --strip-components=1 \
    && ./configure && make && make install \
    && cd /build && rm -rf ./bcm2835
