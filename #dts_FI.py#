import sys
from classy import Class
chi1=16000.0
chi2=16000.0
#outputfile='cdm.txt'
outputfile='FI_16keV.txt'
rwarm=0.1
kmax=2000.0
redshift=0.0
hinput=0.6727
mncdm= [chi1,chi2]
omegancdm = [(1-rwarm)*0.1198, rwarm*0.1198] 
#omegancdm = [0.00001,0.00001]
Tncdm = [0.332 ,0.332]
Nbins=[2000,2000]
Npsdncdm = [1,1]
WDMsetting = {'N_ncdm':2 , 
'T_ncdm': str(Tncdm).strip('[]'),
'm_ncdm': str(mncdm).strip('[]'), 
'ncdm_fluid_approximation':3,
'omega_cdm':0.0,
'omega_b':0.02225,
'use_ncdm_psd_files':str(Npsdncdm).strip('[]'),
'omega_ncdm':str(omegancdm).strip('[]'),
'ncdm_psd_filenames': 'FIpd.txt,FIpd.txt', 
'h':hinput,
'n_s':0.954 ,
'sigma8':0.796 ,
'z_reio':8.5}
LambdaWDM = Class()
LambdaWDM.set(WDMsetting)
LambdaWDM .set({'output':'mPk',
'P_k_max_1/Mpc':kmax, 
'z_max_pk':5.0,
'ncdm_N_momentum_bins':str(Nbins).strip('[]')})
LambdaWDM.compute()
#for i in range(-30,11):
#    x=float(pow(10,i/10))
#    print([x/hinput,pow(hinput,3.0)*LambdaWDM.pk(x,redshift)])
with open(outputfile, 'w') as f:
    sys.stdout = f # Change the standard output to the file we created.
    for i in range(-600,600):
        x=float(pow(10,i/200))
        print('  '.join([str(x/hinput),str(pow(hinput,3.0)*LambdaWDM.pk(x,redshift))]))
