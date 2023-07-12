# 0 Mnist_calculator

Handwritten Arithmetic/mathematical symbols Recognition and Calculation

# 1 Repository structure

- `mnist+` : training dataset（16 kinds symbols:`mnist` dataset + `+ - * / ( )` symbols） and test dataset(handwritten Arithmetic)
- `train.ipynb`: train a model to classify 16 kinds of symbols, use `cnn-lstm` neural network
- `predict.ipynb`: to predict the handwritten Arithmetic in `test` file
- `singlePredict.ipynb`: to predict a single symbol, like a number. (recognition)
- `cnn-lstm.h5`: the weight file I trained, it performed well (not perfect....but ... I try my best)

# 2 Something I want to tell u

1. In `train.ipynb`, I use `cnn-lstm neural network`，but it is not so perfect, and make lots of incorrect, I hope you to improve this model and train your own model
2. In `prect.ipynb`, I use `Connected domain extraction` method to extract the black area in pictures. But you know the `division` sign (`÷`)contains three area. So I just extract the `-` area, and ignore the small dot in that sign,
and then, I cropped the image vertically to make sure the clipped picture contains the full sign. Finally I have to convert the picture into `28*28`, to fit the input of my model.

```python
# extract the black signs
    num_labels, labels, stats, centroids = cv2.connectedComponentsWithStats(binary_image, connectivity=8)

# create a list to save the area's locations 
    character_regions = []
    for i in range(1, num_labels):

        # for every sign area is a rectangle
        left = stats[i, cv2.CC_STAT_LEFT]
        top = stats[i, cv2.CC_STAT_TOP]
        width = stats[i, cv2.CC_STAT_WIDTH]
        height = stats[i, cv2.CC_STAT_HEIGHT]

        # ignore the dot of division(too small area)
        if width * height < 500:
            continue

        # crop vertically, keep the width I extract, and adjust the rectangle's height as same as the original picture
        top = 0
        height = binary_image.shape[0] - 1
        character_regions.append((left, top, width, height))  # append to the list
```


# 3 Any thing else

I am too lazy to conver the code annotation into English, But I think you can easily understand what I have done with my code. (may you need help from translate software or GPT). I am also welcome anyone to ask for me by my email (cjy0415@qq.com).

Or you can just post an issue.

thank u !!!
