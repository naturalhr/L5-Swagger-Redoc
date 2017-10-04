This is a fork of [DarkaOnLine/L5-Swagger](https://github.com/DarkaOnLine/L5-Swagger) which is based on [swagger-PHP](https://github.com/zircote/swagger-php) and [swagger-UI](https://github.com/swagger-api/swagger-ui). 

Instead of the stock Swagger interface this package uses the [Rebilly/Redoc](https://github.com/Rebilly/ReDoc) UI. 

# Installation & Usage

```
composer require imikemiller/l5-swagger-redoc
```

Register the service provider `L5Swagger\L5SwaggerServiceProvider::class` in the Laravel app config file `config/app.php` and run

```
php artisan l5-swagger:publish //to publish the resources
php artisan l5-swagger:generate //to generate the doc spec json
```
By default the documentation will be available at `http://{base_url}/api/documentation`. You can configure the page title and other Swagger configuration options by editing `config/l5-swagger.php`.

# TODO
* Add support for configuration of the Redoc UI

# Example Controller Annotations

```php
<?php
/**
 * @SWG\Swagger(
 *     basePath="/api/v1",
 *     schemes={"http", "https"},
 *     host=L5_SWAGGER_CONST_HOST,
 *     @SWG\Info(
 *         version="1.0.0",
 *         title="L5 Swagger API",
 *         description="L5 Swagger API description",
 *         @SWG\Contact(
 *             email="darius@matulionis.lt"
 *         ),
 *     )
 * )
 */
/**
 * @SWG\Get(
 *      path="/projects",
 *      operationId="getProjectsList",
 *      tags={"Projects"},
 *      summary="Get list of projects",
 *      description="Returns list of projects",
 *      @SWG\Response(
 *          response=200,
 *          description="successful operation"
 *       ),
 *       @SWG\Response(response=400, description="Bad request"),
 *       security={
 *           {"api_key_security_example": {}}
 *       }
 *     )
 *
 * Returns list of projects
 */
/**
 * @SWG\Get(
 *      path="/projects/{id}",
 *      operationId="getProjectById",
 *      tags={"Projects"},
 *      summary="Get project information",
 *      description="Returns project data",
 *      @SWG\Parameter(
 *          name="id",
 *          description="Project id",
 *          required=true,
 *          type="integer",
 *          in="path"
 *      ),
 *      @SWG\Response(
 *          response=200,
 *          description="successful operation"
 *       ),
 *      @SWG\Response(response=400, description="Bad request"),
 *      @SWG\Response(response=404, description="Resource Not Found"),
 *      security={
 *         {
 *             "oauth2_security_example": {"write:projects", "read:projects"}
 *         }
 *     },
 * )
 *
 */
 
 ```
