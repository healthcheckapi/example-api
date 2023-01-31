FROM python

RUN mkdir /service
COPY ./ /service/recommendations/
WORKDIR /service/recommendations
RUN python -m pip install --upgrade pip
RUN python -m pip install -r requirements.txt
RUN python -m grpc_tools.protoc -I ../recommendations/protobufs --python_out=. \
           --grpc_python_out=. ../recommendations/protobufs/recommendations.proto

EXPOSE 50051/tcp
EXPOSE 443/tcp
EXPOSE 80/tcp
EXPOSE 9090/tcp
ENTRYPOINT ["python", "recommendations.py"]