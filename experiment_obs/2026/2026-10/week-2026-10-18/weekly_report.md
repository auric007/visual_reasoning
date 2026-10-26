## My conclusion
Last week in the experiment I did with the VLM, initially the 4-class VLM was not working because the descriptions corresponding to others and background class are the same. The model just overfitted, in my opinion, and for all the stage 1 boxes it was giving an answer among the two classes: radar and missile. After that what happened? Instead of creating chain-of-thought data for all of the classes, I trained with a super simple SFT technique that will have to produce only one class: the class name. With that I didn't force myself to create CoT data for others and background because I don't have the time and the annotation capability to create diverse data for all the others and background. When I tested that the recall and precision were not that good. I said it is under a confusion matrix of this week that I will plot here. Now the task is to compare it with the YOLO stage 8 class detector: what was the overlap, for which classes and for which images are the recall and precision metrics the same, and where are they different? It will help me to integrate both the stages side by side. I have to work on:

- how to clean the dataset
- how I can efficiently train this VLM to produce a way better matrix than this
- how to prepare the dataset
- how to train again with better technique

We need to focus this week

### Last week confusion matrix
|Actual ↓ / Predicted →|Radar|Missile|Other|Background|
|---|---|---|---|---|
|Radar|**54**|24|17|0|
|Missile|6|**114**|66|9|
|Other|120|248|**1,817**|735|
|Background|95|72|521|**333**|

## About p_camo
	 Merging p_camo==yes instances of radar and missile into camo is not helping at all, training them under their parent class giving a way better results. The reason is not very known as of now, might be for radar and missile. for those p_camoed which are predicted under radar and missile, is because there feature/geomerty is obvious to model so just because they are placed here and model is overfitted on those platforms
	 - For evaluating these set of problems, there are several technique in deep learning community 