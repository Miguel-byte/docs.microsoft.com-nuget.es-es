---
ms.openlocfilehash: 2fc62e7161a07d739760ed638653fbdec0dfc330
ms.sourcegitcommit: e763d9549cee3b6254ec2d6382baccb44433d42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68860571"
---
Use el comando [restore](../../reference/cli-reference/cli-ref-restore.md), que descarga e instala los paquetes que faltan en la carpeta *packages*.

En el caso de los proyectos migrados a PackageReference, use [msbuild-t:restore](../package-restore.md#restore-using-msbuild) para restaurar los paquetes en su lugar.

`restore` solo agrega paquetes en el disco, pero no cambia las dependencias de un proyecto. Para restaurar las dependencias del proyecto, modifique `packages.config` y use el comando `restore`.

Como con los otros comandos de la CLI de `nuget.exe`, primero abra una línea de comandos y cambie al directorio que contiene el archivo de proyecto.

Para restaurar un paquete con `restore`:

```cli
nuget restore MySolution.sln
```