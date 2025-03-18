---
layout: post
title: Karplus–Strong string synthesis
date:   2023-02-12 10:34:23
math: true
categories: 
---


# Karplus–Strong string synthesis



## Kevin Karplus and Alex Strong:

Karplus–Strong is a method to synthesis the sound of a hammered or plucked string or some types of percussion. so simple algoritm to generate music sound.

There is very simple code to generate so nice sound. please look at this python code:

```
def KarplusStrong(nSamples, sampleRate, frequency):

    k = 0.995
    buf = np.array(np.random.rand(int(sampleRate/frequency)) - 0.5)
    samples = np.array([0]*nSamples, 'float32')
    for i in range(nSamples):
        samples[i] = buf[0]
        avg = k*0.5*(buf[0] + buf[1])
        buf[:-1] = buf[1:]
        buf[-1] = avg
    return (samples)
```


>One of the first musically useful physical models (dating from the early 1980s), the Karplus-Strong algorithm has proven quite effective at generating a variety of plucked-string sounds (acoustic and electric guitars, banjos, and kotos) and even drumlike timbres. *(ref: http://sites.music.columbia.edu)*


KS algoritm is like this:

$$Y_t = \frac{1}{2}*(Y_{t-p-1} - Y_{t-p})$$