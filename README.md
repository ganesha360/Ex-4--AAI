<H3>KANISHKAR M</H3>
<H3>212222240044</H3>
<H3>EX. NO.4</H3>
<H3>DATE:14.03.2024</H3>
<H1 ALIGN =CENTER> Implementation of Hidden Markov Model</H1>

## Aim: 
Construct a Python code to find the sequence of hidden states by the known sequence of observances using Hidden Markov Model. Consider two hidden states Sunny and Rainy with observable states,happy and sad.

## Algorithm:

Step 1:Define the transition matrix, which specifies the probability of transitioning from  one hidden state to another.<br>
Step 2:Define the emission matrix, which specifies the probability of observing each possible observation given each hidden state.<br>
Step 3:Define the initial probabilities, which specify the probability of starting in each possible hidden state.<br>
Step 4:Define the observed sequence, which is the sequence of observations need to  be analyzed.<br>
Step 5:Initialize the alpha matrix with zeros, where each row represents a time step and each column represents a possible hidden state.<br>
Step 6:Calculate the first row of the alpha matrix by multiplying the initial  probabilities by the emission probabilities for the first observation.<br>
Step 7:Loop through the rest of the observed sequence and calculate the rest of the alpha matrix by multiplying the emission probabilities by the sum of the product of 
       the previous row of the alpha matrix and the corresponding row of the transition matrix.<br>
Step 8:Calculate the probability of the observed sequence by summing the last row of the alpha matrix.<br>
Step 9:Find the most likely sequence of hidden states by selecting the hidden state with the highest probability at each time step based on the alpha matrix.<br>

## Program:
```
import numpy as np
t_m = np.array([[0.7,0.3],
                [0.4, 0.6]])
e_m = np.array([[0.1,0.9],
                [0.8,0.2]])
i_p = np.array([0.5,0.5])

o_s = np.array([1,1,1,0,0,1])

alpha = np.zeros((len(o_s),len(i_p)))

alpha[0, :] = i_p * e_m[:, o_s[0]]

for t in range(1, len(o_s)):

  for j in range(len(i_p)):

    alpha[t, j ] = e_m[j,o_s[t]] * np.sum(alpha[t-1, :] * t_m[:, j ])

prob = np.sum(alpha[-1, :])

print("The Probability of the observed sequence is :",prob)

m_l_s = []
for t in range(len(o_s)):
  if alpha[t, 0] > alpha[t,1]:
    m_l_s.append("sunny")
  else:
    m_l_s.append("rainy")  

print("Thye most likely sequence of weather states is :",m_l_s)

```

## Output:

![image](https://github.com/KANISHKAR2607/Ex-4--AAI/assets/118886772/909ed463-f3dd-4d6a-8694-790ddae56070)


![image](https://github.com/KANISHKAR2607/Ex-4--AAI/assets/118886772/9ab7bbcf-0614-4ee7-b1be-93257ebef540)


## Result:
Thus Hidden Markov Model is implemented using python.

