# Proyecto Maven vulnerable

Este proyecto multi-módulo se creó intencionalmente para incluir dependencias que traen bibliotecas transitivas con vulnerabilidades conocidas, con fines de prueba y auditoría.

Estructura relevante:
- `vuln-lib1` -> depende de `commons-configuration:1.6` (trae `commons-collections:3.2.1` y `commons-beanutils-core` como dependencias transitivas)
- `vuln-lib2` -> depende de `commons-digester:1.8` (trae `commons-beanutils:1.7.0` transitivamente)
- `vuln-lib3` -> depende de `com.sun.jersey:jersey-json:1.9` (trae `org.codehaus.jackson:jackson-mapper-asl:1.8.3` transitivamente)
- `app` -> depende de los tres módulos anteriores (las vulnerabilidades aparecen como dependencias transitivas)

Cómo ver el árbol de dependencias para el módulo `app`:

```powershell
cd test_repo_personal
mvn -pl app dependency:tree
```

Nota: Este proyecto está diseñado para pruebas locales. No lo despliegues en producción.
