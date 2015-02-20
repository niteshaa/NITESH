# NITESH
NITESH

# makeCacheMatrix is a function that returns a list of functions
# Its puspose is to store a martix and a cached value of the inverse of the 
# matrix.

makeCacheMatrix <- function(x = numeric()) {
        
        # holds the cached value or NULL if nothing is cached
        # initially set to null as nothing is there,
        cache <- NULL
        
        # store a matrix
        setMatrix <- function(newValue) {
                x <<- newValue
                cache <<- NULL
        }
        getMatrix <- function() {
                x
        }
        cacheInverse <- function(solve) {
                cache <<- solve
        }
        getInverse <- function() {
                cache
        }
        list(setMatrix = setMatrix, getMatrix = getMatrix, cacheInverse = cacheInverse, getInverse = getInverse)
}


# The following function calculates the inverse of a "special" matrix created with 
cacheSolve <- function(y, ...) {
        # get the cached value
        inverse <- y$getInverse()
        if(!is.null(inverse)) {
                message("getting cached data")
                return(inverse)
        }
        data <- y$getMatrix()
        inverse <- solve(data)
        y$cacheInverse(inverse)
        
               inverse
}
