# R

---

[https://www.geeksforgeeks.org/r-tutorial/?ref=lbp](https://www.geeksforgeeks.org/r-tutorial/?ref=lbp)

https://www.r-project.org/

- The language of data science, free and open-source, 9000+ free packages
- Variables
    - The assignment can be done in three ways
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled.png)
        
        ```r
        var = "Example"
        var <- "Example" # also <<- (makes it global)
        "Example" -> var # also ->> (makes it global)
        ```
        
    - Methods
        - ls()
            - Used to know all of the variables in the workspace
                
                ```r
                # using equal to operator
                var1 = "hello"
                
                # using leftward operator
                var2 <- "hello"
                
                # using rightward operator
                "hello" -> var3
                
                print(ls())
                # [1] "var1" "var2" "var3"
                ```
                
        - rm()
            - Used to delete an unwanted variable within your workspace
            - This helps to clear the memory space allocated to certain variables that are not been used
            
            ```r
            # using equal to operator
            var1 = "hello"
            
            # using leftward operator
            var2 <- "hello"
            
            # using rightward operator
            "hello" -> var3
            
            # Removing variable
            rm(var3)
            print(var3)
            # Error in print(var3) : object 'var3' not found
            # Execution halted 
            ```
            
        - Global and local variables
            - We can use local (are modified just inside the function) and global (can be modified anywhere) variables
- Data types
    - Numeric
        - Set of all real numbers, real numbers with a decimal point are represented using this data type in R. It uses a format for double-precision floating-point numbers to represent numerical values
            - Even if an integer is assigned to a variable y, it is still saved as a numeric value
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%201.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%202.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%203.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%204.png)
        
        - When R stores a number in a variable, it converts the number into a “double” value or a decimal type with at least two decimal places; this means that a value such as “5” here, is stored as 5.00 with a type of double and a class of numeric and also y is not an integer here can be confirmed with the is.integer() function.
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%205.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%206.png)
            
    - Integer
        - Set of all integers, to assign a value as a integer we can use the function as.integer() or use a capital ‘L’ notation as a suffix to denote that a particular value if an integer
            
            ```r
            x = as.integer(5)
            print(class(x)) # "integer"
            print(typeof(x)) # "integer"
            
            y = 5L
            print(class(y)) # "integer"
            print(typeof(y)) # "integer"
            ```
            
    - Logical
        - Basically a boolean value
        
        ```r
        z = 3 > 4
        print(z) # TRUE
        print(class(z)) # "logical"
        print(typeof(z)) # "logical"
        ```
        
    - Complex
        - The set of all the complex numbers, this data type is used to store numbers with an imaginary component
        
        ```r
        x = 4 + 3i
        print(class(x)) # "complex"
        print(typeof(x)) # "complex"
        ```
        
    - Character
        - It stores character values or strings and it needs to be between simple or double commas; the character can be letters, numbers, symbols etc
        
        ```r
        char = "Testeteste"
        print(class(char)) # "character"
        print(typeof(char)) # "character"
        ```
        
    - Raw
        - To save and work with data at byte level or working with data that is not meant to be interpreted as a numerical or character data
            - By displaying a series of unprocessed bytes, it enables low-level operations on binary data
            - It basically creates a vector with ascii, binary, hex information; we can convert char to raw using charToRaw() and vice-versa using rawToChar()
                - We can also convert a number to bits and then convert the bits to raw using intToBits() and packBits()
            
            ```r
            # Convert a character string to raw bytes
            char_data <- "Example"
            raw_data <- charToRaw(char_data)
            print(raw_data)  # Prints the raw bytes
            # [1] 45 78 61 6d 70 6c 65
            
            # Convert the raw bytes back to a character string
            back_to_char <- rawToChar(raw_data)
            print(back_to_char)  # Prints "Example"
            # [1] "Example"
            
            # Create a raw vector directly
            raw_vector <- as.raw(c(0x01, 0x02, 0xFF))
            print(raw_vector)  # Prints the raw vector
            # [1] 01 02 ff
            
            # Convert integers to raw bits and back
            int_value <- 42
            bits <- intToBits(int_value)
            print(bits)  # Prints the raw bits of the integer 42
            #  [1] 00 01 00 01 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
            # [31] 00 00
            packed_bits <- packBits(bits)
            print(packed_bits)  # Prints the packed bits as raw data
            # [1] 2a 00 00 00
            ```
            
    - To find a data type in R just use class() function and to verify the data type just use is.data_type() (this function returns a boolean value TRUE if the data type is correct else returns FALSE)
    - Conversions
        - To convert data types we can use as.data_type(), but not all of the conversions are possible and can return NA value
            - Alongside the data types above, there are much more “as.” functions such as as.Date, as.vector, as.matrix and etc.
