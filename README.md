# ninfe
Numerical INner Filter Effect Corrector - NINFE
# by Tomislav Friganović, Davor Šakić and Tin Weitner

University of Zagreb, Faculty of Pharmacy and Biochemistry, Zagreb, Croatia.

Help from Mario Gabričević (discussion), Tino Šeba, Valentina Borko, and Robert Kerep (testing) is greatly appreciated. Please report all suggestion, changes, improvements, and usage to davor.sakic@pharma.unizg.hr. 

Finanancial support provided through Croatian Science Foundation grant no. UIP-2017-05-9537 "Glycosylation as a factor in the iron transport mechanism of human serum transferrin" GlyMech at University of Zagreb Faculty of Pharmacy and Biochemistry.

Introduction

This is a quick guide in using Numerical INner Filter Effect Corrector - NINFE. 
Although different methods are available for countering IFE, this method can be implemented into laboratory workflow with minimal hassle.

User guide

Necessary steps:

1) Determine the geometric parameter for the respective microplate reader and microplate type.
2) Measure fluorescence for known fluorophore concentration series to be used for NINFE calibaration. At least two fluorescence measurements at two different z-axis positions (z-positions) for the same sample in the microplate well are required.
3) Format calibration data table (see details below).
4) Run NINFE calibration routine to obtain optimal z-position combination and linear response parameters.
5) Measure fluorescence for samples with unknown fluorophore concentration at the determined optimal z-position combination.
6) Format concentration readout data table (see details below).
7) Run NINFE readout routine to retrieve unknown fluorophore concentrations. The NINFE calibration routine needs to be performed previously. Readout can be used multiple times while using the same calibration.
8) Click START AGAIN for another cycle.

Data formats (input/output)

Input format (calibration): <br>
c	z1	z2	z3	z4	z5 <br>
uM	14,000	15,000	16,000	17,000	18,000 <br>
1.0	10	12	14	16	18 <br>
5.0	50	60	70	80	90 <br>
10.0	100	120	140	160	180 <br>
15.0	150	180	210	240	270 <br>
20.0	200	240	280	320	360 <br>


Output format (calibration): <br>
ID	pair	F1	F2	conc1(1.0)	conc2(5.0)	conc3(10.0)	conc4(15.0)	conc5(20.0)	slope	intercept	r2	rmsre	steyx	LOD	%mErr	BBm/Pm	exp <br>
0	0	14,000	15,000	221.861	1,109.306	2,218.611	3,327.917	4,437.222	221.861	-0	1	0	NaN	NaN	-0	BBm	17 <br>
1	0	14,000	15,000	27.724	138.622	277.243	415.865	554.486	27.724	-0	1	0	0	0	0	Pm	5.593 <br>
2	1	14,000	16,000	0.012	0.06	0.12	0.179	0.239	0.012	-0	1	0	NaN	NaN	0	BBm	-20 <br>
3	1	14,000	16,000	21.656	108.281	216.562	324.844	433.125	21.656	0	1	0	0	0	0	Pm	2.297 <br>
*BBM = Black-box model, Pm = Parametric model <br>

Input format (readout): <br>

designation	z1	z2	z3	z4	z5 <br>
num	14,000	15,000	16,000	17,000	18,000 <br>
A1	10	12	14	16	18 <br>
B2	50	60	70	80	90 <br>
C3	100	120	140	160	180 <br>
D4	150	180	210	240	270 <br>
E5	200	240	280	320	360 <br>
*Designation = user-defined or sample-specific label, e.g. well position etc. <br>

Output format (readout): <br>

-Parametric model (Pm) <br>
 	F(15000)	F(16000)	Fcorrected Pm	conc Pm (uM) <br>
1	10	18	14.638	1 <br>
2	50	90	73.19	5 <br>
3	100	180	146.38	10 <br>
4	150	270	219.569	15 <br>
5	200	360	292.759	20 <br>

-Black-box model (BBm) <br>
 	F(15000)	F(17000)	Fcorrected BBm	conc BBm (uM) <br>
1	12	14	48.051	1 <br>
2	60	70	240.255	5 <br>
3	120	140	480.51	10 <br>
4	180	210	720.765	15 <br>
5	240	280	961.02	20 <br>

