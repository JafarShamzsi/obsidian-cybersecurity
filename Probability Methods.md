### EXERCISE 7: Coin Flip Probabilities

#### Given:

- A coin is flipped 3 times.
- Outcomes for each flip: **Head (H)** or **Tail (T)**.
- The probability of getting a Head (P(H)) = 0.5, and the probability of getting a Tail (P(T)) = 0.5.
- Total possible outcomes for 3 flips = 23=82^3 = 823=8: {HHH,HHT,HTH,HTT,THH,THT,TTH,TTT}\{HHH, HHT, HTH, HTT, THH, THT, TTH, TTT\}{HHH,HHT,HTH,HTT,THH,THT,TTH,TTT}.

#### a) Exactly 2 Heads

This corresponds to scenarios where 2 flips result in Heads, and 1 flip results in Tails. Possible outcomes:

- HHT,HTH,THHHHT, HTH, THHHHT,HTH,THH (3 outcomes).

The probability is calculated using:

P(exactly 2 heads)=(32)⋅(0.5)2⋅(0.5)1P(\text{exactly 2 heads}) = \binom{3}{2} \cdot (0.5)^2 \cdot (0.5)^1P(exactly 2 heads)=(23​)⋅(0.5)2⋅(0.5)1 P(exactly 2 heads)=3⋅0.25⋅0.5=0.375P(\text{exactly 2 heads}) = 3 \cdot 0.25 \cdot 0.5 = 0.375P(exactly 2 heads)=3⋅0.25⋅0.5=0.375

#### b) Exactly 1 Head

This corresponds to scenarios where 1 flip results in Heads, and 2 flips result in Tails. Possible outcomes:

- HTT,THT,TTHHTT, THT, TTHHTT,THT,TTH (3 outcomes).

The probability is:

P(exactly 1 head)=(31)⋅(0.5)1⋅(0.5)2P(\text{exactly 1 head}) = \binom{3}{1} \cdot (0.5)^1 \cdot (0.5)^2P(exactly 1 head)=(13​)⋅(0.5)1⋅(0.5)2 P(exactly 1 head)=3⋅0.5⋅0.25=0.375P(\text{exactly 1 head}) = 3 \cdot 0.5 \cdot 0.25 = 0.375P(exactly 1 head)=3⋅0.5⋅0.25=0.375

#### c) No More Than 1 Head

This includes scenarios with **0 Heads** and **1 Head**.

1. **0 Heads**: TTTTTTTTT (1 outcome).

P(exactly 0 heads)=(30)⋅(0.5)0⋅(0.5)3=1⋅1⋅0.125=0.125P(\text{exactly 0 heads}) = \binom{3}{0} \cdot (0.5)^0 \cdot (0.5)^3 = 1 \cdot 1 \cdot 0.125 = 0.125P(exactly 0 heads)=(03​)⋅(0.5)0⋅(0.5)3=1⋅1⋅0.125=0.125

2. **1 Head**: Already calculated in part (b).

P(no more than 1 head)=P(exactly 0 heads)+P(exactly 1 head)=0.125+0.375=0.5P(\text{no more than 1 head}) = P(\text{exactly 0 heads}) + P(\text{exactly 1 head}) = 0.125 + 0.375 = 0.5P(no more than 1 head)=P(exactly 0 heads)+P(exactly 1 head)=0.125+0.375=0.5

---

### EXERCISE 8: Ball Draw Probabilities

#### Given:

- Total balls = 555 White, 333 Black, 222 Red (Total = 101010).
- Balls are drawn **one by one**, either **with returning** or **without returning**.

---

#### **Case 1: With Returning**

After drawing a ball, it is placed back in the box.

#### a) All of the Same Color

1. **All White**: Probability for all 3 draws to be White:

P(all white)=(510)3=0.125P(\text{all white}) = \left(\frac{5}{10}\right)^3 = 0.125P(all white)=(105​)3=0.125

2. **All Black**: Similarly:

P(all black)=(310)3=0.027P(\text{all black}) = \left(\frac{3}{10}\right)^3 = 0.027P(all black)=(103​)3=0.027

3. **All Red**:

P(all red)=(210)3=0.008P(\text{all red}) = \left(\frac{2}{10}\right)^3 = 0.008P(all red)=(102​)3=0.008

Total Probability:

P(all same color)=0.125+0.027+0.008=0.16P(\text{all same color}) = 0.125 + 0.027 + 0.008 = 0.16P(all same color)=0.125+0.027+0.008=0.16

