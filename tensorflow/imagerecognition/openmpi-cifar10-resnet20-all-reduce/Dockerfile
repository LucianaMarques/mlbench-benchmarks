# ********************************** STAGE 2 **********************************************
# later we will use the remote ones
FROM mlbench/mlbench-tensorflow-base:1.1.0

# -------------------- Debug --------------------
RUN apt-get update && apt-get install -y vim net-tools dnsutils iputils-ping traceroute

# The reference implementation and user defined implementations are placed here.
ADD ./requirements.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

RUN mkdir /codes
ADD ./main.py /codes/main.py

ENV PYTHONPATH /codes

# To find `libnvidia-ml.so` on google cloud.
# ENV LD_LIBRARY_PATH="/usr/local/nvidia/lib64:$LD_LIBRARY_PATH"

EXPOSE 22222

# Remove empty ld
RUN rm $(ldconfig 2>&1 | grep 'is empty, not checked' | awk '{print $3}') 2> /dev/null || true