- Data structures (TERMINAR)
    - String
        - It’s an array of characters
        - An empty string is represented with “”
        - A string can be double-quoted or single-quoted
        - Lenght
            - To get the lenght of a string usestr_lenght() that belongs to the package stringr
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%207.png)
                
                - Output: 5
                - Also, we can use nchar(), that is a built-in function
                    
                    ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%208.png)
                    
                    - Output: 6
        - Substring
            - To get a portion of a string (substring) we can use substr() or substring()
                - The syntax of both functions is: function(string, start_index, end_index)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%209.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2010.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2011.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2012.png)
                
            - With the lenght and substring combined we can do string slicing
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2013.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2014.png)
                
        - Case convertion
            - We can use toupper() to get uppercase, tolower() to get lowercase and we can get casefold(…, UPPER = TRUE) to get uppercase (the vale of upper in casefold is FALSE by default)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2015.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2016.png)
                
        - Concatenation
            - We can concatenate strings using the output function paste() (the best imo) and other more
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2017.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2018.png)
                
        - Updating strings
            - We can update a string using the gsub() function (syntax: gsub(word_that_i_want_to_change, word_to_get_in_place, my_string))
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2019.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2020.png)
                
    - Vector
        - A vector is an ordered collection of basic data types of a given lenght, in R the index of vector always start from 1 and not from 0
        - Is basically a one-dimensional array
        - Creation
            - To create a vector we normally use c() function, the arguments of this function is basically the elements that we want to compose our vector
            - Another function we can use is seq() that basically creates a sequence of continuous values, the syntax is: seq(first_element, second_element, lenght.out)
            - Finally, we can use ‘:’ to create a vector, we just need to put values before and after the ‘:’ ad=nd it will return a vector of the continous values
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2021.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2022.png)
            
        - To get the lenght of a vector we can use lenght() function
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2023.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2024.png)
            
        - To access the vector elements, we can use index operator ‘[]’, we just need to pay attention because the vector is 1-based
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2025.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2026.png)
            
            - We can get multiple index using c() as a index
        - Modifying a vector
            - We can modify a specific element, a subvector or the entire vector
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2027.png)
            
            - The first modification we change our vector to (2, 7, 9, 8, 2) to (2, 9, 1, 7, 8, 2)
            - The second modification, we modify the vector from the index 1 to 5 and we put 0 in all of these index
                - Vector before: (2, 9, 1, 7, 8, 2); vector after: (0, 0, 0, 0, 0, 2)
            - The last modification, we change our vector X with 6 index positions to another vector with 3 index positions, which these positions are his third, second and first element and these elements are displayed on the vector in this order
                - Vector before: (0, 0, 0, 0, 0, 2); vector after: (0, 0, 0)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2028.png)
            
        - Deleting a vector
            - We can just assign the vector as NULL
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2029.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2030.png)
                
            - Other way
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2031.png)
                
                - Deleting the elements 3, 4 and 5 if they are on vec
        - Sorting the elements of a vector
            - We can use sort() function to sort the elements of a vector in ascending or descending order
                - sort() has a argument decresing that is FALSE by default, but if it’s TRUE it will sort by descending order
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2032.png)
            
    - Matrices
        - A matrix is a two-dimensional array
        - Creation
            - To create a matrix we can use the matrix() function
                - Syntax
                    
                    ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2033.png)
                    
            - Example
                
                ```r
                my_matrix <- matrix(
                  1:9,
                  nrow = 3,
                  ncol = 3,
                  byrow = FALSE
                )
                
                print(my_matrix)
                
                my_matrix <- matrix(
                  1:9,
                  nrow = 3,
                  ncol = 3,
                  byrow = TRUE
                )
                
                print(my_matrix)
                
                cat('\014')
                
                Output:
                
                    [,1] [,2] [,3]
                [1,]    1    4    7
                [2,]    2    5    8
                [3,]    3    6    9
                
                     [,1] [,2] [,3]
                [1,]    1    2    3
                [2,]    4    5    6
                [3,]    7    8    9
                ```
                
            - Named matrix
                - We just use the colnames() and rownames() functions
                
                ```r
                my_matrix <- matrix(
                  1:9,
                  nrow = 3,
                  ncol = 3,
                  byrow = TRUE,
                )
                
                rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                
                print(my_matrix)
                
                cat('\014')
                
                Output:
                      col 1 col 2 col 3
                row 1     1     2     3
                row 2     4     5     6
                row 3     7     8     9
                ```
                
            - Special matrices
                - A matrix where all rows and columns are filled by a single constant
                    
                    ```r
                    my_matrix <- matrix(
                      5,
                      nrow = 3,
                      ncol = 3,
                      byrow = TRUE,
                    )
                    
                    rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                    colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                    
                    print(my_matrix)
                    
                    cat('\014')
                    
                    Output:
                          col 1 col 2 col 3
                    row 1     5     5     5
                    row 2     5     5     5
                    row 3     5     5     5
                    ```
                    
                - Diagonal matrix
                    - To create a diagonal matrix we use the diag() function
                        
                        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2034.png)
                        
                    
                    ```r
                    my_matrix <- diag(c(4, 9, 8), 3, 3)
                    
                    rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                    colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                    
                    print(my_matrix)
                    
                    cat('\014')
                    
                    Output:
                    
                          col 1 col 2 col 3
                    row 1     4     0     0
                    row 2     0     9     0
                    row 3     0     0     8
                    ```
                    
                - Identity matrix
                    - We use the diag() function and the parameter “k” on this function is 1
                    
                    ```r
                    my_matrix <- diag(1, 3, 3)
                    
                    rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                    colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                    
                    print(my_matrix)
                    
                    cat('\014')
                    
                    Output:
                          col 1 col 2 col 3
                    row 1     1     0     0
                    row 2     0     1     0
                    row 3     0     0     1
                    ```
                    
        - Helpful functions
            - dim(), nrow(), ncol(), lenght(), prod()
            
            ```r
            my_matrix <- matrix(
              1:9,
              nrow = 3,
              ncol = 3,
              byrow = TRUE,
            )
            
            rownames(my_matrix) <- c("row 1", "row 2", "row 3")
            colnames(my_matrix) <- c("col 1", "col 2", "col 3")
            
            cat("My matrix: \n")
            print(my_matrix)
            cat("The dimension of my matrix: ", dim(my_matrix))
            cat("The number of rows: ", nrow(my_matrix))
            cat("The number of columns: ", ncol(my_matrix))
            cat("The number of elements w\ length: ", length(my_matrix))
            cat("The number of elements w\ prod: ", prod(dim(my_matrix)))
            cat("The product of the elements: ", prod(my_matrix))
            
            cat('\014')
            
            Output:
            
            My matrix: 
                  col 1 col 2 col 3
            row 1     1     2     3
            row 2     4     5     6
            row 3     7     8     9
            The dimension of my matrix:  3 3
            The number of rows:  3
            The number of columns:  3
            The number of elements w length:  9
            The number of elements w prod:  9
            The product of the elements:  362880
            ```
            
        - Accessing
            - To access the elements of our matrix we use the index, note that the index of a row is [x,] and the index of a column is [,x]
            
            ```r
            my_matrix <- matrix(
              1:9,
              nrow = 3,
              ncol = 3,
              byrow = TRUE,
            )
            
            rownames(my_matrix) <- c("row 1", "row 2", "row 3")
            colnames(my_matrix) <- c("col 1", "col 2", "col 3")
            
            print(my_matrix)
            
            print(my_matrix[1:2,])
            # accessing the 1st and 2nd rows
            
            print(my_matrix[,c("col 1", "col 3")])
            # accessing the 1st and 3rd columns
            
            print(my_matrix[c(1, 3), c("col 2", "col 3")])
            # accessing the elements that belong to the 1st row, 3rd row, 2nd column
            # and 3rd column
            
            cat('\014')
            
            Output:
            
                  col 1 col 2 col 3
            row 1     1     2     3
            row 2     4     5     6
            row 3     7     8     9
            
                  col 1 col 2 col 3
            row 1     1     2     3
            row 2     4     5     6
            
                  col 1 col 3
            row 1     1     3
            row 2     4     6
            row 3     7     9
            
                  col 2 col 3
            row 1     2     3
            row 3     8     9
            ```
            
        - Modifying elements
            - We can modifying the elements accessing them using index
            
            ```r
            my_matrix <- matrix(
              1:9,
              nrow = 3,
              ncol = 3,
              byrow = TRUE,
            )
            
            rownames(my_matrix) <- c("row 1", "row 2", "row 3")
            colnames(my_matrix) <- c("col 1", "col 2", "col 3")
            
            print(my_matrix)
            
            my_matrix[1, "col 2"] <- 80
            # modifying a single element
            
            print(my_matrix)
            
            my_matrix["row 2",] <- c(78, 65, 43)
            # modifying a hole row
            
            print(my_matrix)
            
            my_matrix[, "col 3"] <- c(55, 43, 21)
            # modifying a hole column
            
            print(my_matrix)
            
            cat('\014')
            
            Output:
                  col 1 col 2 col 3
            row 1     1     2     3
            row 2     4     5     6
            row 3     7     8     9
            
                  col 1 col 2 col 3
            row 1     1    80     3
            row 2     4     5     6
            row 3     7     8     9
            
                  col 1 col 2 col 3
            row 1     1    80     3
            row 2    78    65    43
            row 3     7     8     9
            
                  col 1 col 2 col 3
            row 1     1    80    55
            row 2    78    65    43
            row 3     7     8    21
            ```
            
        - Concatenation
            - The concatenation of rows is done by using rbind()
                - The parameters are just the matrices itselfs
                - The names of the rows and cols has priority on the first matrix to be called on the function
                
                ```r
                my_matrix <- matrix(
                  1:9,
                  nrow = 3,
                  ncol = 3,
                  byrow = TRUE,
                )
                
                rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                
                print(my_matrix)
                
                aux_matrix <- matrix(
                  10:12,
                  nrow = 1,
                  ncol = 3,
                  byrow = TRUE
                )
                
                rownames(aux_matrix) <- c("aux row 1")
                colnames(aux_matrix) <- c("aux col 1", "aux col 2", "aux col 3")
                
                print(aux_matrix)
                
                new_matrix <- rbind(my_matrix, aux_matrix)
                
                print(new_matrix)
                
                cat('\014')
                
                Output:
                      col 1 col 2 col 3
                row 1     1     2     3
                row 2     4     5     6
                row 3     7     8     9
                
                          aux col 1 aux col 2 aux col 3
                aux row 1        10        11        12
                
                          col 1 col 2 col 3
                row 1         1     2     3
                row 2         4     5     6
                row 3         7     8     9
                aux row 1    10    11    12
                ```
                
            - The concatenation of cols is done by using cbind()
                - The parameters are just the matrices itselfs
                - The names of the rows and cols has priority on the first matrix to be called on the function
                
                ```r
                my_matrix <- matrix(
                  1:9,
                  nrow = 3,
                  ncol = 3,
                  byrow = TRUE,
                )
                
                rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                
                print(my_matrix)
                
                aux_matrix <- matrix(
                  10:15,
                  nrow = 3,
                  ncol = 2,
                  byrow = TRUE
                )
                
                colnames(aux_matrix) <- c("aux col 1", "aux col 2")
                rownames(aux_matrix) <- c("aux row 1", "aux row 2", "aux row 3")
                
                print(aux_matrix)
                
                new_matrix <- cbind(my_matrix, aux_matrix)
                
                print(new_matrix)
                
                cat('\014')
                
                Output:
                
                      col 1 col 2 col 3
                row 1     1     2     3
                row 2     4     5     6
                row 3     7     8     9
                
                          aux col 1 aux col 2
                aux row 1        10        11
                aux row 2        12        13
                aux row 3        14        15
                
                      col 1 col 2 col 3 aux col 1 aux col 2
                row 1     1     2     3        10        11
                row 2     4     5     6        12        13
                row 3     7     8     9        14        15
                ```
                
            - In both cases, we need to make sure that the number of columns or rows must be the same for the parameters in the functions
        - Adding elements
            - Adding a row
                - To add a row we use again the rbind()
                
                ```r
                my_matrix <- matrix(
                  1:9,
                  nrow = 3,
                  ncol = 3,
                  byrow = TRUE,
                )
                
                rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                
                print(my_matrix)
                
                new_row <- c(10, 11, 12)
                
                my_matrix <- rbind(my_matrix, new_row)
                
                print(my_matrix)
                
                cat('\014')
                
                Output:
                
                      col 1 col 2 col 3
                row 1     1     2     3
                row 2     4     5     6
                row 3     7     8     9
                
                        col 1 col 2 col 3
                row 1       1     2     3
                row 2       4     5     6
                row 3       7     8     9
                new_row    10    11    12
                ```
                
            - Adding a column
                - To add a column we use again the cbind()
                
                ```r
                my_matrix <- matrix(
                  c(1, 2, 3, 4, 5, 6, 7, 8, 9),
                  nrow = 3,
                  ncol = 3,
                  byrow = TRUE,
                )
                
                rownames(my_matrix) <- c("row 1", "row 2", "row 3")
                colnames(my_matrix) <- c("col 1", "col 2", "col 3")
                
                print(my_matrix)
                
                new_column <- c(10, 11, 12)
                
                my_matrix <- cbind(my_matrix, new_column)
                
                print(my_matrix)
                
                cat('\014')
                
                Output:
                
                      col 1 col 2 col 3
                row 1     1     2     3
                row 2     4     5     6
                row 3     7     8     9
                
                      col 1 col 2 col 3 new_column
                row 1     1     2     3         10
                row 2     4     5     6         11
                row 3     7     8     9         12
                ```
                
        - Deleting elements
            - To delete a row or column we just need to access it with index and put a negative sign before the index to delete it
            
            ```r
            my_matrix <- matrix(
              1:9,
              nrow = 3,
              ncol = 3,
              byrow = TRUE,
            )
            
            rownames(my_matrix) <- c("row 1", "row 2", "row 3")
            colnames(my_matrix) <- c("col 1", "col 2", "col 3")
            
            print(my_matrix)
            
            my_matrix <- my_matrix[-2, ]
            # removing the 2nd row
            
            print(my_matrix)
            
            my_matrix <- my_matrix[, -3]
            # removing the 3rd column
            
            print(my_matrix)
            
            my_matrix <- my_matrix[-1, -2]
            # removing the 1st row and the 2nd column (my_matrix is now a integer)
            
            print(my_matrix)
            
            cat('\014')
            
            Output:
                  col 1 col 2 col 3
            row 1     1     2     3
            row 2     4     5     6
            row 3     7     8     9
            
                  col 1 col 2 col 3
            row 1     1     2     3
            row 3     7     8     9
            
                  col 1 col 2
            row 1     1     2
            row 3     7     8
            
            [1] 7
            ```
            
    - Lists
        - A list is a vector but with heterogenous data elements, we can have a list of vectors, functions, matrices and so on
        - Creation
            - To create a lista we need to use the function list()
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2035.png)
                
                - In this example, we create a list that the first index of this list contains a vector of ID’s, the second index contains a vector of names and the third index contains the number of employees
                    
                    ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2036.png)
                    
            - Named list
                - The [[1]], [[2]] and [[3]] are the index of the list and [1] are the index inside the index of the list; we can name these [[1]], [[2]] and [[3]] index by assign to the vectors inside the list function
                    
                    ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2037.png)
                    
                    ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2038.png)
                    
                    - Now, we have what is called a named list
        - Acessing list components
            - All the components of a list can be named and we can use those names to access the components of the list using the dollar command ($)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2039.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2040.png)
                
            - We can also access the components of a list using the double slicing operator “[[]]” and if we want to access an inner-lever components we need to add another “[]” along with the double slicing operator
                - Inside of these two brackets we can put or the index that we want or the name given to that index (in case if the list is a named one)
                
                ```r
                empId = c(1, 2, 3, 4)
                empName = c("Debi", "Sandeep", "Subham", "Shiba")
                numberOfEmp = 4
                
                empList = list(
                  "ID's" = empId, 
                  "name" = empName, 
                  "Number of Employees" = numberOfEmp
                  )
                
                print(empList)
                
                # Accessing a top level components by name
                cat("Accessing name components using name\n")
                print(empList[["name"]])
                
                # Accessing a top level components by indices
                cat("Accessing name components using indices\n")
                print(empList[[2]])
                
                # Accessing a inner level components by name
                cat("Accessing Sandeep from name using name\n")
                print(empList[["name"]][2])
                
                # Accessing a inner level components by indices
                cat("Accessing Sandeep from name using indices\n")
                print(empList[[2]][2])
                
                # Accessing another inner level components by name
                cat("Accessing 4 from ID using name\n")
                print(empList[["ID's"]][4])
                
                # Accessing another inner level components by indices
                cat("Accessing 4 from ID using indices\n")
                print(empList[[1]][4])
                
                Output:
                $`ID's`
                [1] 1 2 3 4
                
                $name
                [1] "Debi"    "Sandeep" "Subham"  "Shiba"  
                
                $`Number of Employees`
                [1] 4
                
                Accessing name components using name
                [1] "Debi"    "Sandeep" "Subham"  "Shiba"  
                
                Accessing name components using indices
                [1] "Debi"    "Sandeep" "Subham"  "Shiba"  
                
                Accessing Sandeep from name using name
                [1] "Sandeep"
                
                Accessing Sandeep from name using indices
                [1] "Sandeep"
                
                Accessing 4 from ID using name
                [1] 4
                
                Accessing 4 from ID using indices
                [1] 4
                ```
                
        - Modifying components of a list
            - We can modify the same way we access the list components, but we assign a value to this access
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2041.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2042.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2043.png)
                
        - Concatenation of lists
            - To concatenate a list we can use the c() function with lists as arguments
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2044.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2045.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2046.png)
                
        - Adding itens
            - To add an item to the end of the list we use the append(my_list, element) function
                
                ```r
                # creating a list
                number_vector <- c(1, 2, 3, 4, 5)
                
                my_list <- list("numbers" = number_vector)
                print(my_list)
                
                # adding a new layer (index) on the end of the list and not specifying
                my_list <- append(my_list, "Recife")
                print(my_list)
                
                # adding a new layer (index) on the end of the list and specifying
                # to create a new named layer we need to to assign with 
                # the layer and inside the append()
                my_list$"currency" <- append(my_list$"currency", "Reais")
                print(my_list)
                
                # adding a new element on "numbers"
                my_list$"numbers" <- append(my_list$"numbers", 8)
                print(my_list)
                
                cat("\014") # clear the console
                
                Output:
                # creating a list
                $numbers
                [1] 1 2 3 4 5
                
                # adding a new layer (index) on the end of the list and not specifying
                $numbers
                [1] 1 2 3 4 5
                
                [[2]]
                [1] "Recife"
                
                # adding a new layer (index) on the end of the list and specifying
                $numbers
                [1] 1 2 3 4 5
                
                [[2]]
                [1] "Recife"
                
                $currency
                [1] "Reais"
                
                # adding a new element on "numbers"
                $numbers
                [1] 1 2 3 4 5 8
                
                [[2]]
                [1] "Recife"
                
                $currency
                [1] "Reais"
                ```
                
        - Deleting components of a list
            - To delete a component of a list we need to access this component and deleting using negative index
                
                ```r
                # Creating a list by naming all its components
                empId = c(1, 2, 3, 4)
                empName = c("Debi", "Sandeep", "Subham", "Shiba")
                numberOfEmp = 4
                empList = list(
                  "ID" = empId,
                  "Names" = empName,
                  "Total Staff" = numberOfEmp
                )
                cat("Before deletion the list is\n")
                print(empList)
                
                # Deleting a top level components
                cat("After Deleting Total staff components\n")
                empList <- empList[-3]
                print(empList)
                
                # Deleting a inner level components
                cat("After Deleting sandeep from name\n")
                empList[[2]] <- empList[[2]][-2]
                print(empList)
                
                cat("\014")
                
                Output:
                Before deletion the list is
                $ID
                [1] 1 2 3 4
                
                $Names
                [1] "Debi"    "Sandeep" "Subham"  "Shiba"  
                
                $`Total Staff`
                [1] 4
                
                After Deleting Total staff components
                $ID
                [1] 1 2 3 4
                
                $Names
                [1] "Debi"    "Sandeep" "Subham"  "Shiba" 
                
                After Deleting sandeep from name
                $ID
                [1] 1 2 3 4
                
                $Names
                [1] "Debi"   "Subham" "Shiba" 
                ```
                
        - Merging lists
            - We can merge two or more lists by concatenate them
            - Not named
                
                ```r
                # Create two lists.
                lst1 <- list(1,2,3)
                lst2 <- list("Sun","Mon","Tue")
                
                # Merge the two lists.
                new_list <- c(lst1,lst2)
                
                # Print the merged list.
                print(new_list)
                
                cat("\014")
                
                Output:
                [[1]]
                [1] 1
                
                [[2]]
                [1] 2
                
                [[3]]
                [1] 3
                
                [[4]]
                [1] "Sun"
                
                [[5]]
                [1] "Mon"
                
                [[6]]
                [1] "Tue"
                ```
                
            - Named
                
                ```r
                # Create two lists.
                
                lst1 <- list("numbers" = c(1,2,3))
                lst2 <- list("days" = c("Sun","Mon","Tue"))
                
                # Merge the two lists.
                new_list <- c(lst1,lst2)
                
                # Print the merged list.
                print(new_list)
                
                cat("\014")
                
                Output:
                $numbers
                [1] 1 2 3
                
                $days
                [1] "Sun" "Mon" "Tue"
                ```
                
        - Convertion
            - List to vector
                - First we create a list and then create a vector variable that will be asigned with the function unlist(my_list)
                    
                    ```r
                    
                    # Create lists.
                    lst <- list(1:5)
                    print(lst)
                     
                    # Convert the lists to vectors.
                    vec <- unlist(lst)
                     
                    print(vec)
                    
                    Output:
                    [[1]]
                    [1] 1 2 3 4 5 # list
                    
                    [1] 1 2 3 4 5 # vector
                    ```
                    
            - List to matrix
                - To convert a list to a matrix we use matrix() and unlist() combined
                    
                    ```r
                    # Defining list
                    lst1 <- list("list 1" = list(1, 2, 3), "list 2" = list(4, 5, 6))
                    
                    # Print list
                    cat("The list is:\n")
                    print(lst1)
                    cat("Class:", class(lst1), "\n")
                    
                    # Convert list to matrix
                    mat <- matrix(unlist(lst1), nrow = 2, byrow = TRUE)
                    
                    # Print matrix
                    cat("\nAfter conversion to matrix:\n")
                    print(mat)
                    cat("Class:", class(mat), "\n")
                    
                    cat("\014")
                    
                    Output:
                    The list is:
                    
                    $`list 1`
                    $`list 1`[[1]]
                    [1] 1
                    
                    $`list 1`[[2]]
                    [1] 2
                    
                    $`list 1`[[3]]
                    [1] 3
                    
                    $`list 2`
                    $`list 2`[[1]]
                    [1] 4
                    
                    $`list 2`[[2]]
                    [1] 5
                    
                    $`list 2`[[3]]
                    [1] 6
                    
                    Class: list 
                    
                    After conversion to matrix:
                         [,1] [,2] [,3]
                    [1,]    1    2    3
                    [2,]    4    5    6
                    
                    Class: matrix array 
                    ```
                    
    - Array
        - Arrays are data storage structures defined by a fixed number of dimensions, an uni-dimensional array is called vector and a two-dimensional array is called matrix
        - Arrays consists in all elements of the same data type
        - Creation
            - To create an array we use the function array()
                - Syntax
                    
                    ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2047.png)
                    
                - If we want to create a vector, we use c() function and if we want to create a matrix we use matrix() function
                - Creating a matrix using array()
                    
                    ```r
                    arr <- array(
                        2:13, # we want to get in our array the elements from 2 to 13
                        dim = c(2, 3, 2) # to set up the dimensions of our array we use c()
                        # the first parameter is the number of rows, the second is number of columns
                        # and the third is how many index that contains row x col elements our array
                        # will have; is basically the number of matrices of dimensions row * col
                        )
                        
                    print(arr)
                    
                    Output:
                    , , 1
                    
                         [,1] [,2] [,3]
                    [1,]    2    4    6
                    [2,]    3    5    7
                    
                    , , 2
                    
                         [,1] [,2] [,3]
                    [1,]    8   10   12
                    [2,]    9   11   13
                    ```
                    
        - Naming of arrays
            - To put names on the rows, cols and matrices of our array we must use the 3rd argument of the array() function, dimnames
                - dimnames must be a list
            
            ```r
            row_names <- c("row 1", "row 2", "row 3")
            col_names <- c("col 1", "col 2")
            mat_names <- c("matrix 1", "matrix 2")
            
            arr <- array(
                data = 2:20, 
                dim = c(length(row_names), length(col_names), length(mat_names)),
                dimnames = list(row_names, col_names, mat_names)
                )
            
            print(arr)
            
            cat("\014")
            
            Output:
            , , matrix 1
            
                  col 1 col 2
            row 1     2     5
            row 2     3     6
            row 3     4     7
            
            , , matrix 2
            
                  col 1 col 2
            row 1     8    11
            row 2     9    12
            row 3    10    13
            ```
            
            - Note that i’ve put 2:20 but the array has only 2:13; this is like that because our array was full
        - Accessing
            - We can access either by index or by name (if our array is a named one)
            - Index of an array
                - The index of any matrix of an array is succeeded by two commas: ,,matrix_index
                - The index of any row of an array is followed by one comma: row_index,
                - The index of any col of an array is succeeded by one comma: ,col_index
            - Accessing entire matrices
                
                ```r
                row_names <- c("row 1", "row 2", "row 3")
                col_names <- c("col 1", "col 2")
                mat_names <- c("matrix 1", "matrix 2")
                
                arr <- array(
                    data = 2:20, 
                    dim = c(length(row_names), length(col_names), length(mat_names)),
                    dimnames = list(row_names, col_names, mat_names)
                    )
                
                # printing matrix 1 using the index
                print(arr[,,1])
                
                # printing matrix 2 using the name
                print(arr[,,"matrix 2"])
                
                cat("\014")
                
                Output:
                      col 1 col 2
                row 1     2     5
                row 2     3     6
                row 3     4     7
                
                      col 1 col 2
                row 1     8    11
                row 2     9    12
                row 3    10    13
                ```
                
            - Accessing specific rows and cols of matrices
                - Putting the index separate
                    
                    ```r
                    row_names <- c("row 1", "row 2", "row 3")
                    col_names <- c("col 1", "col 2")
                    mat_names <- c("matrix 1", "matrix 2")
                    
                    arr <- array(
                        data = 2:20, 
                        dim = c(length(row_names), length(col_names), length(mat_names)),
                        dimnames = list(row_names, col_names, mat_names)
                        )
                    
                    # printing row 2 of matrix 1 using the index
                    print(arr[,,1][2,])
                    
                    # printing row 3 of matrix 2 using the name
                    print(arr[,,"matrix 2"]["row 3",])
                    
                    # printing the col 1 of matrix 1 using the name
                    print(arr[,,"matrix 1"][,"col 1"])
                    
                    # printing the col 2 of matrix 2 using the index
                    print(arr[,,2][,2])
                    
                    cat("\014")
                    
                    Output:
                    col 1 col 2  # arr[,,1][2,]
                        3     6 
                        
                    col 1 col 2 # arr[,,"matrix 2"]["row 3",]
                       10    13 
                    
                    row 1 row 2 row 3 # arr[,,"matrix 1"][,"col 1"]
                        2     3     4 
                        
                    row 1 row 2 row 3 # arr[,,2][,2]
                       11    12    13 
                    ```
                    
                - We can also “combine” the index of the columns/rows and matrices (best imo)
                    
                    ```r
                    row_names <- c("row 1", "row 2", "row 3")
                    col_names <- c("col 1", "col 2")
                    mat_names <- c("matrix 1", "matrix 2")
                    
                    arr <- array(
                      data = 2:20, 
                      dim = c(length(row_names), length(col_names), length(mat_names)),
                      dimnames = list(row_names, col_names, mat_names)
                    )
                    
                    # printing row 2 of matrix 1 using the index
                    print(arr[2,,1])
                    
                    # printing row 3 of matrix 2 using the name
                    print(arr["row 3",,"matrix 2"])
                    
                    # printing the col 1 of matrix 1 using the name
                    print(arr[,"col 1","matrix 1"])
                    
                    # printing the col 2 of matrix 2 using the index
                    print(arr[,2,2])
                    
                    cat("\014")
                    
                    Output:
                    col 1 col 2  # arr[2,,1]
                        3     6 
                        
                    col 1 col 2 # arr["row 3",,"matrix 2"]
                       10    13 
                    
                    row 1 row 2 row 3 # arr[,"col 1","matrix 1"]
                        2     3     4 
                        
                    row 1 row 2 row 3 # arr[,2,2]
                       11    12    13 
                    ```
                    
            - Accessing elements individually
                - To access a element individually we must need all three index
                    
                    ```r
                    row_names <- c("row 1", "row 2", "row 3")
                    col_names <- c("col 1", "col 2")
                    mat_names <- c("matrix 1", "matrix 2")
                    
                    arr <- array(
                        data = 2:20, 
                        dim = c(length(row_names), length(col_names), length(mat_names)),
                        dimnames = list(row_names, col_names, mat_names)
                        )
                    
                    print(arr)
                    
                    # printing the element on the 2nd row of the 1st column of the 
                    # 1st matrix
                    print(arr[2,1,1])
                    
                    # printing the element on the 3rd row of the 2nd column of the 
                    # 2nd matrix
                    print(arr["row 3", "col 2", "matrix 2"])
                    
                    cat("\014")
                    
                    Output:
                    , , matrix 1
                    
                          col 1 col 2
                    row 1     2     5
                    row 2     3     6
                    row 3     4     7
                    
                    , , matrix 2
                    
                          col 1 col 2
                    row 1     8    11
                    row 2     9    12
                    row 3    10    13
                    
                    [1] 3 # arr[2,1,1]
                    
                    [1] 13 # arr["row 3", "col 2", "matrix 2"]
                    ```
                    
            - Accessing subset of array elements
                - To access a subset of an array (more than one row or one col etc.), we must use c() function inside the index of the array
                    
                    ```r
                    row_names <- c("row 1", "row 2", "row 3")
                    col_names <- c("col 1", "col 2")
                    mat_names <- c("matrix 1", "matrix 2")
                    
                    arr <- array(
                      data = 2:20, 
                      dim = c(length(row_names), length(col_names), length(mat_names)),
                      dimnames = list(row_names, col_names, mat_names)
                    )
                    
                    print(arr)
                    
                    # printing the elements on the 1st and 2rd rows 
                    # on the 2nd col of 1st matrix
                    print(arr[c(1, 3), 2, 1])
                    
                    # printing the elements on the 2nd row 
                    # on the 1st and 2nd cols of the 2nd matrix
                    print(arr["row 2", c("col 1", "col 2"), "matrix 2"])
                    
                    # printing the elements on the 1st and 3rd rows on the
                    # 1st and 2nd columns on the matrix 1
                    print(arr[c(1, 3), c(1, 2), 1])
                    
                    # printing all the elements that are on the 2nd column 
                    # and on the 1st and 3rd rows of both matrices 1 and 2
                    print(arr[c(1, 3), 2, c(1, 2)])
                    
                    cat("\014")
                    
                    Output:
                    row 1 row 3 # arr[c(1, 3), 2, 1]
                        5     7 
                    
                    col 1 col 2 # arr["row 2", c("col 1", "col 2"), "matrix 2"]
                        9    12 
                    
                          col 1 col 2 # arr[c(1, 3), c(1, 2), 1]
                    row 1     2     5
                    row 3     4     7
                    
                          matrix 1 matrix 2 # arr[c(1, 3), 2, c(1, 2)]
                    row 1        5       11
                    row 3        7       13
                    ```
                    
        - Adding elements
            - To add an element on an array we can only add on a row or on a column or on a matrix using c() function or using indexing or using append() function; these adding operations are the same for vector
                - OBS: if our array was built woth array(), these adding operations won’t happen
        - Removing elements
            - Same as vectors, but if our array was built with array() these operations won’t happen
        - Updating elements
            - To update an element on array we just need to access them and change them
            
            ```r
            row_names <- c("row 1", "row 2", "row 3")
            col_names <- c("col 1", "col 2")
            mat_names <- c("matrix 1", "matrix 2")
            
            arr <- array(
              data = 2:20, 
              dim = c(length(row_names), length(col_names), length(mat_names)),
              dimnames = list(row_names, col_names, mat_names)
            )
            
            arr[1,1,2] <- 89
            # changing a single element
            
            arr[1,,1] <- c(120, 800)
            # changing a row
            
            arr[,2,2] <- c(20, 25, 30)
            # changing a column
            
            print(arr)
            
            arr[,,1] <- 78:83
            # changing an entire matrix
            
            print(arr)
            
            cat("\014")
            
            Output:
            , , matrix 1
            
                  col 1 col 2
            row 1   120   800
            row 2     3     6
            row 3     4     7
            
            , , matrix 2
            
                  col 1 col 2
            row 1    89    20
            row 2     9    25
            row 3    10    30
            
            , , matrix 1
            
                  col 1 col 2
            row 1    78    81
            row 2    79    82
            row 3    80    83
            
            , , matrix 2
            
                  col 1 col 2
            row 1    89    20
            row 2     9    25
            row 3    10    30
            ```
            
    - Factors
        - Data structures that are implemented to categorize the data or represent categorical data and store it on multiple levels
        - Creation
            - To create a factor we use the factor() function
                - Parameters
                    - This function has 6 parameters
                    - The first one is the data itself, is the vector that needs to be converted into a factor
                    - The second ont is the Levels of the factor, is a set of distinct values which are given to the input vector x, is automatic
                    - The third are the Labels, is a string vector that basically name the levels and also modify the data based on these levels; by default the labels are the same as the levels
                    - The fourth is `exclude`, this parameter will mention all the values that you want to exclude; by default, exclude = NA
                    - The fifth is `ordered`, a logical atribute that decides wheter the levels are ordered; by default, ordered = is.ordered(first_parameter)
                    - The sixth is the nmax, the upper limit for the maximum number of levels; by default, nmax = NA
            
            ```r
            fac <- factor(c("Brazil", "Peru", "Ecuador", "Peru", "Brazil"))
            
            print(fac)
            
            levels(fac) <- c("DF", "Quito", "Lima")
            # adding labels using levels()
            
            print(fac)
            
            fac <- factor(fac, exclude = "DF")
            # excluding "DF" from the factor
            
            print(fac)
            
            fac <- factor(fac, ordered = TRUE)
            # ordering the factor
            
            print(fac)
            
            cat('\014')
            
            Output:
            [1] Brazil  Peru    Ecuador Peru    Brazil 
            Levels: Brazil Ecuador Peru
            
            [1] DF    Lima  Quito Lima  DF   
            Levels: DF Quito Lima
            
            [1] <NA>  Lima  Quito Lima  <NA> 
            Levels: Quito Lima
            
            [1] <NA>  Lima  Quito Lima  <NA> 
            Levels: Quito < Lima # Lima is a level above Quito
            ```
            
        - Accessing elements
            - To access an element we can use index, like in a vector
            
            ```r
            fac <- factor(c("Brazil", "Peru", "Ecuador", "Peru", "Brazil"))
            levels(fac) <- c("DF", "Quito", "Lima")
            
            print(fac[3])
            
            cat('\014')
            
            Output:
            [1] Quito
            Levels: DF Quito Lima
            ```
            
        - Modifying a factor
            - To modify a factor we just access it and assign a new value
                - We can also delete it by using the index with the negative symbol
            
            ```r
            fac <- factor(c("Brazil", "Peru", "Ecuador", "Peru", "Brazil"))
            levels(fac) <- c("DF", "Quito", "Lima")
            
            levels(fac) <- c(levels(fac), "Bogotá")
            # we need to add the new level first
            
            fac[3] <- "Bogotá"
            
            print(fac)
            
            fac <- fac[-2]
            
            print(fac)
            
            cat('\014')
            
            Output:
            
            [1] DF     Lima   Bogotá Lima   DF    
            Levels: DF Quito Lima Bogotá
            
            [1] DF     Bogotá Lima   DF    
            Levels: DF Quito Lima Bogotá
            ```
            
    - Data-Frames
        - Used to store tabular data
            - Example
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2048.png)
                
        - Creation
            - To create a data frame, we use the function data.frame()
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2049.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2050.png)
                
                - Example
                    
                    ```r
                    # R program to create dataframe
                     
                    # creating a data frame
                    friend.data <- data.frame(
                        friend_id = c(1:5), 
                        friend_name = c("Sachin", "Sourav", 
                                        "Dravid", "Sehwag", 
                                        "Dhoni"),
                        stringsAsFactors = FALSE
                    )
                    # print the data frame
                    print(friend.data)
                    ```
                    
        - Get
            - We can use str() function
            - Example
                
                ```r
                # creating a data frame
                friend.data <- data.frame(
                    friend_id = c(1:5), 
                    friend_name = c("Sachin", "Sourav", 
                                    "Dravid", "Sehwag", 
                                    "Dhoni"),
                    stringsAsFactors = FALSE
                )
                # using str()
                print(str(friend.data))
                
                Output:
                'data.frame':	5 obs. of  2 variables:
                 $ friend_id  : int  1 2 3 4 5
                 $ friend_name: chr  "Sachin" "Sourav" "Dravid" "Sehwag" ...
                NULL
                ```
                
        - Summary
        - Extract data
        - Expand data
        - Accessing items
        - Amount of rows and columns
        - Add rows and columns
        - Remove rows and columns
        - Combining data frames
            - Vertically
            - Horizontally
- Input
    - To read an input we can use the functions scan() or readline()
    - readline()
        - readline() always convert the input to a string, so we need to use as.data_type to convert
        - If we want multiple inputs we can use brackets and put readlines inside it
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2051.png)
            
        - Inside the function we can write a prompt, like the input function in python
    - scan()
        - Takes input continuously, to terminate the input process we need to press enter key 2 times on the console
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2052.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2053.png)
            
        - We can specify the type of input with an argument called “what” and then the data type function
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2054.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2055.png)
            
        - Also, we can read files with this method
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2056.png)
            
- Output
    - On R we have the print() function to output, it can print a string or a variable
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2057.png)
        
        - We can use the method paste() inside the print() function to print output with string and variable together (there is also paste0() that basically doens’t add a whitespace “between” the commas)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2058.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2059.png)
            
        - Arguments
            - quote: we can take it off the quotes (if we are printing a string or char) by simply putting quote = FALSE
            - digits: we can define the minimal number of significant digits
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2060.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2061.png)
                
            - na.print: indicates what it will prints if thw value is NA
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2062.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2063.png)
                
    - Also, we can print just by writting on the console the name of the variable
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2064.png)
        
    - Another function to output is sprintf(), that is literally a C library function with data specifiers
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2065.png)
        
    - Another way to output is using the cat() function that is basically the print() + paste() functions together (converts the arguments to character strings)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2066.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2067.png)
        
    - Another way is using message() but this function it’s not used for print output but it’s used for showing simple diagbostic messages which are no warnings or errors in the program but it can be used for normal output
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2068.png)
        
    - Also, we can write a file with the output of our program using write() using a option called table to write a file
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2069.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2070.png)
        
    - To clear the terminal on RStudio we can use cat(”\014”)
- Comments
    - Can be done using #, only single line comments are supported
    - But we can do comments with more than one line using this trick:
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2071.png)
        
        - output: [1] “This is fun!”
- Operators
    - Arithmetical
        - +(sum), - (subtraction), * (multiplication), / (division), ^ (power), %% (module), %/% (quotient)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2072.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2073.png)
            
    - Logical
        - Logical operators in R simulate element-wise decision operations, based on the specified operator between the operands, which are then evaluated to either a True or False boolean value. Any non-zero integer value is considered as a TRUE value, be it a complex or real number.
        - Element-wise
            - And (&) - any non zero integer value is considered as a TRUE value
            - Or (|)
        - Not (!), And (&&), Or (||)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2074.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2075.png)
        
    - Relational
        - < (less than), <= (less than equal to), > (greater than), >= (greater than equal to), != (not equal to), == (equals to)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2076.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2077.png)
        
    - Miscellaneous
        - %in%
            - Checks if an element belongs to a list and returns a boolean value
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2078.png)
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2079.png)
                
        - %*%
            - Operator to multiply a matrix with its transpose
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2080.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2081.png)
            
- Conditionals
    - There are if’s, else if’s and else’s and the structure is similar to C/C++
    - Example
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2082.png)
        
    - OBS: the else if’s and else’s need to be strictly after the brackets; otherwise it won’t run
- Switch-case statement
    - It’s a conditional statement expression that has a list of cases, if a match is found then something happens
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2083.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2084.png)
        
    - The cases can be anything, like outputs
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2085.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2086.png)
        
        - If we atribute a variable to a switch-case statement, it will return NULL value
    - If we want a default case, we can just don’t put that anything equals to
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2087.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2088.png)
        
- Loops
    - For
        - It’s a loop that it’s executed a finite amount of times until exit condition is reached; very commom to be used for iterate over the elements
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2089.png)
            
        - We can iterate over a variable
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2090.png)
            
        - We can use to create plots
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2091.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2092.png)
            
    - While
        - Run a statement repeatedly unless the given condition becomes false
        - The condition is checked first and then the code inside the while will run
        
        ```r
        # R program to demonstrate the use of while loop 
        
        val = 1 
        
        # using while loop 
        while (val <= 5 ) { 
        	# statements 
        	print(val) 
        	val = val + 1 
        } 
        
        # Output
        [1] 1
        [1] 2
        [1] 3
        [1] 4
        [1] 5
        ```
        
    - Break
        - Is a jump statement that is used to terminate the loop at a particular iteration
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2093.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2094.png)
            
    - Next
        - Is used to skip any remaining statements in the loop and continue the execution of the program, it is a statement that skips the current iteration without loop termination
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2095.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2096.png)
            
    - Repeat
        - It’s a loop that can be iterated many number of times but has no exit condition, so we have to create one inside this repeat-loop using break to come out of the loop
        
        ```r
        # R program to demonstrate the use of repeat loop 
        
        val = 1 
        
        # using repeat loop 
        repeat { 
        	# statements 
        	print(val) 
        	val = val + 1 
        	
        	# checking stop condition 
        	if(val > 5) { 
        		# using break statement 
        		# to terminate the loop 
        		break
        	} 
        } 
        
        # Output
        [1] 1
        [1] 2
        [1] 3
        [1] 4
        [1] 5
        ```
        
    - Nested loops
        - Loops inside of loops
- Keywords
    - TRUE and FALSE
    - Function: used to create functions
    - NULL: used to represent the missing and undefined values, neither TRUE or FALSE
    - NaN: “Not a Number”
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2097.png)
        
    - Inf: keyword to negative or positive infinity, function is.finite and is.infinite
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2098.png)
        
    - NA: “Not Available”, used to represent the missing values
- Functions
    - Accepts arguments and can return values
    - Syntax to create a function
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%2099.png)
        
        - The arguments don’t need to have his data type specified
            - If we want to specify we need to check inside the function the data type of the argument, using is.data_type()
        - Example
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20100.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20101.png)
            
        - We can have default arguments inside the function
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20102.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20103.png)
            
        - Other functions can be passed as arguments, and a function can have 0 arguments also
    - Types
        - Primitive
        - Infix
            - Are those functions in which the function name comes in between its arguments and have only two arguments
                - It’s basically an operator, but we are defining it using functions
            - Example
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20104.png)
                
                - This function print who is greater than who; if both numbers are equal prints equal
                
                ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20105.png)
                
        - Replacement
    - Return
        - Keyword used to return some value inside functions
        - The return value needs to be inside parenthesis
    - Recursive functions
        - Functions that the return returns the function itself
        - Example
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20106.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20107.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20108.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20109.png)
            
    - Some built-in functions
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20110.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20111.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20112.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20113.png)
        
- POO
- Error Handling
- File Handling
- Packages
- Data interfaces (REFAZER)
    - Import files
        - To import files in R we use read.table(*filename, header = FALSE, sep = “”*)
        - To import csv files, we use read.csv(*filename, header = FALSE, sep = “”*)
            - To get a specific item we use $
- Data visualization (REFAZER)
    - barplot()
        - Have a parameter which is if the bar plot is horizontal or vertical
        - Example
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20114.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20115.png)
            
        - Good to perform a comparative study between the various dara categories in the data set
    - hist()
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20116.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20117.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20118.png)
        
        ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20119.png)
        
    - boxplot()
    - plot()
        - Many points on a Cartesian plane, each point denotes the value taken by two parameters and helps us easily identify the relationship between them
        - Parameters
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20120.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20121.png)
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20122.png)
            
        - Example
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20123.png)
            
        - Example
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20124.png)
            
        - Adding title, color and labels
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20125.png)
            
        - Multiple lines
            
            ![Untitled](../../../assets/faculdade/periodo2/estatistica-probabilidade-p-computacao/r/Untitled%20126.png)
            
    - heatmap()
    - map()
    - persp()
    - table()
    - pie()
- Statistics (REFAZER)
    - Mean
        - To calculate the arithmetic mean, we use mean()
    - Median
        - To calculate the median, we use median()
    - Mode
        - There is no built-in function for mode, so we need to create
        - There is the package modeest, that has the function mfv()
    - Standart deviation
        - We use sd()
    - Variance
        - We use var() or sd() ^ 2
    - Range
        - We can do max(data) - min(data)
    - Quartile
        - We use quantile()
        - Interquartile range
            - We use IQR()
    - Summary
        - Using summary() we can access several statistic summaries of either one variable or an entire data frame
    - Normal distribution
        - We can use dnorm(), pnorm(), qnorm() and rnorm(); probably the most useful are dnorm() (better) and rnorm()
            - The parameters are the data, the mean and the sd
    - Binomial distribution
    - T-Student distribution
        - We can use dt(), pt(), qt() and rt() (i think the best may be qt())
    - Skewness
        - We use skewness() (from moments), if the function returns > 0 so the graph is positively skewed (asymmetric) if returns 0 or close to zero the graph is symmetric and normally distributed, else the graph is negatively skewed
    - Kurtosis
        - Not a built-in function but with the package moments we can use it
    - Hypothesis testing
- Machine learning