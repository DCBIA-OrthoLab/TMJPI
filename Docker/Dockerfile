FROM ubuntu:latest

WORKDIR /app

RUN apt-get update && apt-get install -y \
    wget \
    zip \
	libxt6

RUN mkdir matlab_install matlab
RUN wget https://ssd.mathworks.com/supportfiles/downloads/R2020a/Release/3/deployment_files/installer/complete/glnxa64/MATLAB_Runtime_R2020a_Update_3_glnxa64.zip && \
    unzip MATLAB_Runtime_R2020a_Update_3_glnxa64.zip -d matlab_install
RUN /app/matlab_install/install -mode silent -agreeToLicense yes -destinationFolder /app/matlab
RUN rm -rf MATLAB_Runtime_R2020a_Update_3_glnxa64.zip && \
    rm -rf MATLAB_Runtime_R2020a_Update_3_glnxa64

RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/DSCI_train
RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/DSCI_predict
RUN chmod +x ./DSCI_train
RUN chmod +x ./DSCI_predict

RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/test_cl.csv 
RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/test_ct.csv
RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/train_bl.csv
RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/train_cl.csv
RUN wget https://github.com/winstonwzhang/TMJPI/releases/download/v1.4/train_ct.csv

ENV LD_LIBRARY_PATH=/app/matlab/v98/runtime/glnxa64:/app/matlab/v98/bin/glnxa64:/app/matlab/v98/sys/os/glnxa64:/app/matlab/v98/sys/opengl/lib/glnxa64
ENV PATH=/app:$PATH
