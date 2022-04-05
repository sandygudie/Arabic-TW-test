# Checklist for Code Testing

This checklist contains a lot of items. Como {ref}`mencionó antes<rr-testing-write-tests>`, es mucho mejor hacer algunos de los elementos que ninguno de ellos. Do not be discouraged if this list of tasks seems insurmountable.

<a name="Writing_tests"></a>

## Writing tests

- Write a few smoke tests.
- Write unit tests for all your code units.
- Write integration tests to check the integration between units.
- Write a few system tests. Prioritise common and important paths through the program.
- Write regression tests. Regression tests can exist at any level of testing.
- If appropriate for your project write acceptance tests.
- Add runtime tests into your project.

<a name="Good_practice_checks"></a>

## Good practice checks

- [ ] Documentar las pruebas y cómo ejecutarlas.
  - [ ] Escribe scripts para configurar y configurar cualquier recurso necesario para ejecutar las pruebas.
- [ ] Escoja y haga uso de un framework de pruebas.
- [ ] Ejecute las pruebas regularmente.
  - [ ] Automatizar el proceso de ejecución de pruebas. Considere hacer uso de la integración continua (ver el capítulo de integración continua) para hacer esto.
- [ ] Comprueba la cobertura de código de tus pruebas e intenta mejorarla.
- [ ] Introducir en la revisión de código con un socio.
