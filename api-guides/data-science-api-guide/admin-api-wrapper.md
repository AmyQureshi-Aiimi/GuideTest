# Admin API Wrapper

The Admin API Wrapper is designed primarily for the AI Enrichment, Model and Classification services and is used by them to register as services. It may help when creating custom enrichment steps, it has methods to get service registrations and configure AI Model Server wrappers.&#x20;

## Initialisation&#x20;

`AdminAPI(host: str, system_secret: str, verify: bool)`&#x20;

* **Parameters:**&#x20;
  * `host`: A string representing the Admin API URI.&#x20;
  * `system_secret`: A system secret used for authorisation.&#x20;
  * `verify`: A boolean indicating whether to verify SSL certificates.&#x20;

### Methods&#x20;

`register_service(configuration_registration: dict) -> dict` \
Registers a service with the Admin API.&#x20;

* **Parameters:**&#x20;
  * `configuration_registration`: A dictionary containing the configuration details for the service registration.&#x20;
* **Returns:**&#x20;
  * A dictionary containing the registered service configuration.&#x20;
* **Raises:**&#x20;
  * Exception: If the registration fails, an exception is raised with the status code and response text.&#x20;

`get_aie_settings() -> dict`\
Retrieves the Workplace AI settings.&#x20;

* **Returns:**&#x20;
  * A dictionary containing the Workplace AI settings.&#x20;
* **Raises:**&#x20;
  * Exception: If the retrieval fails, an exception is raised with the status code and response text.&#x20;

`get_service_registration(service_id: str) -> dict | None` \
Fetches the registration details for a specific service.&#x20;

* **Parameters:**&#x20;
  * `service_id`: A string representing the ID of the service.&#x20;
* **Returns:**&#x20;
  * A dictionary containing the service registration details, or None if the service is not found.&#x20;

`get_model_server(service_id: str) -> ModelServer`\
Retrieves a ModelServer instance for a given service ID.&#x20;

* **Parameters:**&#x20;
  * `service_id`: A string representing the ID of the service.&#x20;
* **Returns:**&#x20;
  * An instance of ModelServer.&#x20;
* **Raises:**&#x20;
  * Exception: If the service ID is invalid or the service type is not AIModelService.&#x20;

`get_generative_model(service_id: str, provider_id: str, model_parameters: dict) -> GenerativeModel` \
Obtains a GenerativeModel instance based on the provided service and provider IDs, and model parameters.&#x20;

* **Parameters:**&#x20;
  * `service_id`: A string representing the ID of the service.&#x20;
  * `provider_id`: A string representing the ID of the provider.&#x20;
  * `model_parameters`: A dictionary containing parameters for the model.&#x20;
* **Returns:**&#x20;
  * An instance of GenerativeModel.&#x20;
* **Raises:**&#x20;
  * `ValueError`: If the provider\_id is empty.&#x20;
  * Exception: If the service ID is invalid or the service type is not AIModelService.&#x20;

`get_generative_model_from_parameter(ai_model_parameter: str) -> GenerativeModel`\
Returns a GenerativeModel wrapper from a parameter string for classification or enrichment parameters configured as 'AIModel' type.&#x20;

* **Parameters:**&#x20;
  * `ai_model_parameter`: A JSON string containing the parameters for the AI model, including aiModelServiceId, providerId, and modelParameters.&#x20;
* **Returns:**&#x20;
  * An instance of GenerativeModel.&#x20;
* **Notes:**&#x20;
  * This method parses the ai\_model\_parameter string into a dictionary and uses it to retrieve the generative model.&#x20;
