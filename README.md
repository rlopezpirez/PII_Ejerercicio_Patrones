# Ejercicios de DIP, ISP, SRP
## Ejercicio 1 

**DIP:** se cumple o no y por que
No cumple el patron DIP ya que las clases BaseDeDatos y AnlizadorDatos utilizan instancias de DataBaseObject por lo que dependen de esta clase para implementar sus propias responsabilidades (Las clases de alto nivel no deben depender de clases de bajo nivel)

**ISP:** se cumple o no y por que
Se cumple ya que no hay ninguna clase que pida colaboracion a otra mediante tipos (no hay herencia ni interfaces)

**SRP:** se cumple o no y por que
DataBaseObject- Tiene la unica responsabilidad de conocer la estructura de un dato de la base de datos (Cumple SRP)
BaseDeDatos- Tiene la responsabilidad de operar sobre la base de datos, lee, escribe, o selecciona determinados datos (Cumple SRP, no hay mas de un motivo para cambiar la clase)
AnlizadorDatos-Tiene la responsabilidad de chequear que se cumple una determinada condicion en un dato (Cumple SRP , no hay mas de un motivo para cambiar la clase)

## Ejercicio 2 y Ejercicio 3 
//Abstraccion de data base object.
interface IDataBaseObject
{
    public string Descripcion { get; }
}

//Objeto que representa un dato de la base de datos.
class DataBaseObject
{
    public string Descripcion { get; }
}

//Base de datos.
class BaseDeDatos
{
    public IDataBaseObject ObtenerDato(string clave)
    {
        //Devuelve el dato correspondiente a la clave
    }
    public void GrabarDato(string clave, IDataBaseObject dato)
    {
        //Graba el dato en la base de datos, bajo la clave dada
    }
    public String[] ListarClaves()
    {
        //Devuelve un String[] con todas las claves
    }
    public String[] ListarDescripcionDatos()
    {
        //Devuelve un String[] con la descripción de todas los 
        //datos almacenados en  la base
    }
    public DataBaseObject[] ListarDatos()
    {
//Devuelve un DataBaseObject[] con todos los datos almacenados en la base
    }
}
interface ICondicion{
    public bool Cumplecondicion(IDataBaseObject DBobj);
    public void MensajeUno();
    public void MensajeDos();
}
class CondicionF{
    
    public bool Cumplecondicion(IDataBaseObject DBobj)
    {
        //Devuelve true si se cumple una cierta condición
    }
    public void MensajeUno()
    { /*Mensaje predeterminado*/ 
        
    }
    public void MensajeDos()
    { /*Mensaje predeterminado*/ 
        
    }

}
class AnlizadorDatos
{
    private BaseDeDatos baseDatos{get; set;};
    public void Analizar(ICondicion cond)
    {
        foreach (IDataBaseObject DBObj in baseDatos.ListarDatos())
        {
            if (cond.CumpleCondicion(DBObj))
            {
                cond.MensajeUno();
            }
            else
            {
                cond.MensajeDos();
            }
        }
    }
}
