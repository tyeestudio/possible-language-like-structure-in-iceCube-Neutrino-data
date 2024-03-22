#
Description
Goal of the Competition
#
The goal of this competition is to predict a neutrino particle’s direction. You will develop a model based on data from the "IceCube" detector, which observes the cosmos from deep within the South Pole ice.

Your work could help scientists better understand exploding stars, gamma-ray bursts, and cataclysmic phenomena involving black holes, neutron stars and the fundamental properties of the neutrino itself.

Context
One of the most abundant particles in the universe is the neutrino. While similar to an electron, the nearly massless and electrically neutral neutrinos have fundamental properties that make them difficult to detect. Yet, to gather enough information to probe the most violent astrophysical sources, scientists must estimate the direction of neutrino events. If algorithms could be made considerably faster and more accurate, it would allow for more neutrino events to be analyzed, possibly even in real-time and dramatically increase the chance to identify cosmic neutrino sources. Rapid detection could enable networks of telescopes worldwide to search for more transient phenomena.

Researchers have developed multiple approaches over the past ten years to reconstruct neutrino events. However, problems arise as existing solutions are far from perfect. They're either fast but inaccurate or more accurate at the price of huge computational costs.

The IceCube Neutrino Observatory is the first detector of its kind, encompassing a cubic kilometer of ice and designed to search for the nearly massless neutrinos. An international group of scientists is responsible for the scientific research that makes up the IceCube Collaboration.

By making the process faster and more precise, you'll help improve the reconstruction of neutrinos. As a result, we could gain a clearer image of our universe.



# 
is it possible the dataset is the proof of [language] from outer space
# 

![galaxy more avatar 2](https://user-images.githubusercontent.com/131216170/233606301-2af476b4-842d-469d-b849-4245eadd6ac4.png)

notebook link:
https://www.kaggle.com/code/tyeestudio/language-from-outer-space-in-icecube-data

# abstract [what]
gpt is mainly for language model, to prediction next word(s) in sequence. however, this notebook (and other very early open notebooks, see [appendix] ) shows the [datasets] from the iceCube Neutrino Observatory may contain <b>language-like [structures]</b>, after using gpt to predict neutrino particle’s direction.

# introduction [why]
the <b>primage use cases</b> for gpt based model is known for [languege] related dataset. for instance, text and images, these are language related, and the <b>[known true]</b> is, there are some <b>[logics] or [intelligent]</b> inside of human text, human created images. however, in this notebook (and other very early open notebooks, see [appendix] ), shows that <b>non-language-related</b> dataset from iceCube Neutrino Observatory, can be predicted in next sequence just like the [lauguage] can be predicted from gpt based model for the [next word], and because of:

<li>consistency of how <font color='orange'><b>prediction pattern</b></font> of reaching to <font color='orange'><b>[0.0]</b></font> angular-dist-score from multiple different datasets (see train-test-split).  </li>
<li>the nature of gpt is unsupervised learning. </li>
<li>total of 688898 characters, size of <b>unique</b> chars <font color='orange'><b>12</b></font>, actual unique chars <font color='orange'><b>[' ', '.', '1', '2', '3', '4', '5', '6', '7', '8', '9', '0'] </b></font></li>
<li>small number of iterations, the model shows strong prediction ability, which also means, less weights needed, and most importanly, it means some more strong NON-weight related <b>[logics] or [intelligent] in the struture, similar to language</b>.</li>
</br>
<b>leads to reverse prediction</b> of a dataset may have [language] struture inside.
    
# methods [how]

<li> define input context
    <div style='font-size:9px;'>X_train_sample_df['text'] = ' ' + X_train_sample_df['event_id'].astype(str) + ' ' + X_train_sample_df['charge_sc'].astype(str)  + ' ' + X_train_sample_df['auxiliary_num'].astype(str) + ' ' + X_train_sample_df['time_sc'].astype(str)  + ' ' + X_train_sample_df['x_sc'].astype(str)  + ' ' + X_train_sample_df['y_sc'].astype(str) + ' ' + X_train_sample_df['z_sc'].astype(str)  + ' ' + X_train_sample_df['azimuth_sc'].astype(str) + ' ' + X_train_sample_df['zenith_sc'].astype(str) + ' '</div>
    
<li> configure the model parameters </li>
<li> create an model training injection callback function </li>
<li> load data from different batch files </li>
<li> create a gpt based model </li>
<li> feed input context into model trainer</li>
<li> monitoring loss and prediction result (angular_dist_score) from callback during the trainer run </li>

<li> run 6300[production] iters </li>
<li> batch files from [ 1, 60, 111, 240, 222, 389, 433, 555, 618 ] </li>
<li> 9000[production]  rows of data </li>
<li> test data from train-test split </li>

# results
from this notebook, show the prediction can start to predict neutrino particle’s direction after 1350 iterations, and become consistant after 1700 iterations.
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

**[more] in log shows the <font color='orange'><b>prediction patterns</b></font>**

# appendix

* IceCube - Neutrinos in Deep Ice Reconstruct the direction of neutrinos from the Universe to the South Pole https://www.kaggle.com/competitions/icecube-neutrinos-in-deep-ice
* minGPT https://github.com/karpathy/minGPT
* first published notebook for showing the result https://www.kaggle.com/code/tyeestudio/gpt-based-prediction-no-chatgpt
* then, watch it learn in this notebook https://www.kaggle.com/code/tyeestudio/gpt-based-prediction-watch-it-learn  
* show with liveplot https://www.kaggle.com/code/tyeestudio/gpt-based-prediction-live-loss-plot    


# note
<li>this is an copy from my private notebook which has 77 versions.</li>
<li>because of each prediction takes about 0.3 seconds, this notebook timeout the submission</li>


