---
layout: post
title: How Effective is Your Model
math: true
---

Have you ever seen a machine learning model with 99% accuracy and you see the one who did this model bragging? 
Well, I've been there.
Apart from overfitting, accuracy is just one metric that you cannot depend upon for specific data. 
In this article, I will explain why a high accuracy can be misleading from simple interpretations on a simple 
classification problem. Let's try a stupid model, a very stupid one that can classify nothing correctly 
i.e. every spam is predicted nonspam and every nonspam is predicted spam.

<html>
<center>
<head>
<style>
table#t01 {
  width:70%;
}
th, td {
  border: 1px solid black;
  border-collapse: collapse;
  padding: 15px;
  text-align: center;
}
tr:nth-child(even) {
  background-color: #eee;
}
tr:nth-child(odd) {
 background-color: #fff;
}
th {
 background-color: #bbb;
 color: white
}
.dot {
  height: 25px;
  width: 25px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
}
</style>
</head>
<body>

<table>
  <tr>
    <th>$$ y $$</th>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <th>$$ p $$</th>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
  </tr>
</table>

</body>
</center>
</html>

where `y` is the actual label and `p` is the predicted label: 1 for spam and 0 for nonspam comments on social media.

This classifier has 
neither precision nor recall i.e. precision = 0 and recall = 0 (stupid one I told you). Let's take another classifier:

<html>
<center>
<body>

<table>
  <tr>
    <th>$$y$$</th>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <th>$$p$$</th>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
  </tr>
</table>

</body>
</center>
</html>

That one is able to classify all spams correctly but classifies all nonspams as spams. The precision of nonspams is the lowest
 in this case (equals zero) because the classifier predicts each nonspam as a spam. While recall of spams is the highest (equals 1) 
 because each spam is predicted as a spam. But what is precision and recall?
 
## Examples in Table

<center>
<table>
  <tr>
    <th>$$y$$</th>
    <th>$$p_1$$</th>
    <th>$$p_2$$</th>
    <th>$$p_3$$</th>
    <th>$$p_4$$</th>
    <th>$$p_5$$</th>
    <th>$$p_6$$</th>
    <th>$$p_7$$</th>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
  </tr>
  <tr>
    <td>1</td>
    <td><span style="background-color: #58D3F7">0</span></td>
    <td>1</td>
    <td><span style="background-color: #58D3F7">0</span></td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td><span style="background-color: #58D3F7">0</span></td>
  </tr>
  <tr>
    <td>1</td>
    <td><span style="background-color: #58D3F7">0</span></td>
    <td>1</td>
    <td><span style="background-color: #58D3F7">0</span></td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td><span style="background-color: #58D3F7">1</span></td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <th>Precision(0)</th>
    <td>0</td>
    <td>0</td>
    <td>0.8</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>0.89</td>
  </tr>
  <tr>
    <th>Recall(0)</th>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>0.38</td>
    <td>0.75</td>
    <td>0.88</td>
    <td>1</td>
  </tr> 
  <tr>
    <th>F1-score(0)</th>
    <td>0</td>
    <td>0</td>
    <td>0.98</td>
    <td>0.55</td>
    <td>0.86</td>
    <td>0.93</td>
    <td>0.94</td>
  </tr>  
  <tr>
    <th>Precision(1)</th>
    <td>0</td>
    <td>0.2</td>
    <td>0</td>
    <td>0.29</td>
    <td>0.5</td>
    <td>0.67</td>
    <td>1</td>
  </tr>
  <tr>
    <th>Recall(1)</th>
    <td>0</td>
    <td>1</td>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>0.5</td>
  </tr> 
  <tr>
    <th>F1-score(1)</th>
    <td>0</td>
    <td>0.3</td>
    <td>0</td>
    <td>0.44</td>
    <td>0.67</td>
    <td>0.8</td>
    <td>0.67</td>
  </tr>  
  <tr>
    <th>Accuracy</th>
    <td>0</td>
    <td>0.2</td>
    <td>0.8</td>
    <td>0.5</td>
    <td>0.8</td>
    <td>0.9</td>
    <td>0.9</td>
  </tr>
</table>
</center>

$$[X][Y]$$ where $$X$$ is True or False and $$Y$$ is Positive or Negative.
To understand what I'm doing in the next lines. Start with $$Y$$ whether it is Positive or Negative.
Let's take a closer look at predicted spams (class 1). This means Positive will be 1 and Negative will be 0 while True will be the same as Y and False will be the opposite of $$Y$$.

$$TP$$ is how many 1's predicted and actually are 1's.
$$FP$$ is how many 1's predicted and are 0's inactual data.
$$TN$$ is how many 0's predicted and are 0's in actual data.
$$FN$$ is how many 0's predicted and are actually 1's.

For interpretations, replace each 1 by spam and each 0 by nonspam.

$$ Precision=\frac{TP}{TP+FP} $$

$$ Recall=\frac{TP}{TP+FN} $$

F1-score is the harmonic mean of precision and recall.
Accuracy is number of correctly predicted values over total size.

