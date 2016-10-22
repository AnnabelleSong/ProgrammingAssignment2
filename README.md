##Assignment:Caching the Inverse of a Matrix:

\##Matrix inversion is usually a costly computation and there may be some benefit to caching 

\##the inverse of a matrix rather than compute it repeatedly.

\##So I write a pair of functions that cache the inverse of a matrix


```
makeCacheMatrix <- function(x = matrix()) {  
## This function creates a special "matrix" object that can cache its inverse.
      inve <- NULL
      set <- function(y) {
              x <<- y
              inve <<- NULL
  }
      get <- function() x
      setInverse <- function(inverse) inve <<- inverse
      getInverse <- function() inve
      list(set = set, get = get,
       setInverse = setInverse,
       getInverse = getInverse)
}
```


```
'cacheSolve <- function(x, ...) { 
## This function computes the inverse of the special "matrix" created by makeCacheMatrix above.
       inve <- x$getInverse()
       if (!is.null(inve)) {   ## check to see if the inverse has already been calculated
       message("getting cached data")  ##if so,then it should retrieve the inverse from the cache
       return(inve)
  }
      matr <- x$get()
      inve <- solve(matr, ...)
      x$setInverse(inve)
      inve
}
```
