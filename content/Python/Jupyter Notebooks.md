- Use the Anaconda version for now
- Importing everything from a library (as in `from fastai.vision.all import *`) is ok because Jupyter Notebooks is made to handle it and imports only needed pieces into the environment.
- Use `??` to get quick documentation of functions – example: `??verify_images` returns:
```
Signature: verify_images(fns)

Source:

def verify_images(fns):

"Find images in `fns` that can't be opened"

return L(fns[i] for i,o in

enumerate(parallel(verify_image, fns)) if not o)

File: ~/git/fastai/fastai/vision/utils.py

Type: function
```
- make sure to work in a [[Virtual Environments |Virtual Environment]]