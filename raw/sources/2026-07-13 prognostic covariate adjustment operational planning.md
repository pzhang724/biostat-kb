From chat, 2026-07-13

Q: 如果真有trial的话怎么操作这件事儿，以及planning是怎么做的

A: Planning happens before the trial starts: the decision to use prognostic-score adjustment is written into the protocol/SAP, historical/external control-arm data (same population, endpoint, covariates) is assembled, and a prognostic model is trained and then FROZEN ("locked") on that historical data before any new-trial data exist — model architecture, covariates, training data, and freeze date/version are all documented ahead of time so nothing can be tuned to the new trial's outcome. Sample-size/power planning is done using the model's expected predictive accuracy on the historical data to project the precision gain (variance reduction), which is what determines how much smaller/more powered the trial can be.

During conduct: the trial collects the same baseline covariates the locked model needs; an independent, blinded team scores each new participant with the frozen model before unblinding — walled off from anyone with access to unblinded trial data, so the score can't be gamed.

At analysis: the pre-specified ANCOVA (treatment + the locked prognostic score, no re-fitting) is run as the primary analysis exactly as written in the SAP; a standard/unadjusted analysis is typically pre-specified alongside it as a consistency check. The core operational safeguard regulators care about is this "wall" — proof the model was frozen and documented before it ever touched the live trial's data.
