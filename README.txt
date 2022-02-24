#1 - IsPostBack

Es una variable de tipo bool para identificar si la página ha sido cargada por primera vez o es una recarga.

Inicia en false, indicando que es la primera carga.
True, indica que es una recarga de página.

¿Cómo funciona?

Dentro del Page_Load del archivo C# de una pagina aspx, debemos de colocar un validador como lo siguiente.


protected void Page_Load(object sender, EventArgs e)
{
    if (Page.IsPostBack)
    {
        //Cargar codigo
    }
}

En el código anterior estamos indicando que el código sea en la segunda carga, ya que IsPostBack inicia en false.
Sin embargo, en un pagina todo el contenido se carga en la primera ejecución, por lo tanto, debemos hacer lo siguiente.


protected void Page_Load(object sender, EventArgs e)
{
    if (!Page.IsPostBack)
    {
        //Cargar codigo solo en la primera carga
    }
}
Con el símbolo (!) invertimos el valor booleano del postback, por lo tanto, si inicia en false se convierte en True.
En la primera ejecución se carga toda la página, en la segunda solo los datos de actualización.
De esta manera evitamos descargar todo el contenido de la página en cada acción en el formulario.
Haciendo que la pagina tenga un mejor rendimiento y evitando utilizar mucha memoria para guardar información.