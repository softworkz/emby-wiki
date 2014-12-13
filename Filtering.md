There is an api endpoint that you can use to return a fitler object containing the list of available filters.
 
GET /Items/Filters
 
Returns an object with:
 
- Genres
- Tags
- OfficialRatings
- Years
 
It accepts as params:
 
UserId
ParentId
IncludeItemTypes
MediaTypes
 
So for example, if you're showing a movie list, you can pass in the same params that you're using to retrieve the movies, and it will return a filter object containing lists of filters that can be displayed.