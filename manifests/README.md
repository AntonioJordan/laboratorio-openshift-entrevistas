# Manifests RealWorld MicroShift

## Orden de despliegue

1. **base/**  
   Aplica primero. Crea el namespace, las políticas de red y RBAC.  
   `oc apply -f base/`

2. **postgres/**  
   Crea los recursos de base de datos: secreto, PVC, deployment y servicio.  
   `oc apply -f postgres/`

3. **backend/**  
   Despliega la API Node.js, su configmap y servicio.  
   `oc apply -f backend/`

4. **frontend/**  
   Despliega la web React, servicio y route para exponer externamente.  
   `oc apply -f frontend/`

---

## Propósito de cada carpeta

- **base/**  
  Recursos comunes y globales: namespace, seguridad (networkpolicy, rbac).

- **postgres/**  
  Componentes de la base de datos: volumen persistente, secreto de credenciales, despliegue, servicio.

- **backend/**  
  Configuración y despliegue del backend (API), variables, servicio interno.

- **frontend/**  
  Configuración y despliegue del frontend, servicio y route público.

---

## Recomendaciones

- Verifica el estado tras cada paso:  
  `oc get all -n tonijordanrodriguez6-dev`
- Personaliza credenciales en los secretos.
- Todos los manifiestos incluyen `metadata.namespace: tonijordanrodriguez6-dev`.
