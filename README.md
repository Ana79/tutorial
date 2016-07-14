# a special "matrix" object that can cache its inverse.#
makeCacheMatrix <- function(x = matrix()) {
## set the matrix
inverse <-NULL
setmatrix<-function(matrix){
m<<-matrix
}
## get the matrix
getMatrix<-function() m
## set the inverse
setInverse<-function(temp){
inverse<<-temp
}
## get the inverse if the matrix is square
getInverse<-function(){
if (nrow(m) != ncol(m)) {print('matrix is not square')}
inverse
}

list(setMatrix=setMatrix,getMatrix=getMatrix,setInverse=setInverse,getInverse=getInverse)

}
#This function computes the inverse of the special "matrix" returned by makeCacheMatrix#
cacheSolve <- function(x) {
inverse<-m$getInverse()
if (!is.null(inverse)){
## get it from the cache and skips the computation.
message("getting cached data")
return(inverse)
}
## sets the value of the inverse in the cache via the setinv function.
inverse<-solve(m$getMatrix())
m$cacheInverse(inverse)
inverse
}

