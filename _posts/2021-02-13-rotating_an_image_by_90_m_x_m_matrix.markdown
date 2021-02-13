---
layout: post
title:      "Rotating an image by 90' (m x m matrix)"
date:       2021-02-13 16:05:54 +0000
permalink:  rotating_an_image_by_90_m_x_m_matrix
---


Today we will practice on 2d matrix. I am pretty sure everybody is familiar with arrays. 2d matrix is represented by arrays within arrays. For example ; 

```
/*
1     2     3    10
4     5     6     11
7     8     9    12
13  14 15    16
*/
```

If you were to represent the above matrix in an array, how would you represent it? If you are thinking of row by row, then you are absolutely right. Above matrix in array would look like this

```
let matrix = [[1,2,3,10],[4,5,6,11],[7,8,9,12],[13,14,15,16]]
```

You can see each row has their own index position. And with in each index, each element have their own index. That means in order to retrieve or play with specific element inside a row, we have to use index within a specific index. For example to retrieve '3' from first row, we would do 

```
matrix[0][2]
```

In order to loop through all the elements in this matrix, we can simply run a nested for loop where outerloop loops over the rows and inner loop loops over each rows. Now, we are given a task of rotating this 2 d square matrix by 90 degrees clockwise. which is of dimension m x m. 

After the rotation, above matrix would look like this:
```
13    7     4      1   
14    8     5      2
15    9     6      3
16  12   11  10
```

Wow! what is that ? Thats not the matrix we started with or is it? Don't worry, we will go through this together. If you see the pattern, the last row is now the first column and the first row has become the last column. If we can start by converting our rows into column and vice versa, then we have our start. Have you heard about the term called TRANPOSE ? Thats exactly whats happening here at the end, rows converting into a column. 

Lets do a nested for loop and change our first row into first column and vice versa. Don't wory about the order of rows and column for now. 

```

let len = matrix.length

for(let i = 0; i < len; i++){
  for(let j= i; j< len; j++){
    let temp = matrix[i][j]
    matrix[i][j] = matrix[j][i]
    matrix[j][i]= temp

  }
}
```
You can see the above code just switches rows element into the column element in the same index. The only thing that doesnot change is the common element between row and column, which is the top cornered left element or by the end of iteration the diagonal remains the same.

Below is the matrix after every iteration so you can visualize what actually is going on through every iteration

```
Starting Matrix
1     2     3    10
4     5     6     11
7     8     9    12
13  14 15    16


After 1st iteration 
1    4      7      13
2    5      6      11
3    8       9     12
10 14   15    16


After 2nd iteration
1     4    7   13 
2     5    8   14
3     6    9   12
10 11 15  16

After 3rd iteration
 1    4    7   13 
 2    5    8   14
 3    6    9   15
10  11 12 16
```

The trick here to mess with just the inner matrix in every iteration is to make inner j = i . So whenever i increments, j does too so that you dont touch the indices that has been rearranged already.

Now that we iteration is complete, do you see our desired matrix in there? If we see carefully, it is what we want, its just out of order. Last column needs to be the first and vice versa as we proceed to the middle. How do we do that? Simple, just do another similar iteration and switch position of each indices inside each row. But, this time we don't iterate to all the index inside a row. We just do it upto the middle point or up to the half of the row's size.

```
for(let i = 0 ; i < len ; i++){
  for(let j = 0 ; j< Math.floor(len / 2) ; j++){
    let temp = matrix[i][j]
    matrix[i][j] = matrix[i][len-1-j]
    matrix[i][len -1-j] = temp
  }
}

```


If you noticed, inner j starts from 0, because every first element in the rows needs to be switched with the last element, so we don't equal that to i. And that is it. After the final iteration, our matrix is now rotated 90 degrees clockwise 

```
After final iteration
13     7     4   1   
14    8     5    2
15    9     6    3
16  12   11  10
```

Hope you all now have basic understanding of matrix manipulation



