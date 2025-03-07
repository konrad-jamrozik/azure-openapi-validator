# Azure Rules

There are a number of rules that can be validated with azure openapi validator, they are focused with Azure API specs ( ARM and/or Dataplane).

## Rules

### AdditionalPropertiesAndProperties

Don't specify both additionalProperties and properties in the same object schema. Only use additionalProperties to define "map" structures.

Please refer to [additional-properties-and-properties.md](./additional-properties-and-properties.md) for details.

### AdditionalPropertiesObject

Specifying `additionalProperties` with `type: object` is a common error.

Please refer to [additional-properties-object.md](./additional-properties-object.md) for details.

### AllProxyResourcesShouldHaveDelete

All proxy resources SHOULD support delete.

Please refer to [all-proxy-resources-should-have-delete.md](./all-proxy-resources-should-have-delete.md) for details.

### AllResourcesMustHaveGetOperation

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md) ,all the resources ,including top-level and nested resources, must have a get operation.

Please refer to [all-resources-must-have-get-operation.md](./all-resources-must-have-get-operation.md) for details.

### AllTrackedResourcesMustHaveDelete

All tracked resources MUST support delete.

Please refer to [all-tracked-resources-must-have-delete.md](./all-tracked-resources-must-have-delete.md) for details.

### AnonymousBodyParameter

This rule appears if in the parameter definition you have anonymous types.

Please refer to [anonymous-body-parameter.md](./anonymous-body-parameter.md) for details.

### ApiHost

The host is required for management plane specs.

Please refer to [api-host.md](./api-host.md) for details.

### ApiVersionEnum

The `api-version` parameter should not be an enum. This rule is primarily to discourage a practice observed
in some APIs of defining `api-version` as an enum with a single value -- the most current API version.
This requires removing the old API version when a new version is defined, which is disallowed by the breaking changes policy.

Please refer to [api-version-enum.md](./api-version-enum.md) for details.

### ApiVersionParameterRequired

Operation is missing the 'api-version' parameter.

Please refer to [api-version-parameter-required.md](./api-version-parameter-required.md) for details.

### APIVersionPattern

The API Version parameter MUST be in the Year-Month-Date format (i.e. 2016-07-04.)  NOTE that this is the en-US ordering of month and date.
The date MAY optionally be followed by one of:
* -preview - Indicates the API version is in (public) preview

Please refer to [api-version-pattern.md](./api-version-pattern.md) for details.

### ArmResourcePropertiesBag

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), top level properties should not be repeated inside the properties bag for ARM resources.

Please refer to [arm-resource-properties-bag.md](./arm-resource-properties-bag.md) for details.

### ArrayMustHaveType

An array must claim "type:'array'" explicitly.

Please refer to [array-must-have-type.md](./array-must-have-type.md) for details.

### ArraySchemaMustHaveItems

A schema of `array` type must always contain an `items` property. without it, AutoRest will fail to generate an SDK.

Please refer to [array-schema-must-have-items.md](./array-schema-must-have-items.md) for details.

### AvoidAnonymousTypes

This rule appears when you define a model type inline, rather than in the definitions section. If the model represents the same type as another parameter in a different operation, then it becomes impossible to reuse that same class for both operations.

Please refer to [avoid-anonymous-types.md](./avoid-anonymous-types.md) for details.

### AvoidEmptyResponseSchema

Response schema must not be empty, or it will block code generation.

Please refer to [avoid-empty-response-schema.md](./avoid-empty-response-schema.md) for details.

### AvoidMsdnReferences

The documentation is being generated from the OpenAPI(swagger) and published at "docs.microsoft.com". From that perspective, documentation team would like to avoid having links to the "msdn.microsoft.com" in the OpenAPI(swagger) and SDK documentations.

Please refer to [avoid-msdn-references.md](./avoid-msdn-references.md) for details.

### AvoidNestedProperties

Nested properties can result into bad user experience especially when creating request objects. `x-ms-client-flatten` flattens the model properties so that the users can analyze and set the properties much more easily.

Please refer to [avoid-nested-properties.md](./avoid-nested-properties.md) for details.

### AzureResourceTagsSchemaValidation

This rule is to check if the tags definition of a resource conforms to the common tags definition.

Please refer to [azure-resource-tags-schema-validation.md](./azure-resource-tags-schema-validation.md) for details.

### BodyPropertiesNamesCamelCase

This violation is flagged if a request body parameter's property name (BodyPropertiesNamesCamelCase) is not in `camelCase` format. This is because the model's properties are sent across the wire and must adhere to common Json conventions for naming. This implies that every property name must start with a lower cased letter and all subsequent words within the name must start with a capital letter. In cases where there are acronyms involved, a maximum of three contiguous capital letters are allowed (acronyms should not be longer that 2 characters - see https://msdn.microsoft.com/en-us/library/141e06ef(v=vs.71).aspx, third upper case could be start of next word). Eg: `redisCache`, `publicIPAddress`, `location` are valid, but `sampleSQLQuery` is not (must be renamed as `sampleSqlQuery`).

Please refer to [body-properties-names-camel-case.md](./body-properties-names-camel-case.md) for details.

### BodyTopLevelProperties

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), top level properties of a resource should be only ones from the allowed set.

Please refer to [body-top-level-properties.md](./body-top-level-properties.md) for details.

### BooleanPropertyNotRecommended

Booleans may not be descriptive enough to use in the case. Instead, consider using string enums with allowed set of values defined..

Please refer to [boolean-property.md](./boolean-property.md) for details.

### CollectionObjectPropertiesNaming

Per ARM guidelines, a model returned by an `x-ms-pageable` operation must have a property named `value`. This property indicates what type of array the object is.

Please refer to [collection-object-properties-naming.md](./collection-object-properties-naming.md) for details.

### ConsistentPatchProperties

The properties in the patch body must be present in the resource model and follow json merge patch.

Please refer to [consistent-patch-properties.md](./consistent-patch-properties.md) for details.

### ConsistentResponseBody

The standard pattern for REST operations is that a create (PUT), read (GET), and update (PATCH) all return
a representation of the resource.
For a path with a "create" operation (put or patch that returns 201), the 200 response of get, put, and patch, if present,
should have the same response body schema as the create operation 201 response.

Please refer to [consistent-response-body.md](./consistent-response-body.md) for details.

### ControlCharactersNotAllowed

Verifies whether if a specification does not have any control characters in it.
Control characters are not allowed in a specification.

Please refer to [control-characters-not-allowed.md](./control-characters-not-allowed.md) for details.

### CreateOperationAsyncResponseValidation

