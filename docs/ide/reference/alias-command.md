---
title: Befehl "Alias"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 031f1a4bab1acee3f3d0999b17c0b607f7808df9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596904"
---
# <a name="alias-command"></a>Befehl "Alias"
Erstellt einen neuen Alias für einen vollständigen Befehl, einen vollständigen Befehl und seine Argumente oder für einen anderen Alias.

> [!TIP]
> Bei Eingabe von `>alias` ohne Argumente wird die aktuelle Liste der Aliase mit den jeweiligen Definitionen angezeigt.

## <a name="syntax"></a>Syntax

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumente
`aliasname`\
Dies ist optional. Der Name für den neuen Alias. Wenn für `aliasname` kein Wert angegeben wird, wird eine Liste der aktuellen Aliase und ihrer Definitionen angezeigt.

`aliasstring`\
Dies ist optional. Der vollständige Befehlsname oder der Name des vorhandenen Alias sowie alle Parameter, für die Sie einen Alias erstellen möchten. Wenn für `aliasstring` kein Wert angegeben wird, werden der Aliasname und die Aliaszeichenfolge für den angegebenen Alias angezeigt.

## <a name="switches"></a>Schalter
/delete oder /del oder /d\
Dies ist optional. Löscht den angegebenen Alias und entfernt ihn aus der automatischen Vervollständigung.

/reset\
Dies ist optional. Setzt die Liste der vordefinierten Aliase auf die ursprünglichen Einstellungen zurück. Das bedeutet, dass alle vordefinierten Aliase wiederhergestellt und alle benutzerdefinierten Aliase entfernt werden.

## <a name="remarks"></a>Hinweise
Da Aliase Befehle darstellen, müssen sie sich am Anfang der Befehlszeile befinden.

Wenn Sie diesen Befehl geben, sollten Sie die Schalter unmittelbar nach dem Befehl hinzufügen und nicht erst nach den Aliasen, da der Schalter andernfalls als Teil der Aliaszeichenfolge einbezogen wird.

Vor der Wiederherstellung der Aliase werden Sie vom `/reset`-Schalter aufgefordert, den Vorgang zu bestätigen. Es gibt keine Kurzform für `/reset`.

## <a name="examples"></a>Beispiele
In diesem Beispiel wird der neue Alias `upper` für den vollständigen Befehl "Edit.MakeUpperCase" erstellt.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

In diesem Beispiel wird der Alias `upper` gelöscht.

```cmd
>Tools.alias /delete upper
```

In diesem Beispiel wird eine Liste aller aktuellen Aliase und Definitionen angezeigt.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
