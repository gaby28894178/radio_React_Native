# 📻 Radio Live App - FM LUZ

Aplicación de radio en vivo con chat interactivo, múltiples temas de colores y sistema de chat sincronizado.

## 🌐 Enlaces del Proyecto

- **🔗 GitHub Repository:** [https://github.com/tu-usuario/radio_React_Native](https://github.com/tu-usuario/radio_React_Native)
- **🚀 Vercel Deployment:** [https://tu-proyecto.vercel.app](https://tu-proyecto.vercel.app)
- **📱 Demo en Vivo:** [http://localhost:8081](http://localhost:8081) (desarrollo local)

## 🚀 Características Principales

### 📡 **Radio en Vivo**
- Transmisión en tiempo real de FM LUZ
- Controles de reproducción (Play/Pause)
- Control de volumen con botones + y -
- Información de la canción actual
- Reconexión automática en caso de pérdida de señal

### 💬 **Chat en Vivo**
- Sistema de chat en tiempo real sincronizado
- Persistencia con localStorage
- Nicknames automáticos basados en iniciales del email
- Fondos diferenciados para mensajes propios y de otros
- Formato: "[NK]: mensaje" (donde NK son las iniciales)
- Sincronización entre pestañas del navegador
- Protección de privacidad del email

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

### 3. Configuración del Chat

El sistema de chat no requiere configuración adicional ya que utiliza localStorage para la persistencia y sincronización en tiempo real.

**Características del chat:**
- Almacenamiento local automático
- Sincronización entre pestañas
- Nicknames basados en iniciales del email
- No requiere base de datos externa

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
2. **Configurar email:** Ingresar tu email la primera vez (se genera nickname automático)
3. **Enviar mensajes:** Escribir y presionar Enter o el botón enviar
4. **Ver historial:** Los mensajes se sincronizan automáticamente
5. **Identificación:** Tus mensajes tienen fondo gris oscuro, los de otros gris claro

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

### **Sistema de Chat**
- **localStorage** para persistencia local
- **Storage Events** para sincronización en tiempo real
- **SharedChatService** para gestión de mensajes compartidos

### **Servicios**
- **AudioService:** Manejo del streaming de audio
- **DatabaseService:** Gestión de mensajes locales
- **SharedChatService:** Sincronización entre pestañas
- **StorageEventService:** Eventos de almacenamiento
- **ChatApi:** API para operaciones de chat
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

### **Desarrollo Local**
```bash
npm start
# o para web específicamente:
npm run web
```

### **Despliegue en Vercel**

#### Configuración de Vercel (`vercel.json`)
```json
{
  "installCommand": "npm install --legacy-peer-deps",
  "buildCommand": "npx expo export --platform web",
  "outputDirectory": "dist",
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

#### Archivos Ignorados (`.vercelignore`)
```
node_modules
build
dist
.git
.trae
.log
.figma
```

#### Comandos de Despliegue
```bash
# Instalar Vercel CLI
npm i -g vercel

# Desplegar
vercel

# Desplegar a producción
vercel --prod
```

### **Construcción para Otras Plataformas**
```bash
# Web (local)
npm run build:web

# Android
eas build --platform android

# iOS
eas build --platform ios
```

### **Sistema de Chat**
- Utiliza localStorage para persistencia
- Sincronización en tiempo real entre pestañas
- No requiere base de datos externa para funcionar

## 🐛 Solución de Problemas

### **Audio no reproduce**
- Verificar conexión a internet
- Comprobar URL del stream
- Revisar permisos de audio

### **Chat no funciona**
- Verificar que localStorage esté habilitado
- Comprobar permisos del navegador
- Revisar la consola del navegador para errores

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

## 📚 Referencias Útiles

### **Documentación Técnica**
- [Expo Documentation](https://docs.expo.dev/)
- [React Native Documentation](https://reactnative.dev/docs/getting-started)
- [Vercel Deployment Guide](https://vercel.com/docs)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)

### **APIs y Servicios**
- [Expo AV (Audio/Video)](https://docs.expo.dev/versions/latest/sdk/av/)
- [AsyncStorage](https://docs.expo.dev/versions/latest/sdk/async-storage/)
- [React Navigation](https://reactnavigation.org/docs/getting-started)

### **Configuración de Vercel**
- [Vercel CLI](https://vercel.com/docs/cli)
- [Vercel Configuration](https://vercel.com/docs/project-configuration)
- [Custom Build Commands](https://vercel.com/docs/build-step#build-command)

### **Herramientas de Desarrollo**
- [Expo CLI](https://docs.expo.dev/workflow/expo-cli/)
- [EAS Build](https://docs.expo.dev/build/introduction/)
- [Expo Web](https://docs.expo.dev/workflow/web/)

---

**Desarrollado con ❤️ para FM LUZ**

*Radio FM LUZ - Conectando corazones a través de la música cristiana*
