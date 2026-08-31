# 📌 Lineamientos para contribuir a MindFlow AI

## 🌿 Flujo de trabajo (GitFlow)

1. **Ramificación principal**  
   - `main` → siempre contiene código listo para producción.  
   - `develop` → rama de integración donde se fusionan las features.

2. **Creación de ramas**  
   ```bash
   # Desde develop
   git checkout -b feature/<nombre-corto> develop
   # o
   git checkout -b fix/<nombre-corto> develop
   ```

3. **Trabajo y commits**  
   - Realiza commits **atómicos** y descriptivos.  
   - Sigue el formato **Conventional Commits**:

     ```
     <type>(<scope>): <short description>

     [optional body]

     [optional footer(s)]
     ```

   - **Tipos permitidos**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.

   Ejemplo:  
   ```bash
   git commit -m "feat(nlp): add entity extraction for cognitive distortions"
   ```

4. **Sincronización**  
   - `git pull develop` antes de iniciar.  
   - `git push -u origin <rama>` para subir.

5. **Pull Request (PR)**  
   - Abre el PR contra `develop`.  
   - Llena la plantilla (descripción, checklist, capturas).  
   - Al menos **un aprobador** (Lead AI Architect) debe validar antes de merge.

6. **Merge**  
   - Una vez aprobado, se fusiona a `develop` (rebase o squash).  
   - Después de estabilizar, se etiqueta una versión en `main` (`v1.0.0`, etc.).

## 📚 Convenciones de código

- **Python**: seguir `pep 8`, usar `black` / `isort` automáticamente.  
- **JavaScript/TypeScript**: `eslint` + `prettier`.  
- **Documentación**: actualizar `README.md` y `docs/` si cambia la funcionalidad pública.  
- **Tests**: agregar o actualizar tests en `tests/` y asegurar cobertura mínima del 80 % (`pytest --cov`).

## 🛠️ Checklist antes de abrir un PR

- [ ] Código adherido a los linters (`black`, `eslint`).  
- [ ] Tests unitarios/integración pasan (`pytest`).  
- [ ] `CHANGELOG.md` (o la sección de "Unreleased" del `README`) actualizado.  
- [ ] Variables de entorno documentadas en `.env.example`.  
- [ ] `README.md` refleja los nuevos endpoints o cambios de UI.  
- [ ] Disclaimer ético y manejo de PII aún son correctos.

## 📧 Preguntas o dudas

Abre un issue con la etiqueta `question` o contacta al **Lead AI Architect** (Edwin Ibagué).