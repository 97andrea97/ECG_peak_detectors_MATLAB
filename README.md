# ECG_peak_detectors_MATLAB
This repo contains 3 independent algorithms for the detect the "R peaks" of ECG signals.
Each algorithm can be tested with 3 ECG signals. The third one is affected by a strong low frequency noise.

The 3 algorithm ideas are here resumed:

- peak_detector_derivative:
I compute the signal derivative approximation and I classify as peaks the points satisfying these conditions: 
derivative zero crossing & signal amplitude close to the absolute maximum value of the signal.

- peak_detector_index:
I scan the signal. I store the region of CONTIGUOUS SAMPLES ABOTHE THE
THRESHOLD. For each region I store the maximum. Those are the peaks.
(If two regions are too close bacause of high frequency noise, so they
must be merged because they actually belong to the same QRS complex).

- peak_detector_max:
This is an easy idea, but is not efficient.
The steps are these
1) Find the absolute maximum.
2) For sure this is a peak, so I store it.
3)Replace the sample of the peak and its neighbourhood with the
isoelectric value, in order to find another peak at the next iteration.
4) Repeat from one, until the maximum is above a certain threshold.
(The neighbourhood is not a fixed value. It depends on the maximum of the current iteration.
it's neighbourdood is defined by all the samples between it and the first left and right values
below the threshold).

