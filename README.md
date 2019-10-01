# FM'2019

This repository contains the code to reproduce the results of the paper:

* Alexandros Evangelidis and David Parker. [Quantitative Verification of Numerical Stability for Kalman Filters](http://www.prismmodelchecker.org/bibitem.php?key=EP19). In Proc. 23rd International Symposium on Formal Methods (FM'19), volume 11800 of LNCS, pages 425-441, Springer, 2019.

The code provided here is a trimmed down version (ver. 1.0) of the original VerFilter code.

## To run the experiments:

- For Fig. 1.a.:

   - Change maxTime to 2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20
-  For Fig. 1.b.:
   - Change decPlaces to 4,5,6

- For Fig. 2.:
    - Scaling the matrix elements by a value of sigma^2_w except the last   one (e.g.(2,2)).
	
     - decPlaces=6 is set for this experiment. The results should be the following:
		
        937.108633829033 sigma2w = 0.2;
       
        869.626488758627 sigma2w = 0.3;
		
        801.473598029666 sigma2w = 0.4;
		
        732.564026884655 sigma2w = 0.5;
		
        662.796053100457 sigma2w = 0.6;
		
        592.04416712323 sigma2w = 0.7;
		
        520.137477630094 sigma2w = 0.8;
		
        446.864108654067 sigma2w = 0.9
		
        371.926991137375 sigma2w = 1;
		
        295.201231838841 sigma2w = 1.1;
		
        215.391223975074 sigma2w = 1.2;
		
        131.838892695357 sigma2w = 1.3;
		
        42.7354617246511 sigma2w = 1.4;

- For Table 3:
   - Set decPlaces=3 and maxTime=2,3 in the ConventionalKalmanFilterPrism's constructor:
   
   - Note that maxTime should change in the property specification as well.
   For example:
     ```java 
     ConventionalKalmanFilterPrism modelGen = new   ConventionalKalmanFilterPrism(2, 3, nd_proc_noise, nd_meas_noise, pm,mm, 3); 
     ```
     
     - Properties' result should be:
     
       R{"cond"}=? [I=2]: 5001.0, P=?[G "isPD"]: 1.0
     
       R{"cond"}=? [I=3]: 6.854101966249687, P=?[G "isPD"]: 1.0
	

  - Set decPlaces=3 and maxTime=2,3 in the SchmidtCarlsonFilterPrismPropC's constructor. For example:
     ```java 
	SchmidtCarlsonFilterPrismPropC modelGen = new SchmidtCarlsonFilterPrismPropC(2, 3, sigma2, dt, Gamma, nd_proc_noise, nd_meas_noise, pm, mm, 3); 
    ```
    - Properties' result should be:

	
      R{"cond"}=? [I=2]: 69.87499999999999, P=?[G "isPD"]: 1.0
	
      R{"cond"}=? [I=3]: 2.479506427024868,  P=?[G "isPD"]: 1.0
