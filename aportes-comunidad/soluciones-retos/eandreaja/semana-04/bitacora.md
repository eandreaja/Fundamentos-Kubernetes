# 📔 Bitácora de Aprendizaje — 💾 Semana 04: Configuración y Datos Persistentes

> ⛵ **Tripulante:** [`@eandreaja`](https://github.com/eandreaja)  
> 🗓️ **Fecha de registro:** `2026-11-28`  
> 🎓 **Portafolio Principal:** [⬅️ Volver a mi Portafolio Profesional K8s](../README.md)

---

## 1️⃣ 💡 ¿Qué aprendí esta semana?

Aprendí que un ConfigMap guarda configuración normal y un Secret datos sensibles, y que un Pod los pide por el nombre del objeto y por la `key`. También que un volumen se declara en `volumes` y se conecta en `volumeMounts` con el mismo nombre, y que un PVC se enlaza con un PV cuando la `storageClassName` coincide y el tamaño pedido cabe en lo disponible. Esta semana hice los 5 retos rotos; los laboratorios de la semana 04 los dejo para otro momento.

---

## 2️⃣ 🧩 ¿Qué fue lo más retador y cómo lo resolví?

Lo que más me costó fue distinguir lo que existe de lo que el Pod pide. En el reto 01 confundí `PRECIO_CAFE`, el nombre de la variable dentro del contenedor, con la `key`, que tiene que existir en el ConfigMap (la correcta era `PRECIO_TINTO`). En el reto 02 primero quise cambiar el Secret para que coincidiera con el Pod, y después volví a escribir los valores rotos; lo entendí comparándolo con una dirección mal anotada: se corrige la nota, no se mueve la casa. Además, en `key` va solo el nombre (`API_TOKEN`), no su valor. En el reto 03 vi primero el tamaño y me faltaba la categoría `manual`. En el reto 05 tenía el valor correcto pero señalé la línea del nombre del ConfigMap en vez de la línea de la `key`. También aprendí que algunos campos de un Pod o de un PVC ya creados no se pueden modificar: hubo que borrarlos y crearlos de nuevo. Y que base64 no es cifrado.

---

## 3️⃣ 💻 Comandos y herramientas que practiqué

```bash
kubectl apply -f reto.yaml
kubectl apply --dry-run=server -f reto.yaml
kubectl get pods
kubectl describe pod barista-reto-01
kubectl get secrets
kubectl get pv,pvc
kubectl get storageclass
kubectl describe pvc bodega-reto-03-pvc
kubectl logs barista-reto-01
kubectl exec barista-reto-01 -- printenv PRECIO_CAFE
kubectl delete pod barista-reto-01
git checkout -b eandreaja/semana-04
```

---

## 4️⃣ 🚀 Aplicación real y próximos pasos

En mi proyecto de Python quiero sacar la configuración de la imagen con un ConfigMap, guardar los tokens en un Secret sin subirlos a GitHub y usar un PVC para los datos que no se pueden perder cuando el Pod se reemplace.

---

<div align="center">
  <sub>🏔️☕ Bitácora registrada en <b><a href="https://github.com/edwinbermudez91/Fundamentos-Kubernetes">De Cero a Capitán en Kubernetes — Cloud Native Medellín (CNCF)</a></b></sub>
</div>
