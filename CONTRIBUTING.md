---
ms.openlocfilehash: efd862261f2d1a6cce52214b56135d2c40f632c6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907447"
---
# <a name="contributing-to-the-project-rome-documentation"></a>Contribuir a la documentación de proyecto Roma

Le agradecemos su interés en nuestra documentación. Le agradecemos sus comentarios, las modificaciones, adiciones y ayuda para mejorar a nuestra documentación. Esta página tratan los pasos básicos y directrices de contribución.

## <a name="sign-a-cla"></a>Firmar un CLC

Si desea contribuir con más de un par de líneas y no es un empleado de Microsoft, deberá [firmar un contrato de licencia de colaboración (CLA) de Microsoft](https://cla.microsoft.com/). 

## <a name="propose-a-minor-change"></a>Proponer un cambio menor

Para sugerir un cambio sencillo a los documentos, siga estos pasos:

1. Si está viendo la página de Docs.microsoft.com, haga clic en el **editar** botón en la esquina superior derecha de la página.  Se le redirigirá al archivo de código fuente Markdown correspondiente en el [repositorio de GitHub](https://github.com/MicrosoftDocs/project-rome). Si ya están en el repositorio de GitHub, simplemente puede navegar al archivo de origen que desea cambiar.
2. Si aún no tiene una cuenta de GitHub, haga clic en **Sign Up** en la esquina superior derecha y crear una nueva cuenta.
3. En la página de GitHub que le gustaría cambiar, haga clic en el icono de lápiz. 
4. Modifique el archivo y use la ficha Vista previa para asegurarse de que los cambios aparezcan correctamente.
5. Cuando haya terminado, confirme los cambios y abra una solicitud de incorporación de cambios.

Después de crear la solicitud de incorporación de cambios, un miembro del equipo de Windows 10 docs la revisará. Si se aceptó la solicitud, las actualizaciones se publicarán en [ https://docs.microsoft.com/windows/project-rome/ ](https://docs.microsoft.com/windows/project-rome/).

## <a name="make-more-substantial-changes"></a>Realizar cambios más sustanciales

### <a name="fork-the-github-repo"></a>Bifurcar el repositorio de GitHub

Para realizar cambios sustanciales en un artículo existente, agregar o cambiar las imágenes o contribuir con un nuevo artículo, se recomienda realizar la bifurcación del repositorio en su cuenta de GitHub (haga clic en el botón "Bifurcación" en la esquina superior derecha de la [repositorio de GitHub](https://github.com/MicrosoftDocs/project-rome)y, a continuación, crear un clon local (haga clic en el verde **clonar o descargar** copia en el Portapapeles y luego en la línea de comandos de botón, escriba `git clone <paste your repo clone link>`).

Para obtener más información, consulte [bifurcar un repositorio](https://help.github.com/articles/fork-a-repo/).

Si no está familiarizado con el uso de Git, consulte el [entrenamiento Lynda.com Git Essentials](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html).

### <a name="author-your-contribution"></a>Crear su contribución

Una vez que ha bifurcado y clonado el repositorio en el equipo local, puede empezar a crear con el editor de texto que prefiera. Se recomienda [Visual Studio Code](https://code.visualstudio.com/), un editor ligero gratuito de código abierto de Microsoft.

### <a name="submit-your-contribution-by-issuing-a-pull-request-pr"></a>Enviar su colaboración mediante la emisión de una solicitud de incorporación de cambios (PR)

Una vez que haya guardado los cambios en el repositorio de git local, escriba los siguientes comandos en la línea de comandos para confirmar e insertarlas en el repositorio bifurcado local:
- `git status`: Este comando le mostrará qué archivos han cambiado para que pueda confirmar que desea realizar esos cambios. 
- `git add -A`: Este comando agrega todos los cambios en el índice del cambio. Si prefiere agregar solo los cambios realizados en un archivo determinado, escriba el comando: `git add <yourfile.md>`.
- `git commit -m "your commit message"`: Este comando indica a git para confirmar los cambios que agregó en el paso anterior, junto con un mensaje breve que describe los cambios realizados.
- `git push origin <yourbranchname>`: Este comando inserta los cambios en el repositorio remoto que ha realizado la bifurcación en GitHub (el "origen"), en la rama que haya especificado.

Después de insertar su contribución en el repositorio remoto, se le enviará un correo electrónico de *servicio de publicación abierta compilar* que le informa si su contribución se compila correctamente y que proporciona vínculos a los errores o advertencias en el repositorio, Por ejemplo, vínculos rotos. Haga clic en los vínculos en el informe para ver el contenido almacenado provisionalmente en el sitio. Cuando se borran los cambios de los errores y advertencias, estará listo para enviar un PR.
- Vaya a la bifurcación del repositorio de proyecto Roma: https://github.com/  **\<your-github-alias\>**/project-rome.
- Haga clic en el **nueva solicitud de incorporación de cambios** botón. La "bifurcación base:" se mostrará como "MicrosoftDocs/project-Roma" y la "bifurcación principal:" debe mostrar la bifurcación del repositorio y la rama en la que ha realizado los cambios. Puede revisar los cambios aquí también. 
- Haga clic en el **crear solicitud de incorporación de cambios** botón. A continuación, deberá dar su solicitud, un título y descripción. Por último, haga clic en el **crear solicitud de incorporación de cambios** botón una vez más.

Una vez que se envía su solicitud, un miembro del equipo de Windows 10 docs la revisará. Cuando los acepta, podrá ver los cambios en el [sitio de ensayo](https://review.docs.microsoft.com/windows/project-rome/). Estas actualizaciones, finalmente, se publicará en vivo en [ https://docs.microsoft.com/windows/project-rome/ ](https://docs.microsoft.com/windows/project-rome/).

## <a name="using-issues-to-provide-feedback-on-project-rome-documentation"></a>Uso de problemas para proporcionar comentarios sobre la documentación de proyecto Roma

Para proporcionar comentarios en lugar de modificar directamente las páginas de documentación, [cree un problema](https://github.com/MicrosoftDocs/project-rome/issues).

No olvide incluir el título del tema y la dirección URL de la página en cuestión.

## <a name="additional-resources"></a>Recursos adicionales
- [Cómo empezar a escribir y aplicar formato en GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Recursos adicionales para los empleados de Microsoft
- [Conecte su cuenta de GitHub y alias de MS](https://review.docs.microsoft.com/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Recursos para la escritura de Markdown](https://review.docs.microsoft.com/windows-authoring-guide/writing-guidance/writing-markdown)