# Real-ESRGAN-inference
This is an unofficial repository of a Real-ESRGAN model trained on custom dataset. This model shows better results on faces compared to the original version. It is also easier to integrate this model into your projects.

You can try it in [google colab](https://colab.research.google.com/drive/1YlWt--P9w25JUs8bHBOuf8GcMkx-hocP)

- Paper: [Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data](https://arxiv.org/abs/2107.10833)
- [Official github](https://github.com/xinntao/Real-ESRGAN)

### Installation

---

1. Clone repo

   ```bash
   git clone https://github.com/boomb0om/Real-ESRGAN-colab
   cd Real-ESRGAN-colab
   ```

2. Install requirements

   ```bash
   pip install -r requirements.txt
   ```

3. Download [pretrained weights](https://drive.google.com/drive/folders/16PlVKhTNkSyWFx52RPb2hXPIQveNGbxS) and put them into `weights/` folder

### Usage

---

Basic example:

```python
from realesrgan import RealESRGAN
from PIL import Image
import numpy as np

device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
print('device:', device)

model = RealESRGAN(device, scale=4)
model.load_weights('weights/RealESRGAN_x4.pth')

path_to_image = 'inputs/lr_image.jpg'
image = Image.open(path_to_image).convert('RGB')
sr_image = model.predict(image)
sr_image.save('results/sr_image.png')
```

