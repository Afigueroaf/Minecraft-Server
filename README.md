# 🎮 Minecraft Server - Panel de Control Remoto

Panel web para iniciar, detener y monitorear un servidor de Minecraft alojado en AWS EC2.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazon-aws&logoColor=white)

## 📋 Resumen

Interfaz web minimalista y responsive que permite controlar remotamente una instancia EC2 con un servidor de Minecraft. El panel se comunica con AWS a través de una API REST serverless, permitiendo:

- ▶️ **Iniciar** el servidor bajo demanda
- ⏹️ **Detener** el servidor para ahorrar costos
- 🔄 **Consultar** el estado en tiempo real
- 📍 **Obtener** la IP pública para conectarse

## 🏗️ Arquitectura

```
┌─────────────┐      ┌─────────────────┐      ┌────────────┐      ┌─────────────┐
│   Usuario   │ ───► │  API Gateway    │ ───► │   Lambda   │ ───► │    EC2      │
│  (Browser)  │ ◄─── │  (REST API)     │ ◄─── │ (Python)   │ ◄─── │ (Minecraft) │
└─────────────┘      └─────────────────┘      └────────────┘      └─────────────┘
```

| Servicio | Función |
|----------|---------|
| **EC2** | Instancia que ejecuta el servidor Minecraft (puerto 25565) |
| **Lambda** | 3 funciones para status, start y stop de la instancia |
| **API Gateway** | REST API con endpoints `/status`, `/start`, `/stop` |
| **IAM** | Rol con permisos `ec2:DescribeInstances`, `StartInstances`, `StopInstances` |

## 🔐 Seguridad

- Autenticación mediante token en query parameter
- Validación del token en cada función Lambda
- CORS configurado en API Gateway

## 🚀 Uso

1. Abrir `index.html` en el navegador
2. Ingresar el token de acceso
3. Usar los botones para controlar el servidor

## 📱 Compatibilidad

Diseño responsive compatible con desktop, tablets y móviles.

---
*Proyecto personal para gestión de servidor Minecraft en AWS*
