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





## **v1.1**


## **Servicio de notificación de botones de alarma**

### Método	
**POST**

### Contenido

```
{
    "mobileID" : [string],
    "latitude" : [string],
    "longitude" : [string],
    "comments" : [string],
    "notificationType" : [string] -> "familyAlarm" or "falseAlarm" or "normalAlarm" or "911Alarm"
}
```

### Ejemplo:

```
{
    "mobileID" : "123456789",
    "latitude" : "20.00000",
    "longitude" : "90.00000",
	"comments": "Comentarios Aquí",
    "notificationType" : "familyAlarm"
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

### Ejemplo notificación en SecurOS

```
Event : CRYXO_NOTIFICATION 1 notification __automatic<1>,requests<["notificationType","familyAlarm","latitude","20.00000","longitude","90.00000","comments", "Comentarios Aquí","mobileID","123456789", "GUID":"570f94e3-a9f1-4ef5-97bf-e71ab7c9bdc9"]>,__from_script<1>,__from_script_id<1>,date<20-09-17>,_generated_slave_id<1>,slave_id<ADMIN-ISSMX.1>,time<13:32:12.944>,owner<ADMIN-ISSMX>,core_global<1>
```