---

#### b) Exactly 2 of the Same Color

This requires:

- 2 balls of one color, and 1 ball of a different color.

For example, **2 White and 1 Black**:

- Number of ways to choose 2 White out of 3 draws: (32)⋅P(W)2⋅P(B)\binom{3}{2} \cdot P(W)^2 \cdot P(B)(23​)⋅P(W)2⋅P(B).

Similarly, calculate for all combinations of 2 same-color outcomes.

---

#### Key Idea:

When drawing **without returning**, the total number of balls decreases after each draw. For example, after the first draw, the total number of balls becomes 999, then 888, etc. Probabilities are adjusted accordingly.

---

### a) All of the Same Color

1. **All White**:
    
    - First ball is White: P(W1)=510P(W_1) = \frac{5}{10}P(W1​)=105​,
    - Second ball is White: P(W2)=49P(W_2) = \frac{4}{9}P(W2​)=94​,
    - Third ball is White: P(W3)=38P(W_3) = \frac{3}{8}P(W3​)=83​.
    
    Probability:
    
    P(all white)=510⋅49⋅38=60720=0.0833P(\text{all white}) = \frac{5}{10} \cdot \frac{4}{9} \cdot \frac{3}{8} = \frac{60}{720} = 0.0833P(all white)=105​⋅94​⋅83​=72060​=0.0833
2. **All Black**:
    
    - First: P(B1)=310P(B_1) = \frac{3}{10}P(B1​)=103​,
    - Second: P(B2)=29P(B_2) = \frac{2}{9}P(B2​)=92​,
    - Third: P(B3)=18P(B_3) = \frac{1}{8}P(B3​)=81​.
    
    Probability:
    
    P(all black)=310⋅29⋅18=6720=0.0083P(\text{all black}) = \frac{3}{10} \cdot \frac{2}{9} \cdot \frac{1}{8} = \frac{6}{720} = 0.0083P(all black)=103​⋅92​⋅81​=7206​=0.0083
3. **All Red**:
    
    - First: P(R1)=210P(R_1) = \frac{2}{10}P(R1​)=102​,
    - Second: P(R2)=19P(R_2) = \frac{1}{9}P(R2​)=91​,
    - Third: P(R3)=0P(R_3) = 0P(R3​)=0.
    
    Probability:
    
    P(all red)=210⋅19⋅08=0P(\text{all red}) = \frac{2}{10} \cdot \frac{1}{9} \cdot \frac{0}{8} = 0P(all red)=102​⋅91​⋅80​=0

Total Probability:

P(all same color)=P(all white)+P(all black)+P(all red)=0.0833+0.0083+0=0.0916P(\text{all same color}) = P(\text{all white}) + P(\text{all black}) + P(\text{all red}) = 0.0833 + 0.0083 + 0 = 0.0916P(all same color)=P(all white)+P(all black)+P(all red)=0.0833+0.0083+0=0.0916

---

### b) Exactly 2 of the Same Color

This involves two balls of one color and one ball of a different color. Consider all possible cases (e.g., **2 White and 1 Black**, **2 Black and 1 White**, etc.).

1. **2 White, 1 Black**:
    
    - Choose the order: (32)=3\binom{3}{2} = 3(23​)=3,
    - Probabilities: P(W1)=510,P(W2)=49,P(B3)=38P(W_1) = \frac{5}{10}, P(W_2) = \frac{4}{9}, P(B_3) = \frac{3}{8}P(W1​)=105​,P(W2​)=94​,P(B3​)=83​.
    
    Probability:
    
    P(2 White, 1 Black)=3⋅(510⋅49⋅38)=3⋅60720=0.25P(\text{2 White, 1 Black}) = 3 \cdot \left( \frac{5}{10} \cdot \frac{4}{9} \cdot \frac{3}{8} \right) = 3 \cdot \frac{60}{720} = 0.25P(2 White, 1 Black)=3⋅(105​⋅94​⋅83​)=3⋅72060​=0.25
2. **2 Black, 1 White**: Repeat with adjusted probabilities.
    

---

### c) At Least 2 White

This includes the cases:

- **2 White and 1 Non-White**,
- **3 White**.

1. **2 White, 1 Non-White**: Calculate similar to part (b).
2. **3 White**: Already calculated in part (a).

Add the probabilities for these cases.

---