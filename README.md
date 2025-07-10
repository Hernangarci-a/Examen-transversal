# Examen-transversal
productos = {'8475HD': ['HP', 15.6, '8GB', 'DD', '1T', 'Intel Core i5', 'Nvidia GTX1050'],
'2175HD': ['lenovo', 14, '4GB', 'SSD', '512GB', 'Intel Core i5', 'Nvidia GTX1050'],
'JjfFHD': ['Asus', 14, '16GB', 'SSD', '256GB', 'Intel Core i7', 'Nvidia RTX2080Ti'],
'fgdxFHD': ['HP', 15.6, '8GB', 'DD', '1T', 'Intel Core i3', 'integrada'],
'GF75HD': ['Asus', 15.6, '8GB', 'DD', '1T', 'Intel Core i7', 'Nvidia GTX1050'],
'123FHD': ['lenovo', 14, '6GB', 'DD', '1T', 'AMD Ryzen 5', 'integrada'],
'342FHD': ['lenovo', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 7', 'Nvidia GTX1050'],
'UWU131HD': ['Dell', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 3', 'Nvidia GTX1050'],
}

stock = {'8475HD': [387990,10], '2175HD': [327990,4], 'JjfFHD': [424990,1],
'fgdxFHD': [664990,21], '123FHD': [290890,32], '342FHD': [444990,7],
'GF75HD': [749990,2], 'UWU131HD': [349990,1], 'FS1230HD': [249990,0],
}

def stock_marca(marca):
    total = 0
    for codigo, datos in productos.items():
        if datos[0].lower() == marca.lower():
            total += stock[codigo][1]
    print(f"El stock total para {marca} es {total}")

def busqueda_precio(precio_min, precio_max):
    resultados = []
    for modelo, datos in stock.items():
        precio = datos[0]
        if precio >= precio_min and precio <= precio_max and productos[modelo][0]:
            resultados.append(modelo + '--' + datos[0])
    if resultados:
        resultados.sort()
        print("Productos encontrados: ", resultados)
    else:
        print("No hay productos en ese rango de precio.")

def actualizar_precio(modelo, p):
    if modelo in productos:
        stock[modelo][0] = p
        return True
    return False

def main():
    while True:
        print("*** MENU PRINCIPAL ***")
        print("1.Stock marca.")
        print("2.Busqueda por precio.")
        print("3.Actualizar precio.")
        print("4.Salir.")

        try:
            opc = int(input("Ingrese una opcion del menu: "))
        except ValueError:
            print("Debe ingresar un valor numerico")
        if opc == 1:
            marca = input("Ingrese la marca ")
            stock_marca(marca)
        elif opc == 2:
            try:
                precio_min = float(input("Ingrese precio minimo: "))
                precio_max = float(input("Ingrese precio maximo: "))
                busqueda_precio(precio_min, precio_max)
            except ValueError:
                print("Debe ingresar un valores numericos ")
        elif opc == 3:
            while True:
                try:
                    modelo = input("Ingrese el modelo del produto: ")
                    p = int(input("ingrese nuevo precio: "))
                    if actualizar_precio(modelo, p):
                        print("stock actalizado!")
                    else:
                        print("la marca no existe")
                except ValueError:
                    print("Debe ingresar valores numericos")
                
                repetir = input("Desea actualizar otro producto (S/N) ").lower()
                if repetir != 's':
                    break
        elif opc == 4:
            print("Programa finalizado.")
            break
        else:
            print("Debe seleccionar una opción válida!!.")

if __name__ == "__main__":
    main()
