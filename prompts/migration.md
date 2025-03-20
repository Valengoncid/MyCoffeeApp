# Prompt 1: Migración de Xamarin a .NET MAUI (Creación y Adaptación del Proyecto)

## IMPORTANTE
- Realiza únicamente la migración de Xamarin a .NET MAUI sin añadir nuevas funcionalidades.  
- Asegura compatibilidad total con Windows, Android e iOS.  
- Mantén la arquitectura original en la medida de lo posible.  
- Aplica mejores prácticas de .NET MAUI para optimizar el código y rendimiento.  

## 1. Creación del Proyecto en .NET MAUI
1. Genera un nuevo proyecto .NET MAUI (.NET 8) con el mismo nombre y estructura que el proyecto original en Xamarin.  
2. Configura correctamente el archivo `.csproj` asegurando que:
   - Se utilice el SDK adecuado para .NET 8 y MAUI.
   - Se incluyan las plataformas necesarias: Windows, Android e iOS.  
3. Habilita permisos y configuraciones necesarias en los archivos `AndroidManifest.xml`, `Info.plist` y `appsettings.json`.

## 2. Migración de Código y Estructura

### Migración de Archivos
- Copia todas las vistas (`.xaml`) y archivos de código (`.cs`).  
- Adapta las referencias y namespaces, cambiando:
  - `Xamarin.Forms` → `Microsoft.Maui.Controls`  
  - `Xamarin.Essentials` → `Microsoft.Maui.Essentials`  
- Convierte efectos visuales y estilos asegurando compatibilidad con `Microsoft.Maui.Graphics`.  

### Adaptación de Componentes Clave
| Xamarin.Forms        | Equivalente en .NET MAUI |
|----------------------|-------------------------|
| `ContentPage`       | `ContentPage`           |
| `NavigationPage`    | `NavigationPage`        |
| `TabbedPage`        | `Shell` o `TabbedPage`  |
| `MasterDetailPage`  | `FlyoutPage`            |
| `DependencyService` | `Service Provider`      |
| `Effects`           | `Graphics Effects`      |

### Migración de ViewModels y Models
- Asegura que todos los bindings y `INotifyPropertyChanged` sigan funcionando correctamente.  
- Ajusta la navegación reemplazando `PushAsync()` y `PopAsync()` por el nuevo sistema de navegación de MAUI basado en `Shell`.  
- Valida eventos y comandos (`Command`, `EventHandler`), asegurando su correcto funcionamiento en MAUI.  

## 3. Actualización de Dependencias y Librerías

### Frameworks Core
- `Xamarin.Forms` → `Microsoft.Maui.Controls`  
- `Xamarin.Essentials` → `Microsoft.Maui.Essentials`  

### Librerías Externas
Verifica y reemplaza dependencias para asegurar compatibilidad con MAUI:  

| Librería Xamarin     | Alternativa en .NET MAUI |
|----------------------|-------------------------|
| `sqlite-net-pcl`    | `sqlite-net-pcl` (actualizado) |
| `FFImageLoading`    | `Microsoft.Maui.Graphics` o `ImageSource` |
| `Plugin.Permissions`| `Permissions` en MAUI.Essentials |
| `Xamarin.Forms.Maps`| `Microsoft.Maui.Controls.Maps` |

### Renderizadores y Handlers
- Sustituye `Custom Renderers` por `Handlers` en MAUI para mejorar rendimiento.  
- Verifica que los `Handlers` personalizados estén correctamente implementados.  

## 4. Pruebas y Optimización

### Corrección de Errores
- Identifica y soluciona errores causados por cambios en el modelo de MAUI.  
- Usa `#if ANDROID`, `#if WINDOWS`, `#if IOS` para manejar especificaciones por plataforma.  

### Pruebas en Dispositivos
- Ejecuta y valida la aplicación en Windows, Android e iOS.  
- Usa depuración avanzada y registros (`Debug.WriteLine`, `ILogger`) para detectar problemas.  

### Optimización Final
- Refactoriza código redundante y optimiza carga de vistas y bindings.  
- Mejora la performance asegurando uso eficiente de `Handlers` y `Resources`.  

## Objetivo Final
El proyecto migrado debe:  
- Mantener la misma funcionalidad que el original en Xamarin.  
- Ser totalmente funcional en Windows, Android e iOS.  
- Estar optimizado para .NET MAUI con mejoras en rendimiento y arquitectura.  