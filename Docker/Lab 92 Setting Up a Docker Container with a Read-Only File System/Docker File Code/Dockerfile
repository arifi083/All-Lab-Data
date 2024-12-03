FROM alpine:latest

# Create a directory and add a sample file
RUN mkdir /data && echo "This is a read-only test file" > /data/test.txt

# Set the working directory
WORKDIR /data

CMD ["sh"]
