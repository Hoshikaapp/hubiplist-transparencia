# Transparencia de HubIPList

Este repositorio es el **registro público e inmutable** de las listas que publica
[HubIPList](https://hubiplist.com). Una vez al día, un proceso automático descarga el
manifiesto oficial (`https://hubiplist.com/api/transparency/manifest`) y lo commitea aquí.

## Qué garantiza esto

Que ninguna IP puede desaparecer de una lista en silencio. Cada commit registra,
para cada lista pública (blocklists de amenazas y rangos de proveedores):

- el número de entradas,
- el SHA-256 del contenido exacto servido en ese momento,
- la fecha de generación.

El historial de commits lo timestampa GitHub, un tercero: alterar el pasado exigiría
manipular también este historial público.

## Cómo verificar una lista

1. Descarga la lista, p. ej. `curl https://hubiplist.com/feeds/public/blocklists/consenso.txt`.
2. Calcula su hash: `sha256sum consenso.txt`.
3. Compáralo con el manifiesto del día en `manifest/` de este repo, o con
   `https://hubiplist.com/feeds/public/blocklists/consenso.txt.sha256`.
4. Si una IP desapareció de una lista, consulta su historial público:
   `https://hubiplist.com/api/transparency/ip-history?ip=<IP>` — cada salida tiene
   motivo (caducó o su fuente dejó de marcarla).

Las listas se generan mecánicamente desde las fuentes citadas en
`https://hubiplist.com/docs` (que no controla HubIPList); nadie las edita a mano.
