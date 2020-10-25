# Programming-Assignment-2-Lexical-Scoping
This is my assignment 2
#this function creates a special "matrix" object that can cache its inverse.
makechacheMatrix <- function(x=matrix()){
  j<- NULL
  set <- function(y){
    x <<- y
    j <<-NULL
  }
  get <- function()x
  setInverse <- function(inverse)j<<-inverse
  getInverse <- function()j
  list(set=set, get=get, setInverse=setInverse, 
       getInverse=getInverse)
}

#this function computes the inverse of the special "matrix" returned by makeCacheMatrix above.
cacheSolve <- function(x, ...){
  ## Return a matrix that is the inverse of 'x'
  j <- x$getInverse()
  if(!is.null(j)){
    message("getting cached data")
    return(j)
  }
  mat <- x$get()
  j <- solve(mat,...)
  x$setInverse(j)
  j
}

