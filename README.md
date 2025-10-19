# 🚀 Angular Clean Architecture Boilerplate

Una implementación completa de **Clean Architecture** para Angular con i18n, gestión de estado y mejores prácticas de desarrollo.

## ✨ Características principales

- **🏗️ Clean Architecture**: Separación clara entre capas (Core, Data, Presentation)
- **🌍 i18n Completo**: Sistema de internacionalización reactivo y tipado
- **📱 Responsive Design**: Interfaz adaptable con PrimeNG + PrimeFlex
- **🔧 TypeScript Strict**: Tipado fuerte y configuración estricta
- **🎯 SOLID Principles**: Implementación de principios de diseño
- **🧪 Testing Ready**: Configuración lista para pruebas unitarias
- **📦 Modular Architecture**: Estructura por features escalable
- **🚀 Production Ready**: Optimizado para producción

## 🛠️ Stack tecnológico

- **Framework**: Angular 17+
- **Lenguaje**: TypeScript
- **UI Library**: PrimeNG + PrimeFlex
- **Reactive Programming**: RxJS
- **Internacionalización**: ngx-translate
- **Code Quality**: ESLint + Prettier
- **Testing**: Jasmine + Karma

## 📁 Estructura del proyecto

```
src/app/
├── core/                    # 🎯 Lógica de negocio y servicios base
│   ├── components/          # Componentes base reutilizables
│   ├── entities/            # Entidades del dominio
│   ├── i18n/               # Sistema de internacionalización
│   │   ├── config/         # Configuración, constantes y tipos
│   │   └── services/       # Servicios especializados de i18n
│   └── service-providers/  # Configuración de inyección de dependencias
├── shared/                  # 🔧 Servicios y componentes compartidos
│   ├── components/         # Componentes UI compartidos
│   └── services/           # Servicios utilitarios
├── features/               # 📦 Módulos por funcionalidad
│   └── example-feature/    # Ejemplo de feature completo
│       ├── core/           # Lógica de negocio del feature
│       ├── data/           # Repositorios e implementaciones
│       └── presentation/   # Componentes y páginas
└── layout/                 # 🎨 Componentes de layout principal
```

## 🚀 Inicio rápido

### 1. **Clonar el repositorio**

```bash
git clone https://github.com/tu-usuario/angular-clean-architecture.git
cd angular-clean-architecture
```

### 2. **Instalar dependencias**

```bash
npm install
```

### 3. **Ejecutar en desarrollo**

```bash
npm start
```

### 4. **Abrir en el navegador**

```
http://localhost:4200
```

## 📋 Scripts disponibles

| Comando              | Descripción                                |
| -------------------- | ------------------------------------------ |
| `npm start`          | Inicia el servidor de desarrollo           |
| `npm run build`      | Construye la aplicación para producción    |
| `npm run build:dev`  | Construye para desarrollo                  |
| `npm run build:qa`   | Construye para QA                          |
| `npm run build:prod` | Construye para producción                  |
| `npm test`           | Ejecuta las pruebas unitarias              |
| `npm run lint`       | Ejecuta el linter                          |
| `npm run lint:fix`   | Corrige automáticamente errores de linting |
| `npm run format`     | Formatea el código con Prettier            |
| `npm run type-check` | Verifica los tipos de TypeScript           |

## 🏗️ Arquitectura Clean

### **Capas de la aplicación:**

1. **🎯 Core (Dominio)**
   - Entidades de negocio
   - Casos de uso (Interactors)
   - Interfaces de repositorios
   - Reglas de negocio

2. **📊 Data (Infraestructura)**
   - Implementaciones de repositorios
   - Servicios externos (APIs)
   - Mappers de datos
   - Fuentes de datos

3. **🎨 Presentation (UI)**
   - Componentes Angular
   - Páginas y routing
   - Gestión de estado local
   - Interacción con el usuario

### **Principios aplicados:**

- **Dependency Inversion**: Las capas internas no dependen de las externas
- **Single Responsibility**: Cada clase tiene una única responsabilidad
- **Open/Closed**: Abierto para extensión, cerrado para modificación
- **Interface Segregation**: Interfaces específicas y cohesivas
- **Liskov Substitution**: Las implementaciones son intercambiables

## 🌍 Sistema de i18n

### **Características:**

- **Tipado fuerte**: Interfaces explícitas para traducciones
- **Reactividad**: Cambio automático de idioma en toda la app
- **Configuración centralizada**: Un solo lugar para definir textos
- **Fallbacks**: Textos por defecto si falta una traducción

