Plugins are able to create their own api endpoints, whether it be for their own consumption, or for the purposes of publishing them to UI developers. This will demonstrate how to build an api endpoint.

Media Browser's api layer is built with **Service Stack**, so their examples are directly applicable.

## Create the Service
Create a class that implements IRestfulService. In order to do this you will have to add the ServiceStack.Common nuget package to your project.

You will then have to create request dto classes that describe the request. The following is a complete service example:


```c#
    [Route("/Weather", "GET")]
    [Api(Description = "Gets weather information for a given location")]
    public class GetWeather : IReturn<WeatherInfo>
    {
        [ApiMember(Name = "Location", Description = "Us zip / City, State, Country / City, Country", IsRequired = true, DataType = "string", ParameterType = "query", Verb = "GET")]
        public string Location { get; set; }
    }

    public class WeatherService : IRestfulService
    {
        public object Get(GetWeather request)
        {
            var result = GetWeatherInfo();

            return result;
        }
    }
```

WeatherService is the service that processes the request. GetWeather is the dto that describes the parameters. The route attribute describes the url and http method.

The Get method should return an object that is one of the following:

* object to be serialized
* string (plain text)
* byte array (to be written to the response stream)
* stream (to be copied to the response stream)

Other http methods are supported - Post, Put, Delete, etc.

The Api and ApiMember attributes, as well as IReturn are all optional. They only serve to improve documentation.

## Advanced Options
If you need http compression, response caching, or the ability to set custom response headers, extend your Service to implement **IHasResultFactory**. This will add a ResultFactory property to your service. 

The following are some of the methods available:

### GetResult
Gets a result object with the ability to specify a content type and response headers.

### GetOptimizedResult
Similar to GetResult, except that http compression is applied if the client supports it.

### GetOptimizedResultUsingCache
Similar to GetOptimizedResult, except that http caching headers will also be specified. You'll have to supply a function delegate to generate the response when the cache is not utilized.

### GetCachedResult
Use this in situations where you need http caching but do not want http compression, such as with images for example.

### GetStaticFileResult
Use this so serve a file statically from the file system.

### ThrowError
Throws an error with a specific response code and message.