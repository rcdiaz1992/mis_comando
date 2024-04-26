# mis_comando

db.getCollection('impAfrActa').find({"data.numDim":"DI-2022-234-2107280"})
db.getCollection('impAfrActa').find({"data.numDim":"DI-2023-401-2457450"})
db.getCollection('impDim').find({"data.num":"DI-2022-234-2107280"})
db.getCollection('message').find({"data.numDeclaracion":"ARIVV-2022-234-45"})
db.getCollection('message').find({"data.sender":"ADAKRONOS"})
db.getCollection('notificacion').find({"data.nomPro":"DI-2022-234-2107280"})
db.getCollection('impDatosMercanciaDimAforo').find({"data.dim.id":"944af26b-6a58-4705-88a1-ce23e0a8322e"},{"data.codSubAra":1})
db.getCollection('impAfrActa').find({"data.numDim":"DI-2023-401-2457450"})

db.getCollection('impDim').find({
  "data.fecTra": {
    $gte: ISODate("2023-12-22T00:00:00.000Z"),
    $lt: ISODate("2023-12-23T00:00:00.000Z")
  },"data.estAct":"EN_AFORO"
});
db.getCollection('impDim').find({"data.num":"DI-2023-201-2119666"})
db.getCollection('impAfrActa').find({"data.numDim":"DI-2023-422-2460356"})
db.getCollection('impAfrActa').find({
  "log.est.nom": "EN_AFORO",
  "log.est.usu": { $ne: "BPM" }
});



backend
npm run build:lib --deployar librerias
npm run publish:lib --publicar interfaces en nexus
npm run start:dev --para ejecutar y cada cambio se reejecute
npm run update:lib --actualizar dependencias 


--reporte UCOA
SELECT
  *
FROM
  sin.bitacora_consulta_sin a
WHERE a.factura_valida = true and a.transaccion=true and 
  (a.nit_proveedor, a.nro_factura, a.codigo_autorizacion_factura) IN (
    SELECT
      b.nit_proveedor,
      b.nro_factura,
      b.codigo_autorizacion_factura
    FROM
      sin.bitacora_consulta_sin b where b.factura_valida = true and b.transaccion=true
    GROUP BY
      b.nit_proveedor,
      b.nro_factura,
      b.codigo_autorizacion_factura
    HAVING
      COUNT(*) >= 2
  )
