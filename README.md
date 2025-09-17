# 📻 Radio Live App - FM LUZ

Aplicación de radio en vivo con chat interactivo, múltiples temas de colores y base de datos PostgreSQL.

## 🚀 Características Principales

### 📡 **Radio en Vivo**
- Transmisión en tiempo real de FM LUZ
- Controles de reproducción (Play/Pause)
- Control de volumen con botones + y -
- Información de la canción actual
- Reconexión automática en caso de pérdida de señal

### 💬 **Chat en Vivo**
- Sistema de chat en tiempo real
- Persistencia en base de datos PostgreSQL
- Colores únicos automáticos por usuario
- Formato: "correo@ejemplo.com dice: mensaje"
- Historial completo de mensajes
- Timestamps con fecha y hora

### 🎨 **Sistema de Temas**
- **13 temas de colores disponibles:**
  - Light (Claro)
  - Dark (Oscuro)
  - Green (Verde)
  - Blue (Azul)
  - Red (Rojo)
  - Gray (Gris)
  - Purple (Morado)
  - Orange (Naranja)
  - Pink (Rosa)
  - Yellow (Amarillo)
  - Cyan (Cian)
  - Brown (Marrón)
  - Indigo (Índigo)

- Selector visual en cuadrícula 3x5
- Persistencia automática del tema seleccionado
- Aplicación global en toda la interfaz

### 📱 **Interfaz Moderna**
- Diseño responsivo y adaptativo
- Navegación por pestañas
- Carrusel de anuncios
- Gradientes dinámicos según el tema
- Iconos consistentes en color blanco

## 🛠️ Instalación

### Requisitos Previos

- **Node.js** (versión 18 o superior)
- **npm** o **yarn**
- **Expo CLI**
- **PostgreSQL** (para el chat)

### 1. Clonar el Repositorio

```bash
git clone <url-del-repositorio>
cd RADIO
```

### 2. Instalar Dependencias

```bash
npm install
```

### 3. Configurar Base de Datos

1. **Instalar PostgreSQL:**
   - Descargar desde: https://www.postgresql.org/download/
   - Recordar la contraseña del usuario `postgres`

2. **Crear la base de datos:**
   ```sql
   psql -U postgres
   CREATE DATABASE radio_chat;
   \c radio_chat;
   ```

3. **Ejecutar el esquema:**
   ```bash
   psql -U postgres -d radio_chat -f src/database/schema.sql
   ```

4. **Configurar variables de entorno:**
   ```bash
   cp .env.example .env
   ```
   
   Editar `.env` con tus datos:
   ```env
   DB_HOST=localhost
   DB_PORT=5432
   DB_NAME=radio_chat
   DB_USER=postgres
   DB_PASSWORD=tu_contraseña
   ```

### 4. Iniciar la Aplicación

```bash
npm start
```

Para web:
```bash
npm run web
```

## 📖 Guía de Uso

### 🎵 **Controles de Audio**

1. **Reproducir/Pausar:** Botón central con icono de play/pause
2. **Volumen:** Botones + y - en la parte inferior
3. **Información:** Muestra la canción actual y estado de conexión

### 💬 **Usar el Chat**

1. **Abrir chat:** Presionar el botón "Chat en Vivo"
2. **Configurar email:** Ingresar tu email la primera vez
3. **Enviar mensajes:** Escribir y presionar Enter o el botón enviar
4. **Ver historial:** Los mensajes se cargan automáticamente

### 🎨 **Cambiar Temas**

1. **Selector de temas:** Ubicado en la pantalla principal
2. **Selección:** Tocar cualquier color en la cuadrícula
3. **Aplicación:** El tema se aplica inmediatamente
4. **Persistencia:** Se guarda automáticamente

### 📱 **Navegación**

- **Inicio:** Radio y controles principales
- **Info:** Información sobre la estación
- **Configuración:** Ajustes adicionales

## 🏗️ Arquitectura Técnica

### **Frontend**
- **React Native** con Expo
- **TypeScript** para tipado estático
- **React Navigation** para navegación
- **Expo AV** para audio streaming
- **AsyncStorage** para persistencia local

