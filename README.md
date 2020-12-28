# Original Documentation 
Check it here: [PyBoof](https://github.com/lessthanoptimal/PyBoof/)

# Why?
Since you might need to use this library in deployment, you will get an error: "ValueError: signal only works in main thread" because the lib is listening on cancel/close key. We will just disable this error by handling the exception thrown.

To start using the library simply install the latest stable version using pip
```bash
git clone https://github.com/FPEPOSHI/PyBoof pyboof-local
cd pyboof-local
./setup.py build
sudo ./setup.py install
```

# Supported Platforms

The code has been developed and tested on Ubuntu Linux 16.04.  Should work on any other Linux variant.  Might work on Mac OS and a slim chance of working on Windows.

# Examples

Examples are included with the source code.  You can obtain them by either checkout the source code, as described above, or browsing 
[github here](https://github.com/lessthanoptimal/PyBoof/tree/master/examples).  If you don't check out the source code you won't have example data and not
all of the examples will work.

To run any of the examples simply invoke python on the script

1. cd PyBoof/examples
2. python example_blur_image.py

Code for applying a Gaussian and mean spatial filter to an image and displays the results.
```Python
import numpy as np
import pyboof as pb

pb.init_memmap() # Use a faster memory copy. Sometimes required

original = pb.load_single_band('../data/example/outdoors01.jpg', np.uint8)

gaussian = original.createSameShape() # useful function which creates a new image of the
mean = original.createSameShape()     # same type and shape as the original

# Apply different types of blur to the image
pb.blur_gaussian(original, gaussian,radius=3)
pb.blur_mean(original, mean, radius=3)

# display the results in a single window as a list
image_list = [(original, "original"), (gaussian, "gaussian"), (mean, "mean")]
pb.swing.show_list(image_list, title="Outputs")

input("Press any key to exit")

```

# Dependencies

PyBoof depends on the following python packages.  They should be automatically installed

* py4j
* numpy
