#### Types
1.**FP32**
This format contains **32 bits**, where **1** bit is for **sign**, **8** bits for **exponent** and **23** bits for **mantissa**
2.**FP16**
This format contains **16 bits**, where **1** bit is for **sign**, **5** bits for **exponent** and **10** bits for **mantissa**
3.**INT8**
Binary numbers from -128 to 127
4.**INT4**
Binary numbers from -8 to 7
5.**TF32**
This format contains **32 bits**, where **1** bit is for **sign**, **8** bits for **exponent** and **10** bits for **mantissa**. It has the same exponent as FP32 and mantissa as FP16. So it's more stable for inference on FP16.
6.**Bfloat16**
This format contains **16 bits**, where **1** bit is for **sign**, **8** bits for **exponent** and **7** bits for **mantissa**

#### Convert
1. Map ranges of different precision. At simplest, normalize range of higher precision to its maximum or minimum (or use percentile values). Then, multiply by the range of lower precision values
2. **Per-tensor** quantization (find min / max of the whole tensor and normalize)
3. **Per-channel** quantization (normalize each channel separately)
4. **Calibration dataset** use outputs of original model and optimize weights correctly. Should use a good dataset of data which will be in production
