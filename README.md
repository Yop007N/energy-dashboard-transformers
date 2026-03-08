# Energy Dashboard Transformers

Un dashboard profesional para monitoreo de transformadores el??ctricos con an??lisis de consumo energ??tico en tiempo real.

## ???? Caracter??sticas

- **Monitoreo en Tiempo Real**: Visualizaci??n de datos de consumo energ??tico en vivo
- **An??lisis Hist??rico**: Consulta de datos hist??ricos con filtros de fecha personalizables
- **Comparaci??n Multi-Serie**: Comparar el rendimiento de m??ltiples transformadores
- **Alertas Inteligentes**: Sistema de alertas basado en umbrales de capacidad
- **Dashboard Responsivo**: Optimizado para dispositivos m??viles y desktop
- **API REST**: Backend completo con documentaci??n Swagger
- **Datos Realistas**: Simulaci??n de patrones de consumo energ??tico realistas

## ??????? Tecnolog??as

### Frontend
- **React 18** - Biblioteca de UI
- **Lightweight Charts** - Gr??ficos de alto rendimiento
- **Axios** - Cliente HTTP
- **CSS3** - Estilos modernos con gradientes y animaciones

### Backend
- **Node.js** - Runtime del servidor
- **Express** - Framework web
- **Swagger** - Documentaci??n de API
- **CORS** - Configuraci??n de seguridad

## ???? Prerrequisitos

- Node.js >= 16.0.0
- npm >= 8.0.0

## ???? Instalaci??n y Configuraci??n

1. **Clonar el repositorio**:
```bash
git clone https://github.com/yop007n/energy-dashboard-transformers.git
cd energy-dashboard-transformers
```

2. **Instalar dependencias**:
```bash
npm install
```

3. **Configurar variables de entorno**:
```bash
cp .env.example .env
```

Editar `.env` con tus configuraciones:
```env
PORT=3002
NODE_ENV=development
CORS_ORIGIN=http://localhost:3000,http://localhost:3001
```

4. **Ejecutar en desarrollo**:
```bash
# Ejecutar solo el frontend
npm start

# Ejecutar solo el backend
npm run server

# Ejecutar frontend y backend simult??neamente
npm run dev
```

5. **Acceder a la aplicaci??n**:
- Frontend: http://localhost:3000
- Backend API: http://localhost:3002
- Documentaci??n Swagger: http://localhost:3002/api-docs

## ???? Transformadores Configurados

| ID | Nombre | Capacidad | Ubicaci??n | Voltaje |
|----|--------|-----------|-----------|---------|
| A | Transformador Alpha | 3000 kVA | Sector Norte | 13.8/0.4 kV |
| B | Transformador Beta | 2500 kVA | Sector Centro | 13.8/0.4 kV |
| C | Transformador Gamma | 3500 kVA | Sector Sur | 13.8/0.4 kV |

## ???? Caracter??sticas del Dashboard

### Gr??fico Hist??rico
- Consulta de datos por rango de fechas
- Botones de acceso r??pido (??ltimo d??a, semana, mes, 3 meses)
- L??nea de capacidad m??xima para referencia
- Informaci??n detallada del transformador

### Gr??fico en Tiempo Real
- Actualizaci??n autom??tica cada 5 segundos
- Indicadores de estado (Normal, Advertencia, Cr??tico)
- ??ltimos 30 puntos de datos
- Monitoreo de carga actual

### Gr??fico Multi-Serie
- Comparaci??n simult??nea de todos los transformadores
- An??lisis de rendimiento relativo
- Identificaci??n de patrones de consumo

## ???? API Endpoints

### Transformadores
- `GET /api/transformers` - Lista todos los transformadores
- `GET /api/transformer-capacity/:id` - Informaci??n de capacidad

### Datos
- `GET /api/historical-data/:id` - Datos hist??ricos con filtros
- `GET /api/real-time-data/:id` - Datos en tiempo real
- `GET /api/multi-series-data` - Datos comparativos

### Utilidades
- `GET /health` - Estado del servidor
- `GET /api-docs` - Documentaci??n Swagger

## ???? Patrones de Datos

El sistema simula patrones realistas de consumo energ??tico:

- **Carga Base**: 30% de la capacidad nominal
- **Pico Matutino**: 6:00-9:00 AM (+50% de carga)
- **Pico Vespertino**: 17:00-21:00 PM (+80% de carga)
- **Consumo Nocturno**: 22:00-5:00 AM (-30% de carga)
- **Variaci??n Aleatoria**: ??15% para simular fluctuaciones reales

## ???? Personalizaci??n

### Modificar Transformadores
Editar la configuraci??n en `server.js`:
```javascript
const transformerConfig = {
  A: {
    name: 'Tu Transformador',
    capacity: 5000,
    location: 'Tu Ubicaci??n',
    voltage: 'Tu Voltaje'
  }
};
```

### Cambiar Colores
Modificar los colores en `src/components/HistoricalChart.js`:
```javascript
const colors = {
  A: '#tu-color',
  B: '#tu-color',
  C: '#tu-color',
};
```

### Ajustar Umbrales de Alerta
Configurar en `.env`:
```env
WARNING_THRESHOLD=70
CRITICAL_THRESHOLD=90
```

## ??????? Estructura del Proyecto

```
energy-dashboard-transformers/
????????? src/
???   ????????? components/
???   ???   ????????? HistoricalChart.js
???   ???   ????????? RealTimeChart.js
???   ???   ????????? MultiSeriesChart.js
???   ????????? App.js
???   ????????? App.css
???   ????????? index.js
????????? public/
????????? server.js              # Backend API
????????? swagger-config.js       # Configuraci??n Swagger
????????? package.json
????????? .env                   # Variables de entorno
????????? README.md
```

## ???? Despliegue

### Producci??n Local
```bash
npm run build
npm run server
```

### Docker (opcional)
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3002
CMD ["npm", "run", "server"]
```

### Variables de Entorno de Producci??n
```env
NODE_ENV=production
PORT=3002
CORS_ORIGIN=https://tu-dominio.com
LOG_LEVEL=warn
```

## ???? Testing

```bash
# Ejecutar tests (cuando est??n implementados)
npm test

# Verificar API
curl http://localhost:3002/health
```

## ???? Documentaci??n Adicional

- **API Documentation**: http://localhost:3002/api-docs
- **Lightweight Charts**: https://tradingview.github.io/lightweight-charts/
- **React Documentation**: https://reactjs.org/

## ???? Seguridad

- CORS configurado para or??genes espec??ficos
- Variables de entorno para configuraci??n sensible
- Validaci??n de par??metros de entrada
- Manejo seguro de errores

## ??????????? Autor

**Enrique Bobadilla**
- GitHub: [@yop007n](https://github.com/yop007n)

## ???? Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Fork el repositorio
2. Crea una rama feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## ???? Soporte

Para soporte t??cnico o preguntas:
- Abrir un issue en GitHub
- Consultar la documentaci??n Swagger
- Revisar los logs del servidor
