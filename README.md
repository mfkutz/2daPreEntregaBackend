Con base en nuestra implementación actual de productos, modificar el método GET / para que cumpla con los siguientes puntos:

- Deberá poder recibir por query params un limit (opcional), una page (opcional), un sort (opcional) y un query (opcional) ✅

- limit permitirá devolver sólo el número de elementos solicitados al momento de la petición, en caso de no recibir limit, éste será de 10.✅

http://localhost:8080/api/products

http://localhost:8080/api/products?limit=2

![alt text](.src/public/images/image.png)

- page permitirá devolver la página que queremos buscar, en caso de no recibir page, ésta será de 1. ✅

http://localhost:8080/api/products?limit=2&page=3
![alt text](/images/image-1.png)

control en caso de introducir una pagina inexistente

http://localhost:8080/api/products?page=4000
http://localhost:8080/api/products?page=-4000
http://localhost:8080/api/products?page=ffffffasd

![alt text](image-13.png)

- query, el tipo de elemento que quiero buscar (es decir, qué filtro aplicar), en caso de no recibir query, realizar la búsqueda general✅

Aqui la disponibilidad depende del stock disponible, true o false

http://localhost:8080/api/products?available=false

![alt text](image-3.png)

http://localhost:8080/api/products?category=frenos

- Todas las cat
  frenos
  cadena
  neumatico
  filtro
  carenados
  manillar
  escape
  amortiguador
  rodamientos
  kitfreno

![alt text](image-2.png)

- sort: asc/desc, para realizar ordenamiento ascendente o descendente por precio, en caso de no recibir sort, no realizar ningún ordenamiento✅

http://localhost:8080/api/products?sort=asc

![alt text](image-4.png)

- El método GET deberá devolver un objeto con el siguiente formato:
  {
  status:success/error
  payload: Resultado de los productos solicitados
  totalPages: Total de páginas
  prevPage: Página anterior
  nextPage: Página siguiente
  page: Página actual
  hasPrevPage: Indicador para saber si la página previa existe
  hasNextPage: Indicador para saber si la página siguiente existe.
  prevLink: Link directo a la página previa (null si hasPrevPage=false)
  nextLink: Link directo a la página siguiente (null si hasNextPage=false)
  }✅

  ![alt text](image-5.png)

-Se deberá poder buscar productos por categoría o por disponibilidad, y se deberá poder realizar un ordenamiento de
estos productos de manera ascendente o descendente por precio. ✅

Además, agregar al router de carts los siguientes endpoints:

- DELETE api/carts/:cid/products/:pid deberá eliminar del carrito el producto seleccionado.✅

http://localhost:8080/api/carts/65d7e7b7fbde72ff1ca1331c/products/65d79970965a8c28cd22b3b7

![alt text](image-6.png)

- PUT api/carts/:cid deberá actualizar el carrito con un arreglo de productos con el formato especificado arriba. ✅

http://localhost:8080/api/carts/65da7d910d6fcf333e2527d7

ejemplo :

{
"products": [
{ "product": "65d798f5965a8c28cd22711b", "quantity": 2 },
{ "product": "65d7992e965a8c28cd2290d9", "quantity": 1 },
{ "product": "65d7992e965a8c28cd2290da", "quantity": 3 }
]
}

![alt text](image-7.png)

- PUT api/carts/:cid/products/:pid deberá poder actualizar SÓLO la cantidad de ejemplares del
  producto por cualquier cantidad pasada desde req.body ✅

  http://localhost:8080/api/carts/65da7d910d6fcf333e2527d7/products/65d798f5965a8c28cd22711b

  ![alt text](image-8.png)

  Aqui le hice un pequeño control de stock, si ponemos mas del existente saldrá un error
  ![alt text](image-9.png)

- DELETE api/carts/:cid deberá eliminar todos los productos del carrito✅

http://localhost:8080/api/carts/65d7e7b7fbde72ff1ca1331c

![alt text](image-10.png)

- Esta vez, para el modelo de Carts, en su propiedad products, el id de cada producto generado dentro del
  array tiene que hacer referencia al modelo de Products. Modificar la ruta /:cid para que al traer todos
  los productos, los traiga completos mediante un “populate”. De esta manera almacenamos sólo el Id, pero
  al solicitarlo podemos desglosar los productos asociados.✅

- Crear una vista en el router de views ‘/products’ para visualizar todos los productos con su respectiva paginación. ✅

http://localhost:8080/products

![alt text](image-11.png)

- Contar con el botón de “agregar al carrito” directamente, sin necesidad de abrir una página adicional con los detalles del producto.✅

- Además, agregar una vista en ‘/carts/:cid (cartId) para visualizar un carrito específico, donde se deberán listar SOLO los productos que pertenezcan a dicho carrito. ✅

http://localhost:8080/carts/65da7d910d6fcf333e2527d7

![alt text](image-12.png)
