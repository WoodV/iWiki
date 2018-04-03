**Change font size of labels:**

~~~r
#ps: fontsize, las=1, labels are always horizontal
par(ps = 5, cex=1, cex.lab=1, las=1)
~~~

**Select random training subset:**

~~~r
#it creates a vector in len(dataset) with random T and F. Total T is numTrain.
train = sample(1:nrow(dataset), numTrain)
trainSet = dataset[train,]
~~~

**use existing model to predict**
