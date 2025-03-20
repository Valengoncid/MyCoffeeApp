# Verificación y Pruebas en la Migración a .NET MAUI  

## 1. Verificación de Dependencias y Compilación  
1. **Comprobación de dependencias**  
   - Revisa el archivo `.csproj` y confirma que todas las dependencias sean compatibles con .NET MAUI.  
   - Sustituye cualquier paquete de Xamarin obsoleto por su equivalente en MAUI.  
   - Asegura que `sqlite-net-pcl`, `Microsoft.Maui.Essentials` y otros paquetes críticos estén correctamente referenciados.  

2. **Compilación sin errores**  
   - Confirma que el código compile correctamente en todos los frameworks de destino: Windows, Android e iOS.  
   - Si aparece el error `CS1061` relacionado con `Run()`, revisa la configuración en `Program.cs` y asegúrate de que `MauiApp.CreateBuilder()` esté correctamente definido.  
   - Verifica la compatibilidad de `Handlers`, `Effects` y `Custom Renderers` migrados desde Xamarin.  

## 2. Pruebas en Plataformas  
1. **Ejecución en Entornos Reales**  
   - Ejecuta la aplicación en emuladores y dispositivos físicos de Android, iOS y Windows.  
   - Asegura que todas las funcionalidades principales respondan correctamente en cada plataforma.  

2. **Validación de Navegación y Flujo de la App**  
   - Prueba la navegación asegurando que las rutas en `Shell` funcionan correctamente.  
   - Verifica que `Navigation.PushAsync()` y `Navigation.PopAsync()` hayan sido correctamente migrados a `Shell Navigation`.  
   - Asegura que la inyección de dependencias (`DependencyService` → `MauiApp.ConfigureServices()`) esté funcionando sin errores.  

## 3. Pruebas de Almacenamiento y UI  
1. **Validación de Base de Datos y Almacenamiento Local**  
   - Asegura que `sqlite-net-pcl` funcione correctamente en cada plataforma.  
   - Verifica que los datos se guarden y recuperen correctamente desde `FileSystem.AppDataDirectory`.  
   - Si la app usa `SecureStorage` o `Preferences`, comprueba que los valores se almacenen y recuperen sin problemas.  

2. **Comprobación de la UI y Renderizado**  
   - Valida que las vistas se rendericen correctamente en cada plataforma y en diferentes tamaños de pantalla.  
   - Asegura que los estilos, temas y fuentes sean consistentes en Windows, Android e iOS.  
   - Verifica que los `Handlers` reemplacen correctamente los `Renderers` y que los controles personalizados funcionen adecuadamente.  

## 4. Limpieza Final  
1. **Eliminación de Código Obsoleto**  
   - Remueve cualquier código comentado o dependencias no utilizadas de Xamarin.  
   - Elimina archivos innecesarios y referencias a `Renderers` si ya fueron reemplazados por `Handlers`.  

2. **Documentación de Cambios**  
   - Registra las modificaciones realizadas en la migración.  
   - Documenta cualquier cambio relevante en la estructura del código, navegación y configuración de dependencias.  
   - Proporciona notas sobre soluciones a errores encontrados durante la migración.  

## Objetivo Final  
El proyecto debe estar completamente migrado a .NET MAUI y cumplir con los siguientes criterios:  
- Funcionamiento estable y sin errores en Windows, Android e iOS.  
- Correcta navegación, almacenamiento y renderizado de la UI.  
- Código optimizado, limpio y sin dependencias obsoletas.  
- Documentación clara sobre los cambios aplicados en la migración.  
