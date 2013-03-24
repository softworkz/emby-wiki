Plugins are able to create their own api endpoints, whether it be for their own consumption, or for the purposes of publishing them to UI developers. This will demonstrate how to build an api endpoint.

Media Browser's api layer is built with **Service Stack**, so their examples are directly applicable.

## Create the Service
Create a class that implements IRestfulService.

You will then have to create request dto classes that describe the request. The following is a complete service example:

`

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
`

WeatherService is the service that processes the request. GetWeather is api method. The route attribute describes the url and http method.

The Get method should return an object that is one of the following:

* object to be serialized
* string (plain text)
* byte array (to be written to the response stream)
* stream (to be copied to the response stream)

The Api and ApiMember attributes, as well as IReturn are all optional. They only serve to improve documentation.

## Advanced Options
If you need http compression, response caching, or the ability to set custom response headers, extend your Service to implement **IHasResultFactory**. This will add a ResultFactory property to your service. You can then call ResultFactory.GetResult, or some of the other more advanced result methods.