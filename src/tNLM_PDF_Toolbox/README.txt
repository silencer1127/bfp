README

tNLMPdf is a global PDF-based non-local means filtering method for fMRI dataset

Usage:

Function call:
[dataSm, output] = tNLMPdf(data, option);

data - a V x T matrix where V is the number of vertices and T is the number of time samples

option - optional parameters, call function without input parameter to obtain the default options, i.e. option = tNLMPdf();
	option.normalization - how to normalize the data after filtering
		0 - no normalization
		1 - zero mean (default)
		2 - zero mean and unit variance
	option.selfWeightMode - what weight is assigned to the data point that is being filtered
		0 - one
		1 - same as the second largest weight (default)
		2 - zero
	option.FPR - false positive rate regariding the noise distribution (default = 0.001)
	option.memoryLimit - specifiy the memory limit
		a positive number - memory limit in GB
		'auto' - try to detect available memory automatically (only works for Linux now)
	option.isPlot - binary flag indicating whether the weighting function and the distributions will be shown (default = false)
	option.isVerbose - binary flag indicating the verboseness of information printing
	option.SCBFile - a file that stores the sample correlation basis (default = SCB.mat in the current directory)

dataSm - filtered data

output - other intermediate result
	output.r - sample correlation axis
	output.h - optimized parameter h
	output.w - weights assigned to each r

also see demo.m for example

Note:
1. The input data for fMRI study should be concatenated data from both hemispheres
2. For each different length of fMRI recordings (T), the sample correlation basis needs to be re-pre-calculated once. This will take a while to finish


