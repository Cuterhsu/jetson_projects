SHELL=/bin/bash -o pipefail
export CUDA_INSTALL_DIR=/usr/local/cuda
export CUDNN_INSTALL_DIR = /usr/local/cuda
SAMPLESDIR=samples
samples=sampleCharRNN sampleDynamicReshape sampleFasterRCNN sampleGoogleNet sampleINT8 sampleINT8API sampleMLP sampleMNIST sampleMNISTAPI sampleNMT sampleMovieLens sampleOnnxMNIST samplePlugin sampleUffPluginV2Ext sampleReformatFreeIO sampleSSD sampleUffMNIST sampleUffSSD trtexec
VERBOSE=1
export VERBOSE

.PHONY: all clean sampleMnist debug_sampleMnist test_all_release help
all: 
	cd $(SAMPLESDIR) && make
	
clean:
	cd $(SAMPLESDIR) && make clean
	
sampleMnist:
	samples=sampleMNIST
	cd $(SAMPLESDIR)/sampleMNIST; make 
	cd bin; ./sample_mnist

sampleNMT:
	samples=sampleNMT
	cd $(SAMPLESDIR)/sampleNMT; make
	cd bin; ./sample_nmt --data_writer=text

sampleMNISTAPI:
	samples=sampleMNISTAPI
	cd $(SAMPLESDIR)/sampleMNISTAPI; make 
	cd bin; ./sample_mnist_api

sampleOnnxMNIST:
	samples=sampleOnnxMNIST
	cd $(SAMPLESDIR)/sampleOnnxMNIST; make 
	cd bin; ./sample_onnx_mnist
	
sampleUffMNIST:
	samples=sampleUffMNIST
	cd $(SAMPLESDIR)/sampleUffMNIST; make 
	cd bin; ./sample_uff_mnist

sampleMovieLens:
	samples=sampleMovieLens
	cd $(SAMPLESDIR)/sampleMovieLens; make 
	cd bin; ./sample_movielens --verbose

sample_fasterRCNN:
	samples=sampleFasterRCNN
	cd $(SAMPLESDIR)/sampleFasterRCNN; make 
	cd bin; ./sample_fasterRCNN
	
sampleSSD:
	samples=sampleSSD
	cd $(SAMPLESDIR)/sampleSSD; make 
	cd bin; ./sample_ssd
	
sampleUffSSD:
	samples=sampleUffSSD
	cd $(SAMPLESDIR)/sampleUffSSD; make 
	cd bin; ./sample_uff_ssd

sampleINT8:
	samples=sampleINT8
	cd $(SAMPLESDIR)/sampleINT8; make 
	cd bin; ./sample_int8

sampleINT8API:
	samples=sampleINT8API
	cd $(SAMPLESDIR)/sampleINT8API; make 
	cd bin; ./sample_int8_api
	
debug_sampleMnist:
	cd $(SAMPLESDIR)/sampleMNIST && make test_debug
	
test_all_release:
	cd $(SAMPLESDIR) && make test_releases
	
help:
	echo "Sample building help menu."
	echo "Samples:"
	$(foreach sample,$(samples), echo "\t$(sample)" &&) :
	echo "\nCommands:"
	echo "\tall - build all samples."
	echo "\tclean - clean all samples."
	echo "\nVariables:"
	echo "\tTARGET - Specify the target to build for."
	echo "\tVERBOSE - Specify verbose output."
	echo "\tCUDA_INSTALL_DIR - Directory where cuda installs to."
