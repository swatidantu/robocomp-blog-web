# GSoC'20 RoboComp project: Human recognition (identification) using multi-modal perception system

11th June 2020
 
## Current updates on the project
 
We are mainly focusing on Face recognition and Gait recognition for multimodal human recognition. To choose which method works best for a particular modality we are going to focus on their generalizability. 

When  the  distribution  of  training  data  and  testing  data are  the  same,  the  face  matching  methods  mentioned  aboveare  effective.  However,  there  is  always  a  distribution  changeor  domain  shift  between  two  domains  that  can  degrade  the performance. Hence we require transfer learning.
  
For each method, I will train it on a large dataset and evaluate its result on a smaller dataset. Moreover I will also use transfer learning to see how methods adapt to new scenarious. 

Overall by conducting these experiments we should find which methods can be used for the multi-modal component. 


### Face Recognition 

I followed [this](!https://arxiv.org/pdf/1804.06655.pdf) survey paper to get insight of what needs to be done. Another [paper](!https://doi.org/10.1016/j.cviu.2019.102805) was also very helpful.  

1. Large dataset to train face recognition models:
  1. Megaface dataset => Large in terms of number of subjects, which is similiar to our case 
  2. Close test set / subject independant protocol  => (subjects in test set are not seen during training & a gallary must be created of the test images)
  3. LFW dataset for testing transfer learning  

2. Methods: 

  1. Arcface (1st) => Found code https://github.com/deepinsight/insightface#pretrained-models, https://github.com/qidiso/mobilefacenet-V2
  2. Cosface (2nd)  => https://github.com/yule-li/CosFace
  3. Mobifacenet (Fast for mobile devices) => Found Code, https://github.com/qidiso/mobilefacenet-V2
  4. Facenet (Previous SOTA) => Found code 
  5. Fisher-face (Old method)  => Found Code 
  6. GCN based methods  

3. Metrics to compute: 
  1. TAR 
  2. FRR
  3. Computation Time 

4. Experiments: 
  1. Results on Megaface 
  2. Results of transfer learning 
    1. Without fine tuning 
    2. With fine tuning  
  3. Test the the top 3 on real life video using face-recognition library for detection & alignment.  

### Silhoute Based Gait Analysis 

1. Gaiset: 
  1. Run gaitset on CASIA-B

2. GEI
  1. https://github.com/nikitaomare/Gait-Recognition




Shubh Maheshwari
