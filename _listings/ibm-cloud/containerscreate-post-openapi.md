---
swagger: "2.0"
x-collection-name: IBM Cloud
x-complete: 0
info:
  title: IBM Containers Create and start a single container
  description: "This endpoint creates and starts a single container in your space
    based on the Docker image that is specified in the Image field of the request
    json. A single container in IBM Containers is similar to a container that you
    create in your local Docker environment. Single containers are a good way to start
    with IBM Containers and to learn about how containers work in the IBM Cloud and
    the features that IBM Containers provides. They are also recommended when you
    want to run simple app tests or during the development process of an app. \n\n
    In the Docker API there are two separate APIs to create and start a container.
    However in IBM Containers a container is created and started in a single API call.
    Therefore, this API merges parameters from the Docker API to create and start
    container. \n\n To create a container with IBM Containers, you must at least define
    the image that the container is based on.\n\n- Image: You must include the full
    path to the image in your private Bluemix registry in the format: `registry.ng.bluemix.net/<namespace>/<image>`."
  version: 3.0.0
host: containers-api.ng.bluemix.net
basePath: /v3
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /build:
    post:
      summary: Build a Docker image from a Dockerfile
      description: |-
        This API builds a new container image from a Dockerfile that is stored on your local machine and pushes the image to the private Bluemix registry (corresponding IBM Containers command: `cf ic build`).

         To push an image to your Bluemix registry, a namespace must be set for the organization. Run `cf ic namespace get` or call the `GET /registry/namespaces` API to check if a namespace is already set. If not, run `cf ic namespace set NAMESPACE` or call the `PUT /registry/namespaces/{namespace}` API to set a namespace for your organization.
      operationId: this-api-builds-a-new-container-image-from-a-dockerfile-that-is-stored-on-your-local-machine-and-pus
      x-api-path-slug: build-post
      parameters:
      - in: body
        name: file
        description: Must be the content of a tar archive compressed with gzip
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: nocache
        description: If you set the query parameter to `nocache=true`, `nocache=True`,
          or `nocache=1`, the cache will not be used to build your image
      - in: query
        name: pull
        description: If set to pull=true, pull=True, or pull=1, then a newer version
          of the image is always attempted to be pulled even though an older version
          of the image exists locally
      - in: query
        name: q
        description: You can choose whether or not to show the verbose build output
          to review every step during the container image build
      - in: query
        name: t
        description: 'Tag the image with the full path to your private Bluemix registry
          in the following format: `t=registry'
      - in: header
        name: X-Auth-Project-Id
        description: The unique ID of your organization space where you want to create
          or work with your containers
      - in: header
        name: X-Auth-Token
        description: The Bluemix JSON web token that you receive when logging into
          Bluemix
      responses:
        200:
          description: OK
      tags:
      - Build
  /containers/create:
    post:
      summary: Create and start a single container
      description: "This endpoint creates and starts a single container in your space
        based on the Docker image that is specified in the Image field of the request
        json. A single container in IBM Containers is similar to a container that
        you create in your local Docker environment. Single containers are a good
        way to start with IBM Containers and to learn about how containers work in
        the IBM Cloud and the features that IBM Containers provides. They are also
        recommended when you want to run simple app tests or during the development
        process of an app. \n\n In the Docker API there are two separate APIs to create
        and start a container. However in IBM Containers a container is created and
        started in a single API call. Therefore, this API merges parameters from the
        Docker API to create and start container. \n\n To create a container with
        IBM Containers, you must at least define the image that the container is based
        on.\n\n- Image: You must include the full path to the image in your private
        Bluemix registry in the format: `registry.ng.bluemix.net/<namespace>/<image>`."
      operationId: this-endpoint-creates-and-starts-a-single-container-in-your-space-based-on-the-docker-image-that-is-
      x-api-path-slug: containerscreate-post
      parameters:
      - in: query
        name: name
        description: Choose a name for your container
      - in: body
        name: Param
        description: Summary of input parameter to create a container in IBM Containers
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Auth-Project-Id
        description: The unique ID of your organization space where you want to create
          or work with your containers
      - in: header
        name: X-Auth-Token
        description: The Bluemix JSON web token that you receive when logging into
          Bluemix
      responses:
        200:
          description: OK
      tags:
      - Containers
      - Create
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---