An async PUT operation response include status code 201 with 'Azure-async-operation' header. Must also support status code 200, for simple updates that can be completed synchronously (ex: tags). Operation must also add "x-ms-long-running-operation and x-ms-long-running-operation-options" to mark that it is a long running operation (in case of 201) and how it is tracked (Azure-async-operation header).

Please refer to [create-operation-async-response-validation.md](./create-operation-async-response-validation.md) for details.

### DefaultErrorResponseSchema

The default error response schema SHOULD correspond to the schema documented at [common-api-details](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/common-api-details.md#error-response-content).

Please refer to [default-error-response-schema.md](./default-error-response-schema.md) for details.

### DefaultInEnum

This rule applies when the default value specified by the property does not appear in the enum constraint for a schema.

Please refer to [default-in-enum.md](./default-in-enum.md) for details.

### DefaultMustBeInEnum

The value assigned as a default for an enum property must be present in the enums' list.

Please refer to [default-must-be-in-enum.md](./default-must-be-in-enum.md) for details.

### DefaultResponse

All operations should have a default (error) response.

Please refer to [default-response.md](./default-response.md) for details.

### DefinitionsPropertiesNamesCamelCase

Property names must use lowerCamelCase style.
If the property is a single word (ex: foo, bar, etc.) it will be all lowercase. 
Two-letter acronyms (ex: ID, IO, IP, etc.) should be capitalized. 
Three-letter acronyms (ex: API, URL, etc.) should only have the first letter capitalized (ex: Api, Url, etc.) 
For more capitalization guidance, see: [https://msdn.microsoft.com/en-us/library/141e06ef(v=vs.71).aspx](https://msdn.microsoft.com/en-us/library/141e06ef(v=vs.71).aspx)

Please refer to [definitions-properties-names-camel-case.md](./definitions-properties-names-camel-case.md) for details.

### DeleteInOperationName

Verifies whether value for `operationId` is named as per ARM guidelines.

Please refer to [delete-in-operation-name.md](./delete-in-operation-name.md) for details.

### DeleteMustNotHaveRequestBody

The request body of a delete operation must be empty.

Please refer to [delete-must-not-have-request-body.md](./delete-must-not-have-request-body.md) for details.

### DeleteOperationAsyncResponseValidation

An async DELETE operation response include status code 202 with 'Location' header. Must support status code 200 if operation can be completed synchronously. Must support 204 (resource doesn't exists). Operation must also add "x-ms-long-running-operation and x-ms-long-running-operation-options" to mark that it is a long running operation (in case of 202) and how it is tracked (Location header).

Please refer to [delete-operation-async-response-validation.md](./delete-operation-async-response-validation.md) for details.

### DeleteOperationResponses

Per ARM Specs, all DELETE methods (non-async) must have responses code implementation: 200, 204.

Please refer to [delete-operation-responses.md](./delete-operation-responses.md) for details.

### DeleteResponseBodyEmpty

The delete response body must be empty.

Please refer to [delete-response-body-empty.md](./delete-response-body-empty.md) for details.

### Delete204Response

A delete operation should have a 204 response.

Please refer to [delete204-response.md](./delete204-response.md) for details.

### DeprecatedXmsCodeGenerationSetting

The x-ms-code-generation-settings is being deprecated. AutoRest (v3) is using settings in readme file for code generation and will stop supporting it inside the swagger file. Please ensure to remove the parameter from swagger spec and move settings to readme.

Please refer to [deprecated-xms-code-generation-setting.md](./deprecated-xms-code-generation-setting.md) for details.

### DescriptionAndTitleMissing

The definition must have at least one of the properties - description/title.

Please refer to [description-and-title-missing.md](./description-and-title-missing.md) for details.

### DescriptionMustNotBeNodeName

Description section must provide details on the current operation or model. Using the name of node in description does not provide any value.

Please refer to [description-must-not-be-node-name.md](./description-must-not-be-node-name.md) for details.

### DescriptiveDescriptionRequired

The value of the 'description' property must be descriptive. It cannot be spaces or empty description.

Please refer to [descriptive-description-required.md](./descriptive-description-required.md) for details.

### docLinkLocale

This rule is to ensure the documentation link in the description does not contains any locale.

Please refer to [doc-link-locale.md](./doc-link-locale.md) for details.

### EnumInsteadOfBoolean

Booleans properties are not descriptive in all cases and can make them to use, evaluate whether is makes sense to keep the property as boolean or turn it into an enum.

Please refer to [enum-instead-of-boolean.md](./enum-instead-of-boolean.md) for details.

### EnumMustHaveType

Enum must define type, and type must not be object. Or it will fail SDK auto-generation.

Please refer to [enum-must-have-type.md](./enum-must-have-type.md) for details.

### EnumMustNotHaveEmptyValue

Enum must not be empty, or contain special character, like space, tab, etc. It will lead to code generation failure in downstream pipeline.

Please refer to [enum-must-not-have-empty-value.md](./enum-must-not-have-empty-value.md) for details.

### EnumMustRespectType

This rule is to check if the enum values conform to the type.

Please refer to [enum-must-respect-type.md](./enum-must-respect-type.md) for details.

### EnumUniqueValue

Enum must not contain duplicated value (case insensitive).

Please refer to [enum-unique-value.md](./enum-unique-value.md) for details.

### ErrorResponse

Error response body should conform to [Azure API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/azure/Guidelines.md#handling-errors).

Please refer to [error-response.md](./error-response.md) for details.

### ExtensionResourcePathPattern

Path (operation) for 'extension routing type' (that has additional /providers/ segment in parent scope) must be of the form '{scope}/provider/RPNamespace/resourceTypeName' (shouldn't include parent scope)

Please refer to [extension-resource-path-pattern.md](./extension-resource-path-pattern.md) for details.

### FormData

It can be appropriate to use formData parameters when sending multiple file-type parameters or an array of file-type parameters.
But it is usually unnecessary and can be overly complicated to use formData when all you are doing is sending a single file-type parameter.
Instead, consider defining a `body` parameter with `type: string, format: binary` and use content-type `application/octet-stream`.

Please refer to [formdata.md](./formdata.md) for details.

### GetCollectionResponseSchema

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md#get-resource), for all resources (top-level and nested), collection GETs should have a response definition with a property "value" containing an array of the "resource" schema.The definition returned in the collection "value" array should be the same as the response body for the individual GET.

Please refer to [get-collection-response-schema.md](./get-collection-response-schema.md) for details.

### GetInOperationName

Verifies whether value for `operationId` is named as per ARM guidelines.

Please refer to [get-in-operation-name.md](./get-in-operation-name.md) for details.

### GetMustNotHaveRequestBody

The request body of a get operation must be empty.

Please refer to [get-must-not-have-request-body.md](./get-must-not-have-request-body.md) for details.

### GetOperation200

The get operation should only return 200, also it should not be a long running operation.

Please refer to [get-operation200.md](./get-operation200.md) for details.

### GuidUsage

Verifies whether format is specified as "uuid" or not.

Please refer to [guid-usage.md](./guid-usage.md) for details.

### HeaderDisallowed

Authorization, Content-type, and Accept headers should not be defined explicitly.

Please refer to [header-disallowed.md](./header-disallowed.md) for details.

### HostParametersValidation

This is to validate if parameters in the 'x-ms-parameterized-host' follow the following rules::
1. If a parameter matches belows, therefore it must be called 'endpoint' and be typed 'type:string, format:url'.
   - Client level (x-ms-parameter-location: client)
   - A path component (in: path)
   - Part of a 'x-ms-parametrized-host' with 'useSchemePrefix: false'
   - Tagged 'x-ms-skip-encoding: true'

Please refer to [host-parameters-validation.md](./host-parameters-validation.md) for details.

### HttpsSupportedScheme

Verifies whether specification supports HTTPS scheme or not.

Please refer to [https-supported-scheme.md](./https-supported-scheme.md) for details.

### ImplementPrivateEndpointAPIs

This rule is to check if all the APIs for private endpoint are implemented. Per design spec, for supporting private endpoint, the service should implement the following APIs:
PUT/DELETE/GET https://management.azure.com/subscriptions/{subscriptionId}/resourceGroups/{groupName}/providers/Microsoft.[Service]/{resourceType}/{resourceName}/privateEndpointConnections/{privateEndpointConnectionName}?api-version=[version]
GET https://management.azure.com/subscriptions/{subId}/resourceGroups/{rgName}/providers/Microsoft.[Service]/[resources]/{resourceName}/privateEndpointConnections?api-version=[version]
GET https://management.azure.com/subscriptions/{subscriptionId}/resourceGroups/{groupName}/providers/Microsoft.[Service]/[resources]/[resourceName]/privateLinkResources?api-version=[version]

Please refer to [implement-private-endpoint-ap-is.md](./implement-private-endpoint-ap-is.md) for details.

### IntegerTypeMustHaveFormat

The type:integer must have a required format. Possible value for format are int32 and int64.

Please refer to [integer-type-must-have-format.md](./integer-type-must-have-format.md) for details.

### InvalidSkuModel

Sku model definition needs to follow [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md) and can contain only a certain set of properties as described in the message.

Please refer to [invalid-sku-model.md](./invalid-sku-model.md) for details.

### InvalidVerbUsed

Each operation definition must have a HTTP verb and it must be DELETE/GET/PUT/PATCH/HEAD/OPTIONS/POST/TRACE.

Please refer to [invalid-verb-used.md](./invalid-verb-used.md) for details.

### LicenseHeaderMustNotBeSpecified

`x-ms-code-generation-settings` must not have the license section specified in the OpenAPI documents since each generated SDK can have a different licensing header. This information must be provided either from the command line or the configuration file when actually generating the sdk.

Please refer to [license-header-must-not-be-specified.md](./license-header-must-not-be-specified.md) for details.

### ListInOperationName

Verifies whether value for `operationId` is named as per ARM guidelines when response contains array of items.

Please refer to [list-in-operation-name.md](./list-in-operation-name.md) for details.

### LocationMustHaveXmsMutability

A tracked resource's `location` property must have the `x-ms-mutability` properties set as `read`, `create`.

Please refer to [location-must-have-xms-mutability.md](./location-must-have-xms-mutability.md) for details.

### LongRunningOperationsOptionsValidator

This is a rule introduced to make the understanding of Long Running Operations more clear.
In case of LRO Post operation with return schema, it MAY be ambiguous for the SDK to understand automatically what the return schema is modeling. To avoid any confusion that would lead SDK to incorrectly instantiate the return type, service team needs to explain if the return schema is modeling a result from a "Location" header, or from an "Azure-AsyncOperation" header.
More details on LRO operation could be found [here](https://github.com/Azure/autorest/blob/main/docs/extensions/readme.md#x-ms-long-running-operation)

Please refer to [long-running-operations-options-validator.md](./long-running-operations-options-validator.md) for details.

### LongRunningOperationsWithLongRunningExtension

Per [x-ms-long-running-operation](https://github.com/Azure/autorest/tree/main/docs/extensions.md#x-ms-long-running-operation) ,The operation which returns 202 status code indicates a long running operation. Every long running operation must have the x-ms-long-running-operation enabled.

Please refer to [long-running-operations-with-long-running-extension.md](./long-running-operations-with-long-running-extension.md) for details.

### LongRunningResponseStatusCode

For ARM spec, the allowed response status codes for a long DELETE operation are "200" & "204"; the allowed response status codes for a POST operation are "200", "201" ,"202", & "204"; the allowed response status codes for a PUT/PATCH operation are "200" & "201".
For Data plane spec, the allowed response status codes for a long DELETE operation are "200","202", & "204"; the allowed response status codes for a POST operation are "200", "201" ,"202", & "204"; the allowed response status codes for a PUT/PATCH operation are "200","201", & "202".

Please refer to [long-running-response-status-code-data-plane.md](./long-running-response-status-code-data-plane.md) for details.

### LongRunningResponseStatusCode

For ARM spec, the allowed response status codes for a long DELETE operation are "200" & "204"; the allowed response status codes for a POST operation are "200", "201" ,"202", & "204"; the allowed response status codes for a PUT/PATCH operation are "200" & "201".
For Data plane spec, the allowed response status codes for a long DELETE operation are "200","202", & "204"; the allowed response status codes for a POST operation are "200", "201" ,"202", & "204"; the allowed response status codes for a PUT/PATCH operation are "200","201", & "202".

Please refer to [long-running-response-status-code.md](./long-running-response-status-code.md) for details.

### LroExtension

Operations with a 202 response should specify `x-ms-long-running-operation: true`.

Please refer to [lro-extension.md](./lro-extension.md) for details.

### LroHeaders

A 202 response should include an `Operation-Location` response header.

Please refer to [lro-headers.md](./lro-headers.md) for details.

### LroLocationHeader

Location header must be supported for all async operations that return 202.

Please refer to [lro-location-header.md](./lro-location-header.md) for details.

### LroPatch202

Async PATCH should return 202.

Please refer to [lro-patch202.md](./lro-patch202.md) for details.

### LroPostMustNotUseOriginalUriAsFinalState

The long running post operation must not use final-stat-via:original-uri.

Please refer to [lro-post-must-not-use-original-url-as-final-state.md](./lro-post-must-not-use-original-url-as-final-state.md) for details.

### ProvisioningStateSpecified

This is a rule introduced to validate if a LRO PUT and PATCH operations response schema has "ProvisioningState" property specified.

Please refer to [lro-provisioning-state-specified.md](./lro-provisioning-state-specified.md) for details.

### LROStatusCodesReturnTypeSchema

The '200'/'201' responses of the long running operation must have a schema definition.

Please refer to [lro-status-codes-return-type-schema.md](./lro-status-codes-return-type-schema.md) for details.

### LroWithOriginalUriAsFinalState

The long running operation with final-state-via:original-uri should have a sibling 'get' operation.

Please refer to [lro-with-original-url-as-final-state.md](./lro-with-original-url-as-final-state.md) for details.

### MissingDefaultResponse

All operations should have a default (error) response.

Please refer to [missing-default-response.md](./missing-default-response.md) for details.

### MissingTypeObject

The rule should apply to any schema with "properties" or "additionalProperties". It is to ensure a schema with "properties" or "additionalProperties" must have explicit "type:object" statement, which means a schema is an object.

Please refer to [missing-type-object.md](./missing-type-object.md) for details.

### MissingXmsErrorResponse

If defines response code 4xx or 5xx , x-ms-error-response:true is required. There is one exception: a HEAD operation with 404 SHOULD have x-ms-error-response:false, as it is often used to check for existence of resources, the HEAD with 404 means the resource doesn’t exist.

Please refer to [missing-xms-error-response.md](./missing-xms-error-response.md) for details.

### MsPaths

Don't use `x-ms-paths` except where necessary to support legacy APIs.
It is non-standard and therefore ignored by tooling that has not been specifically designed to support it.

Please refer to [ms-paths.md](./ms-paths.md) for details.

### MutabilityWithReadOnly

Verifies whether a model property which has a readOnly property set has the appropriate `x-ms-mutability` options. If `readonly: true`, `x-ms-mutability` must be `["read"]`. If `readonly: false`, `x-ms-mutability` can be any of the `x-ms-mutability` options. More details about this extension can be found [here](https://github.com/Azure/autorest/blob/main/docs/extensions/readme.md#x-ms-mutability).

Please refer to [mutability-with-read-only.md](./mutability-with-read-only.md) for details.

### NamePropertyDefinitionInParameter

A parameter must have a `name` property for the SDK to be properly generated.

Please refer to [name-property-definition-in-parameter.md](./name-property-definition-in-parameter.md) for details.

### NestedResourcesMustHaveListOperation

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), all the nested must have a list operation which returns the collection of the resource.

Please refer to [nested-resources-must-have-list-operation.md](./nested-resources-must-have-list-operation.md) for details.

### NextLinkPropertyMustExist

Per definition of AutoRest [x-ms-pageable extension](https://github.com/Azure/autorest/blob/main/docs/extensions/readme.md#x-ms-pageable), the property specified by nextLinkName must exist in the 200 response schema.

Please refer to [next-link-property-must-exist.md](./next-link-property-must-exist.md) for details.

### NoDuplicatePathsForScopeParameter

Swagger authors that use the `scope` path parameter to indicate that an API is applicable to various scopes (Tenant, Management Group, Subscription, Resource Group, etc.), must not include API paths with explicitly defined scopes (e.g. a `subscription` path parameter).

Please refer to [no-duplicate-paths-for-scope-parameter.md](./no-duplicate-paths-for-scope-parameter.md) for details.

### NonApplicationJsonType

Verifies whether operation supports "application/json" as consumes or produces section.

Please refer to [non-application-json-type.md](./non-application-json-type.md) for details.

### NonEmptyClientName

The [`x-ms-client-name`](https://github.com/Azure/autorest/tree/main/docs/extensions#x-ms-client-name) extension is used to change the name of a parameter or property in the generated code.

Please refer to [non-empty-client-name.md](./non-empty-client-name.md) for details.

### Nullable

You should avoid the use of `x-nullable: true`. Properties with no value should simply be omitted from the payload.

Please refer to [nullable.md](./nullable.md) for details.

### OneUnderscoreInOperationId

An operationId can have exactly one underscore, not adhering to it can cause errors in code generation.

Please refer to [one-underscore-in-operation-id.md](./one-underscore-in-operation-id.md) for details.

### OperationDescriptionOrSummaryRequired

Every operation must have a 'description'/'summary' property.

Please refer to [operation-description-or-summary-required.md](./operation-description-or-summary-required.md) for details.

### OperationIdNounConflictingModelNames

The first part of an operation Id separated by an underscore i.e., `Noun` in a `Noun_Verb` should not conflict with names of the models defined in the definitions section. If this happens, AutoRest appends `Model` to the name of the model to resolve the conflict (`NounModel` in given example) with the name of the client itself (which will be named as `Noun` in given example). This can result in an inconsistent user experience.

Please refer to [operation-id-noun-conflicting-model-names.md](./operation-id-noun-conflicting-model-names.md) for details.

### OperationIdNounVerb

OperationId should be of the form `Noun_Verb`.

Please refer to [operation-id-noun-verb.md](./operation-id-noun-verb.md) for details.

### OperationIdRequired

Each operation must have a unique operationId.

Please refer to [operation-id-required.md](./operation-id-required.md) for details.

### OperationId

OperationId should conform to Azure API Guidelines.

Please refer to [operation-id.md](./operation-id.md) for details.

### OperationSummaryOrDescription

Every operation should have a summary or description.

Please refer to [operation-summary-or-description.md](./operation-summary-or-description.md) for details.

### OperationsAPIImplementation

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), each RP must expose an operations API that returns information about all the operations available with the service.

Please refer to [operations-api-implementation.md](./operations-api-implementation.md) for details.

### OperationsApiResponseSchema

The operations API should have a response body schema consistent with the [contract spec](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/proxy-api-reference.md#exposing-available-operations). The required properties such as `isDataAction`,`display.description` and `display.resource`,must be included.

Please refer to [operations-api-response-schema.md](./operations-api-response-schema.md) for details.

### PageableOperation

This rule was introduced to check if a pageable operation has x-ms-pageable enabled.

Please refer to [pageable-operation.md](./pageable-operation.md) for details.

### PageableRequires200Response

Per definition of AutoRest [x-ms-pageable extension](https://github.com/Azure/autorest/blob/main/docs/extensions/readme.md#x-ms-pageable), the response schema must contain a 200 response schema.

Please refer to [pageable-requires200-response.md](./pageable-requires200-response.md) for details.

### PaginationResponse

Pagination parameters must conform to Azure guidelines.

Please refer to [pagination-response.md](./pagination-response.md) for details.

### ParameterDefaultNotAllowed

A required parameter should not specify a default value.

Please refer to [parameter-default-not-allowed.md](./parameter-default-not-allowed.md) for details.

### ParameterDescriptionRequired

A parameter must have 'description' property.

Please refer to [parameter-description-required.md](./parameter-description-required.md) for details.

### ParameterDescriptionRequired

All parameters should have a description.

Please refer to [parameter-description.md](./parameter-description.md) for details.

### ParameterNamesConvention

Parameter names should conform to Azure naming conventions.

Please refer to [parameter-names-convention.md](./parameter-names-convention.md) for details.

### ParameterNamesUnique

All parameter names for an operation should be case-insensitive unique.

Please refer to [parameter-names-unique.md](./parameter-names-unique.md) for details.

### ParameterNotDefinedInGlobalParameters

Per ARM guidelines, if `subscriptionId` is used anywhere as a path parameter, it must always be defined as global parameter. `api-version` is almost always an input parameter in any ARM spec and must also be defined as a global parameter.

Please refer to [parameter-not-defined-in-global-parameters.md](./parameter-not-defined-in-global-parameters.md) for details.

### ParameterNotUsingCommonTypes

Some commonly used parameters are defined in the common-types directory. These parameters should be referenced instead of explicitly redefining them.

Please refer to [parameter-not-using-common-types.md](./parameter-not-using-common-types.md) for details.

### ParameterOrder

Path parameters must be in the same order as in the path.

Please refer to [parameter-order.md](./parameter-order.md) for details.

### ParametersOrder

The rule is to ensure the parameters in the same order as they are ranked in the path. Since it can introduce a breaking change when updating parameter order, for services that have already shipped public versions, you may request to suppress the rule following the process documented here: https://dev.azure.com/azure-sdk/internal/_wiki/wikis/internal.wiki/85/Swagger-Suppression-Process

Please refer to [parameters-order.md](./parameters-order.md) for details.

### PatchBodyParametersSchema

A request parameter of the Patch Operation must not have a required/default/'x-ms-mutability:"create"' value.

Please refer to [patch-body-parameters-schema.md](./patch-body-parameters-schema.md) for details.

### PatchContentType

The request body content type for patch operations should be JSON merge patch.

Please refer to [patch-content-type.md](./patch-content-type.md) for details.

### PatchIdentityProperty

RP must implement PATCH for the 'identity' envelope property if it's defined in the resource model.

Please refer to [patch-identity-property.md](./patch-identity-property.md) for details.

### PatchInOperationName

Verifies whether value for `operationId` is named as per ARM guidelines.

Please refer to [patch-in-operation-name.md](./patch-in-operation-name.md) for details.

### PatchSkuProperty

RP must implement PATCH for the 'SKU' envelope property if it's defined in the resource model.

Please refer to [patch-sku-property.md](./patch-sku-property.md) for details.

### PathCharacters

Path should contain only recommended characters.
The recommended characters are 0-9, A-Z, a-z, -, ., _, ~, and :.

Please refer to [path-characters.md](./path-characters.md) for details.

### PathContainsResourceGroup

Path for resource group scoped CRUD methods MUST contain a resourceGroupName parameter.

Please refer to [path-contains-resource-group.md](./path-contains-resource-group.md) for details.

### PathContainsResourceType

Per ARM RPC,Uri for resource CRUD methods MUST contain a resource type.
Uri path starts with \<scope\>/providers/\<namespace\>/\<resourcetype\> format, where
- \<scope\> is one of:
  1.  Tenant/Global: '/'
  2.  Subscription: "/subscriptions/{subscriptionId}"
  3.  Resource group: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}",
- \<namespace\> is a literal (e.g. "Microsoft.Compute") consisting of alphanumeric characters, plus '.'.
- \<resourcetype\> is a literal resource type name, follow below rules:
  1.  MUST consist of alphanumeric characters only
  2.  SHOULD describe the resource type
  3.  Must be lowerCamelCase words
  4.  Must be a plural

Please refer to [path-contains-resource-type.md](./path-contains-resource-type.md) for details.

### PathContainsSubscriptionId

Path for resource group scoped CRUD methods MUST contain a subscriptionId parameter, like '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MyNameSpace/MyResourceType/{Name}'.

Please refer to [path-contains-subscription-id.md](./path-contains-subscription-id.md) for details.

### PathForNestedResource

Path for CRUD methods on a nested resource type MUST follow valid resource naming, like '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MyNameSpace/MyResourceType/{Name}/NestedResourceType/{nestedResourceName}'.

Please refer to [path-for-nested-resource.md](./path-for-nested-resource.md) for details.

### PathForPutOperation

For a PUT operation, If a uri segment has subscription, it needs to have a resource group segment as well.

Please refer to [path-for-put-operation.md](./path-for-put-operation.md) for details.

### PathForResourceAction

Path for 'post' method on a resource type MUST follow valid resource naming, like '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MyNameSpace/MyResourceType/{Name}/Action'.

Please refer to [path-for-resource-action.md](./path-for-resource-action.md) for details.

### PathParameterNames

Path parameter names should be consistent across all paths.

Please refer to [path-parameter-names.md](./path-parameter-names.md) for details.

### PathParameterSchema

Path parameter should be type: string and specify maxLength and pattern.

Please refer to [path-parameter-schema.md](./path-parameter-schema.md) for details.

### PathResourceProviderMatchNamespace

Verifies whether the resource provider namespace in the last segment of the path matches the namespace to which the specification file belongs. E.g the path /providers/Microsoft.Compute/virtualMachines/{vmName}/providers/Microsoft.Insights/extResource/{extType}' is allowed only if the segment /Microsoft.Insights matches the namespace name to which the specification file belongs (Microsoft.Insights).

Please refer to [path-resource-provider-match-namespace.md](./path-resource-provider-match-namespace.md) for details.

### PathResourceProviderNamePascalCase

Resource provider naming in path SHOULD follow the pascal case. (e.g. Microsoft.Insights/components/proactiveDetectionConfigs)
For more detail, pls refer to https://github.com/microsoft/api-guidelines/blob/vNext/Guidelines.md#172-casing

Please refer to [path-resource-provider-name-pascal-case.md](./path-resource-provider-name-pascal-case.md) for details.

### PathResourceTypeNameCamelCase

Resource type or other identifiers (include: namespace, entityTypes) SHOULD follow camel case. (e.g. Microsoft.Insights/components/proactiveDetectionConfigs, not ProactiveDetectionConfig)
For more detail, pls refer to https://github.com/microsoft/api-guidelines/blob/vNext/Guidelines.md#172-casing

Please refer to [path-resource-type-name-camel-case.md](./path-resource-type-name-camel-case.md) for details.

### Post201Response

Using post for a create operation is discouraged.

Please refer to [post-201-response.md](./post-201-response.md) for details.

### PostOperationAsyncResponseValidation

An async POST operation response include status code 202 with 'Location' header. Must support status code 200 if operation can be completed synchronously. Operation must also add "x-ms-long-running-operation and x-ms-long-running-operation-options" to mark that it is a long running operation (in case of 202) and how it is tracked (Location header).

Please refer to [post-operation-async-response-validation.md](./post-operation-async-response-validation.md) for details.

### PostOperationIdContainsUrlVerb

A POST operation's operationId should contain the verb indicated at the end of the corresponding url.

Please refer to [post-operation-id-contains-url-verb.md](./post-operation-id-contains-url-verb.md) for details.

### PreviewVersionOverOneYear

Per [Retirement-of-Previews](https://dev.azure.com/msazure/AzureWiki/_wiki/wikis/AzureWiki.wiki/37683/Retirement-of-Previews), service, feature, API, and SKU in preview for over one year need to move to GA or retire.

Please refer to [preview-version-over-one-year.md](./preview-version-over-one-year.md) for details.

### PrivateEndpointResourceSchemaValidation

This rule is to check if the schemas used by private endpoint conform to the common [privateLink](https://github.com/Azure/azure-rest-api-specs/blob/main/specification/common-types/resource-management/v1/privatelinks.json). The rule will check the schemas of following models and their properties:
1. PrivateEndpointConnection
2. PrivateEndpointConnectionProperties
3. PrivateEndpointConnectionListResult
4. PrivateLinkResource
5. PrivateLinkResourceProperties
6. PrivateLinkResourceListResult

Please refer to [private-endpoint-resource-schema-validation.md](./private-endpoint-resource-schema-validation.md) for details.

### PropertyDescription

Property should have a description.

Please refer to [property-description.md](./property-description.md) for details.

### PropertyNameConvention

Property names should be camel case.

Please refer to [property-names-convention.md](./property-names-convention.md) for details.

### PropertyType

Schema property should have a defined type.

Please refer to [property-type.md](./property-type.md) for details.

### ProvisioningStateValidation

Per ARM guideline, provisioningState must have terminal states: Succeeded, Failed and Canceled.

Please refer to [provisioning-state-validation.md](./provisioning-state-validation.md) for details.

### PutGetPatchResponseSchema

For a given path with PUT, GET and PATCH operations, the schema of the response must be the same.

Please refer to [put-get-patch-response-schema.md](./put-get-patch-response-schema.md) for details.

### PutInOperationName

Verifies whether value for `operationId` is named as per ARM guidelines.

Please refer to [put-in-operation-name.md](./put-in-operation-name.md) for details.

### PutPath

The put method should be used for resource create or replace, which generally requires the resource id to specified as the final path parameter.

Please refer to [put-path.md](./put-path.md) for details.

### PutRequestResponseScheme

The request & response('200') schema of the PUT operation must be same.

Please refer to [put-request-response-scheme.md](./put-request-response-scheme.md) for details.

### RepeatedPathInfo

Information in the URI should not be repeated in the request body (i.e. subscription ID, resource group name, resource name).

Please refer to [repeated-path-info.md](./repeated-path-info.md) for details.

### RequestBodyNotAllowed

A get or delete operation must not accept a body parameter.

Please refer to [request-body-not-allowed.md](./request-body-not-allowed.md) for details.

### RequestBodyOptional

The body parameter is not marked as required -- this is a common error.
While there are some cases where a body may be optional, they are rare.

Please refer to [request-body-optional.md](./request-body-optional.md) for details.

### RequiredDefaultResponse

Per ARM Specs, every operation must have a default error response implementation.

Please refer to [required-default-response.md](./required-default-response.md) for details.

### RequiredPropertiesMissingInResourceModel

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), a `Resource` model must have the `name`, `id` and `type` properties defined as `readOnly` in its hierarchy.

Please refer to [required-properties-missing-in-resource-model.md](./required-properties-missing-in-resource-model.md) for details.

### RequiredReadOnlyProperties

A model property cannot be both `readOnly` and `required`. A `readOnly` property is something that the server sets when returning the model object while `required` is a property to be set when sending it as a part of the request body.

Please refer to [required-read-only-properties.md](./required-read-only-properties.md) for details.

### RequiredReadOnlySystemData

Per [common-api-contracts](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/common-api-contracts.md#system-metadata-for-all-azure-resources), all Azure resources should implement the `systemData` object property in new api-version. The systemData should be readonly.

Please refer to [required-read-only-system-data.md](./required-read-only-system-data.md) for details.

### ResourceHasXMsResourceEnabled

A 'Resource' definition must have x-ms-azure-resource extension enabled and set to true. This will indicate that the model is an Azure resource.

Please refer to [resource-has-x-ms-resource-enabled.md](./resource-has-x-ms-resource-enabled.md) for details.

### ResourceNameRestriction

This rule ensures that the authors explicitly define these restrictions as a regex on the resource name. If a team does not have custom rules then the ARM's default rule should get applied.

Please refer to [resource-name-restriction.md](./resource-name-restriction.md) for details.

### ResponseSchemaSpecifiedForSuccessStatusCode

Validates if 200 & 201 success status codes for an ARM PUT operation has a response schema specified.

Please refer to [response-schema-specified-for-success-status-code.md](./response-schema-specified-for-success-status-code.md) for details.

### RPaasResourceProvisioningState

Verifies if a Azure resource has a corresponding 'provisioningState' property. If the 'provisioningState' is not defining explicitly , the client will drop the state when the service does return it.

Please refer to [rpaas-resource-provisioning-state.md](./rpaas-resource-provisioning-state.md) for details.

### SchemaDescriptionOrTitle

All schemas should have a description or title.

Please refer to [schema-description-or-title.md](./schema-description-or-title.md) for details.

### SchemaNamesConvention

Schema names should be Pascal case. This includes any acronyms.

Please refer to [schema-names-convention.md](./schema-names-convention.md) for details.

### SchemaTypeAndFormat

Every schema should specify a well-defined combination of `type` and `format`.
`format` is required for type integer and number, optional for type string,
and not allowed for any other types.
The well-defined type/format combinations are:
**type: integer**
| format   | description     | comments                  |
| -------- | --------------- | ------------------------- |
| int32    | signed 32 bits  | from [oas2][oas2]         |
| int64    | signed 64 bits  | from [oas2][oas2]         |
| unixtime | Unix time stamp | from [autorest][autorest] |
**type: number**
| format  | description            | comments                  |
| ------- | ---------------------- | ------------------------- |
| float   | 32 bit floating point  | from [oas2][oas2]         |
| int64   | 64 bit floating point  | from [oas2][oas2]         |
| decimal | 128 bit floating point | from [autorest][autorest] |
**type: string**
| format            | description                  | comments                  |
| ----------------- | ---------------------------- | ------------------------- |
| byte              | base64 encoded characters    | from [oas2][oas2]         |
| binary            | any sequence of octets       | from [oas2][oas2]         |
| date              | [RFC3339][rfc3339] full-date | from [oas2][oas2]         |
| date-time         | [RFC3339][rfc3339] date-time | from [oas2][oas2]         |
| password          | sensitive value              | from [oas2][oas2]         |
| char              |                              | from [autorest][autorest] |
| time              |                              | from [autorest][autorest] |
| date-time-rfc1123 |                              | from [autorest][autorest] |
| duration          |                              | from [autorest][autorest] |
| uuid              |                              | from [autorest][autorest] |
| base64url         |                              | from [autorest][autorest] |
| url               |                              | from [autorest][autorest] |
| odata-query       |                              | from [autorest][autorest] |
| certificate       |                              | from [autorest][autorest] |
oas2: https://github.com/OAI/OpenAPI-Specification/blob/main/versions/2.0.md#data-types
autorest: https://github.com/Azure/autorest/blob/main/packages/libs/openapi/src/v3/formats.ts
rfc3339: https://xml2rfc.tools.ietf.org/public/rfc/

Please refer to [schema-type-and-format.md](./schema-type-and-format.md) for details.

### SecurityDefinitionDescription

All security definitions should have a description.

Please refer to [security-definition-description.md](./security-definition-description.md) for details.

### SecurityDefinitionsStructure

Each OpenAPI json document must contain a security definitions section and the section must adhere to a certain format.

Please refer to [security-definitions-structure.md](./security-definitions-structure.md) for details.

### SubscriptionIdParameterInOperations

`subscriptionId` must not be an operation parameter and must be declared in the global parameters section.

Please refer to [subscription-id-parameter-in-operations.md](./subscription-id-parameter-in-operations.md) for details.

### SubscriptionsAndResourceGroupCasing

The URLs should be checked for consistency. It is easy to type "resourcegroups" instead of "resourceGroups". The current rules allow that through, which causes an issue at the resource provider registration step. When that happens, the APIs get split into two sets in the swagger. The RPaaS registration is very strict and requires the same resource to have all APIs in one set. The pipeline needs to be aware of this kind of behavior and provider URL validation.

Please refer to [subscriptions-and-resource-group-casing.md](./subscriptions-and-resource-group-casing.md) for details.

### SuccessResponseBody

All success responses except 202 & 204 should define a response body.

Please refer to [success-response-body.md](./success-response-body.md) for details.

### SummaryAndDescriptionMustNotBeSame

Each operation has a summary and description values. They must not be same.

Please refer to [summary-and-description-must-not-be-same.md](./summary-and-description-must-not-be-same.md) for details.

### TopLevelResourcesListByResourceGroup

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), all the top-level resources must have a list by resource group operation which returns the collection of the resource.

Please refer to [top-level-resources-list-by-resource-group.md](./top-level-resources-list-by-resource-group.md) for details.

### TopLevelResourcesListBySubscription

Per [ARM guidelines](https://github.com/Azure/azure-resource-manager-rpc/blob/master/v1.0/resource-api-reference.md), all the top-level resources must have a list by subscription operation which returns the collection of the resource.

Please refer to [top-level-resources-list-by-subscription.md](./top-level-resources-list-by-subscription.md) for details.

### TrackedResourceBeyondsThirdLevel

Tracked resources must not be used beyond the third level of nesting.

Please refer to [tracked-resource-beyond-thrid-level.md](./tracked-resource-beyond-thrid-level.md) for details.

### TrackedResourceGetOperation

Verifies if a tracked resource has a corresponding GET operation.
What's a tracked resource? A Tracked Resource is an ARM Resource with "location" as a required property.

Please refer to [tracked-resource-get-operation.md](./tracked-resource-get-operation.md) for details.

### TrackedResourceListByImmediateParent

Verifies if a tracked resource has a corresponding list by immediate parent operation.
What's a tracked resource? A Tracked Resource is an ARM Resource with "location" as a required property.

Please refer to [tracked-resource-list-by-immediate-parent.md](./tracked-resource-list-by-immediate-parent.md) for details.

### TrackedResourceListByResourceGroup

Verifies if a tracked resource has a corresponding ListByResourceGroup operation.
What's a tracked resource? A Tracked Resource is an ARM Resource with "location" as a required property.

Please refer to [tracked-resource-list-by-resource-group.md](./tracked-resource-list-by-resource-group.md) for details.

### TrackedResourceListBySubscription

Verifies if a tracked resource has a corresponding ListByResourceGroup operation.
What's a tracked resource? A Tracked Resource is an ARM Resource with "location" as a required property.

Please refer to [tracked-resource-list-by-subscription.md](./tracked-resource-list-by-subscription.md) for details.

### TrackedResourcePatchOperation

Verifies if a tracked resource has a corresponding PATCH operation.
What's a tracked resource? A Tracked Resource is an ARM Resource with "location" as a required property.

Please refer to [tracked-resource-patch-operation.md](./tracked-resource-patch-operation.md) for details.

### TrackedResourceSchemaTags

Every tracked resource MUST support tags as an optional property.

Please refer to [tracked-resource-schema-tags.md](./tracked-resource-schema-tags.md) for details.

### TrackedResourcesMustHavePut

Tracked resources must have put operation.

Please refer to [tracked-resources-must-have-put.md](./tracked-resources-must-have-put.md) for details.

### UnSupportedPatchProperties

Patch may not change the name, location, or type of the resource.

Please refer to [un-supported-patch-properties.md](./un-supported-patch-properties.md) for details.

### UniqueClientParameterName

This may cause a problem when different swagger files come together. If two APIs with different client name have the same client parameter subscriptionId, but with different reference name in swaggers, the generated model will also have two clients with two client parameters subscriptionId and subscriptionId1 (the latter one has been renamed to avoid collision). We should ensure that the client parameters are all unique in the same API version.

Please refer to [unique-client-parameter-name.md](./unique-client-parameter-name.md) for details.

### UniqueModelName

Do not rely on case sensitivity to differentiate models.

Please refer to [unique-model-name.md](./unique-model-name.md) for details.

### UniqueXmsEnumName

This rule will check all the swagger files with the same api-version, and ensure there is no duplicate x-ms-enum name.
The following cases are deemed as violation:
1. if two enums have the same x-ms-enum name , but types are different.
2. if two enums have the same x-ms-enum name , but 'modelAsString' are different.
3. if two enums have the same x-ms-enum name , but include different values.
4. if two enums have the same x-ms-enum name and 'modelAsString' is false , but enums' values have different order.

Please refer to [unique-xms-enum-name.md](./unique-xms-enum-name.md) for details.

### UniqueXmsExample

x-ms-example name should be unique in the same API version.

Please refer to [unique-xms-example.md](./unique-xms-example.md) for details.

### ValidFormats

Only valid types are allowed for properties.

Please refer to [valid-formats.md](./valid-formats.md) for details.

### ValidResponseCodeRequired

Every operation response must contain a valid code like "200","201","202" or "204" which indicates the operation is succeed and it's not allowed that a response schema just contains a "default" code.

Please refer to [valid-response-code-required.md](./valid-response-code-required.md) for details.

### VersionConvention

API version should be a date in YYYY-MM-DD format, optionally suffixed with '-preview'.

Please refer to [version-convention.md](./version-convention.md) for details.

### VersionPolicy

All services should follow the Azure API Guidelines for specifying the API version using a query parameter with a date-based value.

Please refer to [version-policy.md](./version-policy.md) for details.

### XmsClientNameParameter

The [`x-ms-client-name`](https://github.com/Azure/autorest/tree/main/docs/extensions#x-ms-client-name) extension is used to change the name of a parameter or property in the generated code. By using the 'x-ms-client-name' extension, a name can be defined for use specifically in code generation, separately from the name on the wire. It can be used for query parameters and header parameters, as well as properties of schemas. This name is case sensitive.

Please refer to [xms-client-name-parameter.md](./xms-client-name-parameter.md) for details.

### XmsClientNameProperty

The [`x-ms-client-name`](https://github.com/Azure/autorest/tree/main/docs/extensions#x-ms-client-name) extension is used to change the name of a parameter or property in the generated code. By using the 'x-ms-client-name' extension, a name can be defined for use specifically in code generation, separately from the name on the wire. It can be used for query parameters and header parameters, as well as properties of schemas. This name is case sensitive.

Please refer to [xms-client-name-property.md](./xms-client-name-property.md) for details.

### XmsEnumValidation

AutoRest defines [x-ms-enum extension](https://github.com/Azure/autorest/blob/main/docs/extensions/readme.md#x-ms-enum) to provide more flexibility for enum types, please refer to the documentation.

Please refer to [xms-enum-validation.md](./xms-enum-validation.md) for details.

### XmsExamplesRequired

Verifies whether [x-ms-examples](https://github.com/Azure/azure-rest-api-specs/blob/main/documentation/x-ms-examples.md#why-x-ms-examples) are provided for each operation or not.

Please refer to [xms-examples-required.md](./xms-examples-required.md) for details.

### XmsIdentifierValidation

This rule is to check the `id` property or identifier of objects in the array. See more here: [x-ms-identifiers](https://github.com/Azure/autorest/tree/main/docs/extensions#x-ms-identifiers).

Please refer to [xms-identifier-validation.md](./xms-identifier-validation.md) for details.

### XmsLongRunningOperationOptions

The x-ms-long-running-operation-options should be specified explicitly to indicate the type of response header to track the async operation, see [x-ms-long-running-operation-options](https://github.com/Azure/autorest/tree/main/docs/extensions#x-ms-long-running-operation-options)

Please refer to [xms-long-running-operation-options.md](./xms-long-running-operation-options.md) for details.

### XmsPageableListByRGAndSubscriptions

When a tracked resource has list by resource group and subscription operations, the x-ms-pageable extension values must be same for both operations. A tracked resource is a resource with a 'location' property as required. If this rule flags a resource which does not have a 'location' property, then it might be a false positive.

Please refer to [xms-pageable-list-by-rg-and-subscriptions.md](./xms-pageable-list-by-rg-and-subscriptions.md) for details.

### XmsPageableMustHaveCorrespondingResponse

Per [extensions](https://github.com/Azure/autorest/blob/main/docs/extensions/readme.md#x-ms-pageable) ,when specifying a x-ms-pageable/nextLinkName, the corresponding nextlink property must be defined in the response schema.

Please refer to [xms-pageable-must-have-corresponding-response.md](./xms-pageable-must-have-corresponding-response.md) for details.

### XmsParameterLocation

SDKs generated by AutoRest have two types of operation parameters: method arguments and client fields. The `x-ms-parameter-location` extension gives the Swagger author control of how an operation-parameter will be interpreted by AutoRest, and as such is one of few things in a Swagger document that has semantic value only relevant to the shape of the generated SDKs.
Some parameters, such as API Version and Subscription ID will make sense as part of nearly every request. For these, having developers specify them for each method call would be burdensome; attaching them to the client and automatically including them in each request makes way more sense. Other parameters will be very operation specific and should be provided each time the method is called.

Please refer to [xms-parameter-location.md](./xms-parameter-location.md) for details.

### XmsPathsMustOverloadPaths

The `x-ms-paths` extension allows us to overload an existing path based on path parameters. We cannot specify an `x-ms-paths` without a path that already exists in the `paths` section. For more details about this extension please refer [here](https://github.com/Azure/azure-rest-api-specs/blob/dce4da0d748565efd2ab97a43d0683c2979a974a/documentation/swagger-extensions.md#x-ms-paths).

Please refer to [xms-paths-must-overload-paths.md](./xms-paths-must-overload-paths.md) for details.

### XmsResourceInPutResponse

The 200 response model for an ARM PUT operation must have x-ms-azure-resource extension set to true in its hierarchy. Operation: '{0}' Model: '{1}'.

Please refer to [xms-resource-in-put-response.md](./xms-resource-in-put-response.md) for details.
