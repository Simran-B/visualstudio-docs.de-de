---
title: -Clean („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac184f25d79a47814fee52b99bce1cddce247fc5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570465"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Bereinigt alle Zwischendateien und Ausgabeverzeichnisse

## <a name="syntax"></a>Syntax

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Erforderlich. Der vollständige Pfad und Name der Projektmappendatei

- *Config*

  Dies ist optional. Die Konfiguration (z.B. `Debug` oder `Release`) zum Bereinigen der Zwischendateien für die in *SolutionName* benannte Projektmappe. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben (z.B. `Debug|Win32`). Wenn dieses Argument nicht angegeben wird oder eine leere Zeichenfolge (`""`) enthält, verwendet das Tool die aktive Konfiguration der Projektmappe.

- `/Project` *ProjName*

  Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können den Anzeigenamen des Projekts oder einen relativen Pfad vom *SolutionName*-Ordner zur Projektdatei eingeben. Sie können auch den vollständigen Pfad und Namen der Projektdatei eingeben.

- `/ProjectConfig` *ProjConfigName*

  Dies ist optional. Der Name der Buildkonfiguration des Projekts (z.B. `Debug` oder `Release`), die beim Bereinigen des benannten `/Project` verwenden wird. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben (z.B. `Debug|Win32`). Wenn dieser Schalter angegeben ist, überschreibt er das Argument *Config*.

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Hinweise

Dieser Schalter hat dieselbe Funktion wie der Menübefehl **Projektmappe bereinigen** in der IDE.

Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

Zusammenfassende Informationen beim Bereinigen und Erstellen, inklusive Fehlermeldungen, können im **Befehlsfenster** oder in einer Protokolldatei, die durch den [/Out](out-devenv-exe.md)-Schalter angegeben wird, angezeigt werden.

Wenn der Schalter `/Project` nicht angegeben ist, erfolgt die Bereinigungsaktion für alle Projekte in der Projektmappe, selbst wenn *FileName* als eine Projektdatei angegeben wurde.

## <a name="example"></a>Beispiel

Im ersten Beispiel wird die `MySolution`-Projektmappe mithilfe der in der Projektmappendatei angegebenen Standardkonfiguration bereinigt.

Im zweiten Beispiel wird das Projekt `CSharpWinApp` mithilfe der Projektbuildkonfiguration `Debug` in `MySolution` bereinigt.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
