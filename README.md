# [first draft]
![galaxy more avatar 2](https://user-images.githubusercontent.com/131216170/233606301-2af476b4-842d-469d-b849-4245eadd6ac4.png)

notebook link:
https://www.kaggle.com/code/tyeestudio/language-from-outer-space-in-icecube-data

# abstract [what]
gpt is mainly for language model, to prediction next word(s) in sequence. however, this notebook shows the [datasets] from the iceCube Neutrino Observatory may contain language-like [structures], after using gpt to predict neutrino particle’s direction.

# introduction [why]
<li>because of consistency of how <font color='orange'><b>prediction pattern</b></font> of reaching to <font color='orange'><b>[0]</b></font> angular-dist-score from multiple different datasets (see train-test-split).  </li>
<li>the nature of gpt is unsupervised learning. </li>
<li>total of 688898 characters, size of <b>unique</b> chars is <font color='orange'><b>12</b></font>, actual unique chars are <font color='orange'><b>[' ', '.', '1', '2', '3', '4', '5', '6', '7', '8', '9', '0'] </b></font></li>
    
# methods [how]

<li> define input context
    <div style='font-size:9px;'>X_train_sample_df['text'] = ' ' + X_train_sample_df['event_id'].astype(str) + ' ' + X_train_sample_df['charge_sc'].astype(str)  + ' ' + X_train_sample_df['auxiliary_num'].astype(str) + ' ' + X_train_sample_df['time_sc'].astype(str)  + ' ' + X_train_sample_df['x_sc'].astype(str)  + ' ' + X_train_sample_df['y_sc'].astype(str) + ' ' + X_train_sample_df['z_sc'].astype(str)  + ' ' + X_train_sample_df['azimuth_sc'].astype(str) + ' ' + X_train_sample_df['zenith_sc'].astype(str) + ' '</div>
    
<li> configure the model parameters </li>
<li> create an model training injection callback function </li>
<li> load data from different batch files </li>
<li> create a gpt based model </li>
<li> feed input context into model trainer</li>
<li> monitoring loss and prediction result (angular_dist_score) from callback during the trainer run </li>

# results

<div>
iter_dt 71.12ms; <font color='orange'><b>iter 1350</b></font>: train loss 0.56368
input_context  778000508 0.388702 0 , reversed  0.9249987306885454
output_context:  778000508 0.388702 0 0.473239 0.443972 0.432305 0.474399 0.482462 0.286377   719430412
target event_id: 778000508

target 
    <font color='orange'><b>azimuth: 0.482462, zenith: 0.286377</b></font>
</br>
predicted
    <font color='orange'><b>azimuth: 0.482462, zenith: 0.286377</b></font>
</br>    
predict_zenith_reverse 0.7540110701466416, redict_azimuth_reverse 3.3472593432077193
check if both are float True
angular_dist_score(az_true, zen_true, az_pred, zen_pred)3.3472593432077193, 0.7540110701466416, 3.3472593432077193, 0.7540110701466416
</br>
<font color='orange'><b>progress_rec </b></font>{'iter_id': 1350, 'target_event_id': 778000508, 'target_azimuth': 0.482462, 'target_zenith': 0.286377, 'reverse target_azimuth': 3.3472593432077193, 'reverse target_zenith': 0.7540110701466416, 'predict_azimuth': '0.482462', 'predict_zenith': '0.286377', 'reverse_predict_charge': 0.9249987306885454, 'reverse_predict_azimuth': 3.3472593432077193, 'reverse_predict_zenith': 0.7540110701466416, <font color='orange'><b>'score': 0.0</b></font>}
</div>

**[more] in log shows the pattern**
https://github.com/tyeestudio/language-structure-in-iceCube-Neutrino-data-/blob/main/training.and.prediction.log.txt

# appendix

* IceCube - Neutrinos in Deep Ice Reconstruct the direction of neutrinos from the Universe to the South Pole https://www.kaggle.com/competitions/icecube-neutrinos-in-deep-ice
* minGPT https://github.com/karpathy/minGPT
* first published notebook for showing the result https://www.kaggle.com/code/tyeestudio/gpt-based-prediction-no-chatgpt
* then, watch it learn in this notebook https://www.kaggle.com/code/tyeestudio/gpt-based-prediction-watch-it-learn  
* show with graph https://www.kaggle.com/code/tyeestudio/gpt-based-prediction-live-loss-plot    
