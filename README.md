# a special "matrix" object that can cache its inverse.#
makeCacheMatrix <- function(m = matrix()) {
inverse <- NULL
set <- function(y) {
m <<- y
inverse <<- NULL
}
get <- function() m
setInverse <- function(solve) inverse <<- solve
getInverse <- function() inverse
list(set = set, get = get,
setInverse = setInverse,
getInverse = getInverse)
}

#This function computes the inverse of the special "matrix" returned by makeCacheMatrix#
cacheSolve <- function(m, ...) {
inverse <- m$getInverse()
if(!is.null(inverse)) {
message("getting cached data")
return(inverse)
}
data <- m$get()
inverse <- solve(data, ...)
m$setInverse(inverse)
inverse
}

This is my tutorial repository.