### **Uso básico:**

```typescript
// 1. Definir configuración
export const MyPageConfig: I18nConfigEntity = {
  i18n: {
    title: 'mypage.title',
    subtitle: 'mypage.subtitle'
  }
};

// 2. En el componente
export class MyPageComponent implements OnInit {
  public texts: ResolvedMyPageTexts = {} as ResolvedMyPageTexts;

  ngOnInit() {
    this.i18nService.getReactiveTexts(MyPageConfig)
      .subscribe(texts => this.texts = texts);
  }
}

// 3. En el template
<h1>{{ texts.title }}</h1>
<p>{{ texts.subtitle }}</p>
```

## 🧪 Testing

### **Ejecutar pruebas:**

```bash
# Todas las pruebas
npm test

# Pruebas en modo watch
npm run test:watch

# Cobertura de código
npm run test:coverage
```

### **Estructura de pruebas:**

- **Unit Tests**: Para servicios y lógica de negocio
- **Component Tests**: Para componentes Angular
- **Integration Tests**: Para flujos completos

## 📦 Crear un nuevo feature

### **1. Estructura del feature:**

```
src/app/features/mi-feature/
├── core/
│   ├── entities/           # Entidades del dominio
│   ├── repositories/       # Interfaces de repositorios
│   ├── usecases/          # Casos de uso
│   └── interactor/        # Orquestador principal
├── data/
│   └── repositories/      # Implementaciones
└── presentation/
    ├── pages/             # Páginas del feature
    ├── components/        # Componentes específicos
    └── mi-feature.module.ts
```

### **2. Comandos útiles:**

```bash
# Generar componente
ng generate component features/mi-feature/presentation/pages/mi-page

# Generar servicio
ng generate service features/mi-feature/core/services/mi-service

# Generar módulo
ng generate module features/mi-feature/presentation/mi-feature
```

## 🔧 Configuración de entornos

### **Archivos de entorno:**

- `environment.ts` - Desarrollo
- `environment.dev.ts` - Desarrollo
- `environment.qa.ts` - QA/Testing
- `environment.pdn.ts` - Producción

### **Uso:**

```typescript
import { environment } from '@environments/environment';

const apiUrl = environment.apiUrl;
const production = environment.production;
```

## 📝 Convenciones de código

### **Naming conventions:**

- **Archivos**: `kebab-case.type.ts`
- **Clases**: `PascalCase`
- **Variables/Métodos**: `camelCase`
- **Constantes**: `UPPER_SNAKE_CASE`
- **Interfaces**: `PascalCase` + sufijo `Entity` o `Interface`

### **Estructura de imports:**

```typescript
// 1. Angular core
import { Component, OnInit } from '@angular/core';

// 2. Librerías externas
import { Observable } from 'rxjs';

// 3. Imports internos (usando path mapping)
import { MyService } from '@core/services';
import { MyEntity } from '@shared/entities';
```

## 🤝 Contribuir

1. **Fork** el proyecto
2. **Crea** una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. **Commit** tus cambios (`git commit -m 'feat: agregar nueva funcionalidad'`)
4. **Push** a la rama (`git push origin feature/nueva-funcionalidad`)
5. **Abre** un Pull Request

### **Convención de commits:**

- `feat:` Nueva funcionalidad
- `fix:` Corrección de bug
- `docs:` Documentación
- `style:` Formato de código
- `refactor:` Refactorización
- `test:` Pruebas
- `chore:` Tareas de mantenimiento

## 📄 Licencia

Este proyecto está bajo la **Licencia MIT**. Ver el archivo [LICENSE](LICENSE) para más detalles.

## 🙏 Agradecimientos

- **Angular Team** por el increíble framework
- **PrimeNG** por los componentes UI
- **Clean Architecture** por los principios de diseño
- **Comunidad Open Source** por las librerías utilizadas

---

## 📞 Soporte

¿Tienes preguntas o sugerencias?

- 🐛 **Issues**: [GitHub Issues](https://github.com/Crooks2k/angular-clean-architecture/issues)
- 💬 **Discusiones**: [GitHub Discussions](https://github.com/Crooks2k/angular-clean-architecture/discussions)
- 📧 **Email**: danielcol247@gmail.com

---

**¡Construye aplicaciones Angular escalables y mantenibles! 🚀**
