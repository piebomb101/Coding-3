# Coding-3 read me
James Gibbons-Macgregor Coding 3 Final Project

My project consists of three <1min videos featuring audio reactive visuals using my own music.

Demo Video 1 - Floorplans
https://youtu.be/gKOKBunKaso

Demo Video 2 - Microscope images
https://youtu.be/TKfyWySJZGI

Demo Video 3 - Textures and Abstract art blended
https://www.youtube.com/shorts/o3ojCgHOtrs 

# NOTE: 
please see Working LSD code (video 3) for an example of the code for video 3. The structure of the code is identical for the other videos but with different parameter values. All of the various configs from multiple videos are saved in this one colab notebook:
https://colab.research.google.com/drive/1y8IPK28BRWvy0-PpmV-TFzyNiN95WlrU#scrollTo=H1OB-5oZxV0y

# DEVELOPMENT AND CHALLENGES:
This project uses the Lucid Sonic Dreams (LSD) notebook by Mikael Fritz (https://github.com/mikaelalafriz/lucid-sonic-dreams). This turns StyleGAN2 models into audio reactive videos. Unfortunately I was unable to achieve any of the initial goals I set out to achieve with this notebook due to a number of errors. 

I first created a few test runs of LSD and experimented with the built in datasets and parameters. I gained an understanding of the methods used, and how the program uses percussive and harmonic amplitude to move through linear interpolations. I also experimented with creating some custom visual effects with the ‘skimage’ module. 

My first goal was to train my own styleGAN2 model for use with LSD. I trained my own model from a dataset of fingerprints (https://www.kaggle.com/datasets/ruizgara/socofing), and I successfully created a .pkl file (see fakes000029.jpg or download file here: https://drive.google.com/file/d/1-ZNBMR3-3yBC80vxuoq1_JA8N9UQmbj0/view?usp=sharing )

However every time I tried to run the model I would encounter errors from the ‘dnnlib’ module. Force updating had no effect. I tried multiple different notebooks for training the model and all raised the same error. I had to abandon this attempt. (see dnnlib error example)

I then attempted to using a modified version of LSD by Youtuber Nerdy Rodent (https://github.com/nerdyrodent/lucid-sonic-dreams). This uses StyleGAN2-ada-pytorch models. I was unable to get this to run via Anaconda due to a bug with downloading the ‘mega’ module. As I was not using this in my code I tried to remove any code relating to it from the main.py and init.py files but it would still throw an error saying the module was missing. (see mega error example)

I then tried to run this version of LSD via colab and this solved the ‘mega’ error. I again successfully created a .pkl file using a StyleGAN2-ada-pt training model and was able to get it to load and run the video generation function. But this time I was unable to get the actual video file to generate. The error was with the ImageIO module not recognizing the generated images as an array so it would not create the video. I tried to de-bug but hit a wall. I even contacted Nerdy Rodent himself via twitter and he advised that the issue was likely due to the latest versions of Imageio being incompatible with his code. (see imageio error)

After spending roughly 25 hours on trying to get the model to run and assistance from a number of CCI staff, I had to conclude that it would not be possible to use my own model. I would be better off just using the pre-trained ones and doing what I could to make them my own. 

I also attempted to create my own custom effects based on the example given in the LSD notebook. This uses the ‘skimage’ module. I was able to adjust the ‘swirl’ example to also work as a rotate function. Combining these two effects in opposite directions and adjusting the ‘mode’ parameter for the edges of the image array gave some very interesting effects. These use strength and amplitude values to create audio reactive movement. I attempted this with other ‘skimage.translation’ functions such as rescale and warp but was unable to find ways to integrate the audioreative values without errors or just bad looking effects.

I was however able to blend two models that I knew worked with LSD using this notebook (https://colab.research.google.com/drive/1qhSjGVXWyxKejqZY8nPcgXpKFFaJTE2J#scrollTo=OSFv1iNPolCy) by Justin Pinkley. These were the ‘textures’ as the low res and ‘modern art’ high res inputs. This gave a nice effect where the complex patterns of the textures had the blocky primary colour characteristics of the ‘modern art’ data set applied to them, creating a vibrant 
visual aesthetic.

# VIDEO CONFIG NOTES:
Video 1: Here the motion of the interpolation is linked to the harmonic amplitude of the audio due to the complex rhythm. The rotation and swirl effects are linked percussively but with low strength. The frames per minute is low to avoid the shapes becoming overly abstract, as is batch size. 

Video 2: Interpolation motion entirely harmonic amplitude controlled so gets very fast when bass is present. Heavy percussive rotate, swirl, flash and contrast effects. Low batch size for clarity.

Video 3: Motion and effects all percussive. Very large frames per minute so things get very abstract and varied. Batch size large for even more crazy patterns. 



# ML MUSIC:
The final of the 3 demo videos uses a piece of music I created by utilizing the RAVE audioencoder neural synth. I took the drum and lead synth lines of a short composition and applied various transfer models to them.

The ‘Darbouka’ drum model was applied to the entire drum pattern. The system being confused by multiple patterns within the drum loop created some very interesting polyrhythms that were layered with the original beat.

The first synth arpeggio was layered with the ‘dog’ model, the robotic barks creating a nice resonant noise sweep effect 

I wrote a second synth arpeggio with a sinewave but I replaced it entirely with the transfer output of the ‘speech’ model. This worked nicely on its own as a formant oscillator style synth. 



I noticed that these models do not work well or at all with very low pitches, or audio with any kind of reverb or delays. I also was limited to these models from the RAVE.js (https://caillonantoine.github.io/ravejs/) site as the VST versions of RAVE are currently not available for windows, so I could not load in my own. However, I’m excited to try this when possible. 

# CONCLUSION: 
To conclude, while I am fairly happy with the result I got I am frustrated that I was unable to really make the system my own. It is also limited by being quite slow to output the videos and not working in real time. Sinking such a large amount of time into this project and not achieving what I had intended was frustrating but I do think I have gained a good amount of knowledge of GANs and also python in general. 

I look forward to experimenting with more audio based ML and also animations within the ‘Disco diffusion’ notebook for future works. 

