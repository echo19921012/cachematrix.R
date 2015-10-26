# cachematrix.R
makeCacheMatrix <- function(x = matrix()) {
        inverse <- NULL
 
        setMatrix <- function(matrix = matrix()){
                x <<- matrix
        }
 
        getMatrix <- function() x
 
        setInverse <- function(inverseMatrix = matrix()){ 
                inverse <<- inverseMatrix
        } 
        getInverse <- function() inverse
        list(get = getMatrix, set = setMatrix, getI = getInverse, setI = setInverse)
}
 
cacheSolve <- function(x, ...) {
        ## Return a matrix that is the inverse of 'x' 
 
        if(is.null(x$getI())){
                print("Not cached. Recomputing...") 
                x$setI(solve(x$get()))
        }else {print("Found in cache")}
 
        x$getI()
}
