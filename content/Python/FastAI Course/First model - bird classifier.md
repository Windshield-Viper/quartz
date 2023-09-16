This model identifies whether a given image is an image of a forest or a bird.

- training the model involves creating `DataLoaders`, objects that contain training and validation sets. The `DataLoaders` created by this model look like this:

![[Other/Images, Other Attachments/Pasted image 20230814153303.png| 500]]

```python
# to search ddg for training images
from duckduckgo_search import ddg_images

# keep in mind you can use import * in a notebook
from fastcore.all import *

# just ddg stuff to search images
def search_images(term, max_images=30):
    print(f"Searching for '{term}'")
    return L(ddg_images(term, max_results=max_images)).itemgot('image')

# use search_images to get some training images of birds (first one as a test)
# this sometimes returns a JSON error but if it does just run it again

urls = search_images('bird photos', max_images=1)
print(urls[0])

# download one of the images
from fastdownload import download_url
dest = 'bird.jpg'
download_url(urls[0], dest, show_progress=False)

# open the image in a 256 x 256 format
from fastai.vision.all import *
im = Image.open(dest)
im.to_thumb(256,256)

# do the same thing for forest photos
download_url(search_images('forest photos', max_images=1)[0], 'forest.jpg', show_progress=False)
Image.open('forest.jpg').to_thumb(256,256)

# create datasets using ddg

searches = 'forest','bird'
path = Path('bird_or_not')
from time import sleep

for o in searches:
    dest = (path/o)
    # bird photos stored in bird_or_not/bird, forest photos in bird_or_not/forest 
    dest.mkdir(exist_ok=True, parents=True)
    download_images(dest, urls=search_images(f'{o} photo'))
    sleep(10)  # Pause between searches to avoid over-loading server
    download_images(dest, urls=search_images(f'{o} sun photo'))
    sleep(10)
    download_images(dest, urls=search_images(f'{o} shade photo'))
    sleep(10)
    # resize the images
    resize_images(path/o, max_size=400, dest=path/o)

# destroy incorrectly downloaded images

failed = verify_images(get_image_files(path))
failed.map(Path.unlink)
print(len(failed))

# make datablock of the data we obtained
dls = DataBlock(
    # say that the inputs to our model are images and the outputs are categories
    blocks=(ImageBlock, CategoryBlock), 
    # get images using the get_image_files function
    get_items=get_image_files, 
    # split data into training and validation sets using a random splitter. 20% will be validation, and the psuedorandom seed is 42.
    splitter=RandomSplitter(valid_pct=0.2, seed=42),
    # the y (label of the data) is the parent of each file (the folder it's in)
    get_y=parent_label,
    # resize images using the "squish" method to 192x192
    item_tfms=[Resize(192, method='squish')]
).dataloaders(path, bs=32)

# (use dls.show_batch(max_n=6) to see your data)

# now we train the model.

# resnet18 is the fastest widely used CV model. fine_tune() comes with fastAI and should be used for best fine-tuning practices.
learn = vision_learner(dls, resnet18, metrics=error_rate)
# 3 epochs of fine-tuning, using a pre-trained model
learn.fine_tune(3)

# testing model on initial image
is_bird,_,probs = learn.predict(PILImage.create('bird.jpg'))
print(f"This is a: {is_bird}.")
print(f"Probability it's a bird: {probs[0]:.4f}")
```

