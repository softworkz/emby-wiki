Plugins are able to create their own api endpoints, whether it be for their own consumption, or for the purposes of publishing them to UI developers. This will demonstrate how to build an api endpoint.

Media Browser's api layer is built with **Service Stack**, so their examples are directly applicable.

## Create the Service
Create a class that implements IRestfulService.

You will then have to create request dto classes that describe the request. The following is a complete service example:

>     
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
            var result = Kernel.Instance.WeatherProviders.First().GetWeatherInfoAsync(request.Location, CancellationToken.None).Result;

            return result;
        }
    }