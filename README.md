# Proyecto Maven vulnerable

Este proyecto multi-módulo se creó intencionalmente para incluir dependencias que traen bibliotecas transitivas con vulnerabilidades conocidas, con fines de prueba y auditoría.

Estructura relevante:
- `vuln-lib1` -> depende de `commons-configuration:1.6` (que trae `commons-collections:3.2.1` como dependencia transitiva)
- `vuln-lib2` -> depende de `commons-beanutils:1.8.3`
- `vuln-lib3` -> depende de `jackson-mapper-asl:1.9.13`
- `app` -> depende de los tres módulos anteriores (las vulnerabilidades aparecen como dependencias transitivas)

Cómo ver el árbol de dependencias para el módulo `app`:

```powershell
cd test_repo_personal
mvn -pl app dependency:tree
```

Nota: Este proyecto está diseñado para pruebas locales. No lo despliegues en producción.
