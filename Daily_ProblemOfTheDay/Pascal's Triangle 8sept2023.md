# Pascal's Triangle

Pascal's Triangle is constructed by starting with a single "1" at the top and adding rows below it. Each number in the triangle is the sum of the two numbers directly above it. Here's a glimpse of the first few rows


                           1
                        1       1
                    1       2       1
                1       3       3       1
            1       4       6       4       1
        1       5       10      10      5       1
    

Note : From row 1 to 6



## In this we can get 3 variations of question 

- __Printing a Specific Element:__ Given a row and column, we want to find the value at that position, e.g., row 5, column 3 should return 6. 
    
    row-5, col-3    
        -> 6
- __Printing a Specific Element:__ Given a row and column, we want to find the value at that position, e.g., row 5, column 3 should return 6.

    print row 4  
        -> [ 1       3       3       1 ]

- __Printing the Entire Triangle:__ We'll generate and display the entire Pascal's Triangle up to a specified number of rows.


    
    n = 6 
    -> top digram  ^


## Approach for 1st variation 

To find the value of any row and column use the formula of  

### <sup>row - 1</sup> C <sub> col - 1    

### =  (row -1)! __/__ (col -1)! * __[__ ( row - 1) - (col - 1) __]__!

To put this in code we can modify it(shortcut)

## Code

```
public static int getValueOfRowColumn(int row, int col){
    int ans = 1;
    for(int i = 0;i<row;i++){
        ans = ans * (col -i);
        ans = ans / i+1;
    }

    return ans;
}
```

## Approach for 2nd variation 

__Observation__ : n <sup>th</sup> row will always containg n element ( following 1 based index)

To print the whole row we have to iterate for n times for sure  
and in each iteration we have to use the ealier function find the value of each row & col.

```
for(int col = 1;i<= row;col++){
    print(getValueOfRowColumn(row-1,col-1));
}
```

This will take O(row * col) time complexity which is not that good ...we might be asked to optimize it ..which we will next!


now we will consider the 0 based indexing for the column 

suppose we are talking about 4th row

    [1  5   10  10  5   1]

row = 6

    [1  5   10  10  5   1]

    1   5/1   5/1 * 4/2    5/1 * 4/2 * 3/3   5/1 * 4/2 * 3/3 * 2/2    5/1 * 4/2 * 3/3 * 2/4 * 1/5 



- The first element is always 1.
- For each subsequent element, we can calculate it as previousElement * (row - col) / (col + 1)


 
    row - col / col + 1

    we can replace col + 1 to just col but strarting the loop from 1 only

## Code
```
public static List<Integer> printTheRow(int row){
        List<Integer> temp = new ArrayList<>();
        temp.add(1);
        int ans = 1;
        for(int col = 1;col<row;col++){
            ans = ans * (row - col);
            ans = ans/col;
            temp.add(ans);
        }
        return temp;
    }
```


## Approach 3 - printing triangle

now we have to print row every n

## Code
```
public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> a = new ArrayList<>();
        for(int row =1;row<=numRows;row++){
            a.add(printTheRow(row));
        }
        return a;
    }
```
    
