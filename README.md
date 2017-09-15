# **Servicio GET y POST para administrar coordenadas asociadas a cámaras**

## **v1.0**


## **Consulta coordenadas de una o varias cámaras**

### URL 

Para una cámara en específico:

> /api/cameras/coordinates?id={Camera ID}

Asterisco para obtener todas las cámaras:

> /api/cameras/coordinates?id=*

### Método	
**GET**

### Respuesta Exitosa	

```
{
    "cameras":[
        {
            "name" : "Camera 1",
            "latitude" : "19.394747",
            "longitude" : "-99.173900"
        },
        {
            "name" : "Camera 2",
            "latitude" : "19.394747",
            "longitude" : "-99.173900"
        }
    ],
    "result-count" : 2,
    "state" : "ok"
}
```

### Respuesta Error	

```
{
    "cameras":[],
    "result-count" : 0,
    "state" : "nok"
}
```



## **Servicio web para modificar la latitud y longitud de las cámaras**

### URL 

> /api/cameras/coordinates


### Método	
**POST**

### Contenido

```
{
    "id" : [int],
    "latitude" : [string]
    "longitude" : [string]
}
```

### Respuesta Exitosa	

```
{
   "state" : "ok"
}

```

### Respuesta Error	

```
{
   "state" : "nok"
}

```


## **Servicio web para recibir coordenadas y validar el top 10 de cámaras más cercanas a las coordenadas recibidas**

### URL 

Para una cámara en específico:

> /api/cameras/coordinates/top?longitude={longitud para buscar}&latitude={latitud para buscar}


### Método	
**GET**


### Respuesta Exitosa	

```
{
    "cameras":[
        {
            "name" : "Camera 1",
            "latitude" : "19.394747",
            "longitude" : "-99.173900"
        },
        {
            "name" : "Camera 2",
            "latitude" : "19.394747",
            "longitude" : "-99.173900"
        },
        
        ...
        
        {
            "name" : "Camera 10",
            "latitude" : "19.394747",
            "longitude" : "-99.173900"
        }
    ],
    "result-count" : 10,
    "state" : "ok"
}

```

### Respuesta Error	

```
{
    "cameras":[],
    "result-count" : 0,
    "state" : "nok"
}

```