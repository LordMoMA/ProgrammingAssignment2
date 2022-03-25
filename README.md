
# Programming Assignment 2: Lexical Scoping

## [R Programming](https://www.coursera.org/course/rprog)

Assignment: Caching the Inverse of a Matrix

Matrix inversion is usually a costly computation and there may be some benefit to caching the inverse of a matrix rather than computing it repeatedly (there are also alternatives to matrix inversion that we will not discuss here). Your assignment is to write a pair of functions that cache the inverse of a matrix.

Write the following functions:

makeCacheMatrix: This function creates a special "matrix" object that can cache its inverse.

cacheSolve: This function computes the inverse of the special "matrix" returned by makeCacheMatrix above. If the inverse has already been calculated (and the matrix has not changed), then cacheSolve should retrieve the inverse from the cache.

Computing the inverse of a square matrix can be done with the solve function in R. For example, if X is a square invertible matrix, then solve(X) returns its inverse.


	# create a *square* matrix (because `solve` only handles square matrices)
	# create the matrix during the call of makeCacheMatrix()
	
	a <- makeCacheMatrix( matrix(c(1,2,12,13), nrow = 2, ncol = 2) );

	summary(a);
	#>              Length Class  Mode    
	#> setMatrix    1      -none- function
	#> getMatrix    1      -none- function
	#> cacheInverse 1      -none- function
	#> getInverse   1      -none- function

	# create a square matrix 
	
	a$setMatrix( matrix(c(1,2,12,13), nrow = 2, ncol = 2) );
	a$getMatrix();
	#>      [,1] [,2]
	#> [1,]    1   12
	#> [2,]    2   13

	cacheSolve(a)
	#> [,1]        [,2]
	#> [1,] -1.1818182  1.09090909
	#> [2,]  0.1818182 -0.09090909

	# run it again, we get the cached value
	cacheSolve(a)
	#> getting cached data
	#> [,1]        [,2]
	#> [1,] -1.1818182  1.09090909
	#> [2,]  0.1818182 -0.09090909