### **Backend/Base de Datos**
- **PostgreSQL** para almacenamiento de mensajes
- **API REST** para operaciones de chat
- **Conexión directa** desde el frontend

### **Servicios**
- **AudioService:** Manejo del streaming de audio
- **DatabaseService:** Conexión y operaciones con PostgreSQL
- **ChatApi:** Endpoints para mensajes del chat
- **ThemeContext:** Gestión global de temas

## 📁 Estructura del Proyecto

```
RADIO/
├── src/
│   ├── api/
│   │   └── chatApi.ts          # API del chat
│   ├── components/
│   │   ├── AdCarousel.tsx      # Carrusel de anuncios
│   │   ├── ChatModal.tsx       # Modal del chat
│   │   └── PlayButton.tsx      # Botón de reproducción
│   ├── constants/
│   │   ├── Colors.ts           # Definición de temas
│   │   └── MockData.ts         # Datos de ejemplo
│   ├── contexts/
│   │   └── ThemeContext.tsx    # Contexto de temas
│   ├── database/
│   │   └── schema.sql          # Esquema de BD
│   ├── screens/
│   │   ├── HomeScreen.tsx      # Pantalla principal
│   │   ├── InfoScreen.tsx      # Información
│   │   └── SettingsScreen.tsx  # Configuración
│   ├── services/
│   │   ├── AudioService.ts     # Servicio de audio
│   │   └── DatabaseService.ts  # Servicio de BD
│   └── types/
│       └── index.ts            # Tipos TypeScript
├── assets/                     # Recursos gráficos
├── .env.example               # Variables de entorno
├── DATABASE_SETUP.md          # Guía de BD
└── package.json               # Dependencias
```

## 🔧 Configuración Avanzada

### **Variables de Entorno**

```env
# Base de Datos
DB_HOST=localhost
DB_PORT=5432
DB_NAME=radio_chat
DB_USER=postgres
DB_PASSWORD=tu_contraseña

# Configuración de Audio (opcional)
STREAM_URL=https://tu-stream-url.com
```

### **Personalización de Temas**

Para agregar nuevos temas, editar `src/constants/Colors.ts`:

```typescript
export type ThemeType = 'light' | 'dark' | 'nuevo_tema';

const themes = {
  nuevo_tema: {
    primary: { main: '#COLOR', light: '#COLOR', dark: '#COLOR' },
    background: { primary: '#COLOR', secondary: '#COLOR', tertiary: '#COLOR' },
    text: { primary: '#COLOR', secondary: '#COLOR', tertiary: '#COLOR', inverse: '#COLOR' },
    gradients: { playButton: ['#COLOR1', '#COLOR2'], background: ['#COLOR1', '#COLOR2'] },
  },
};
```

## 🚀 Despliegue

### **Desarrollo**
```bash
npm start
```

### **Construcción para Producción**
```bash
# Web
npm run build:web

# Android
eas build --platform android

# iOS
eas build --platform ios
```

### **Base de Datos en Producción**
- Usar servicios como AWS RDS, Google Cloud SQL, o Heroku Postgres
- Configurar SSL para conexiones seguras
- Implementar respaldos automáticos

## 🐛 Solución de Problemas

### **Audio no reproduce**
- Verificar conexión a internet
- Comprobar URL del stream
- Revisar permisos de audio

### **Chat no funciona**
- Verificar conexión a PostgreSQL
- Comprobar variables de entorno
- Revisar logs de la base de datos

### **Temas no se guardan**
- Verificar permisos de AsyncStorage
- Limpiar caché de la aplicación

## 📝 Licencia

Este proyecto está bajo la Licencia MIT.

## 👥 Contribución

1. Fork el proyecto
2. Crear una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir un Pull Request

## 📞 Soporte

Para soporte técnico o preguntas:
- Crear un issue en GitHub
- Contactar al equipo de desarrollo

---

**Desarrollado con ❤️ para FM LUZ**# radio_React_Native
# radio_React_Native
