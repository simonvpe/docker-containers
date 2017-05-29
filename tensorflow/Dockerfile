FROM tensorflow/tensorflow:latest-gpu

# Install dependencies
RUN apt-get update -y \
    && apt-get install -yqq libssl-dev git-core sudo \
    && apt-get clean

# Install needed python packages
RUN pip install keras             \
                pandas-datareader \
                quandl            \
		h5py              \
		git+https://github.com/tflearn/tflearn.git
