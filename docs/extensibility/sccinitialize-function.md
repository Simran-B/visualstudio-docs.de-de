---
title: Sccinitialize-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 552ec06a4eabf55872358fc8e5d731e47c1eb6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721182"
---
# <a name="sccinitialize-function"></a>SccInitialize-Funktion
Diese Funktion initialisiert das Quellcodeverwaltungs-Plug-in und bietet Funktionen und Einschränkungen für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE).

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parameter
 `ppvContext`

in Das Quellcodeverwaltungs-Plug-in kann hier einen Zeiger auf seine Kontext Struktur platzieren.

 `hWnd`

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 `lpCallerName`

in Der Name des Programms, das das Quellcodeverwaltungs-Plug-in aufrufen.

 `lpSccName`

[in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-in seinen eigenen Namen einfügt (nicht überschreiten `SCC_NAME_LEN`).

 `lpSccCaps`

vorgenommen Gibt die funktionsflags für das Quellcodeverwaltungs-Plug-in zurück.

 `lpAuxPathLabel`

[in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-in eine Zeichenfolge einfügt, die den `lpAuxProjPath` Parameter beschreibt, der von [sccopenproject](../extensibility/sccopenproject-function.md) und [sccgetprojpath](../extensibility/sccgetprojpath-function.md) zurückgegeben wird (nicht überschreiten `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

vorgenommen Gibt die maximal zulässige Länge für einen Auscheck Kommentar zurück.

 `pnCommentLen`

vorgenommen Gibt die maximal zulässige Länge für andere Kommentare zurück.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Initialisierung der Quell Code Verwaltung war erfolgreich.|
|SCC_E_INITIALIZEFAILED|Das System konnte nicht initialisiert werden.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf den angegebenen Vorgang nicht ausführen.|
|SCC_E_NONSPECFICERROR|Nicht spezifischer Fehler. das Quell Code Verwaltungssystem wurde nicht initialisiert.|

## <a name="remarks"></a>Hinweise
 Die IDE ruft diese Funktion auf, wenn das Quellcodeverwaltungs-Plug-in zum ersten Mal geladen wird. Sie ermöglicht der IDE, bestimmte Informationen, wie z. b. den Namen des Aufrufers, an das Plug-in zu übergeben. Die IDE erhält auch bestimmte Informationen, wie z. b. die maximal zulässige Länge für Kommentare und die Funktionen des Plug-ins.

 Der `ppvContext` verweist auf einen `NULL` Zeiger. Das Quellcodeverwaltungs-Plug-in kann eine Struktur für die eigene Verwendung zuordnen und einen Zeiger auf diese Struktur in `ppvContext` speichern. Die IDE übergibt diesen Zeiger an jede andere vssci-API-Funktion und ermöglicht dem Plug-in, Kontextinformationen zur Verfügung zu stellen, ohne auf den globalen Speicher zurückzugreifen und mehrere Instanzen des Plug-ins zu unterstützen. Die Zuordnung dieser Struktur sollte aufgehoben werden, wenn [sccuninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.

 Die Parameter `lpCallerName` und `lpSccName` ermöglichen der IDE und dem Quellcodeverwaltungs-Plug-in das Austauschen von Namen. Diese Namen können einfach zur Unterscheidung zwischen mehreren Instanzen verwendet werden, oder Sie werden möglicherweise in Menüs oder Dialogfeldern angezeigt.

 Der `lpAuxPathLabel`-Parameter ist eine Zeichenfolge, die als Kommentar verwendet wird, um den zusätzlichen Projektpfad zu identifizieren, der in der Projektmappendatei gespeichert und in einem Aufrufen von [sccopenproject](../extensibility/sccopenproject-function.md)an das Quellcodeverwaltungs-Plug-in übergeben wird. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] verwendet die Zeichenfolge "SourceSafe Project:"; andere Quellcodeverwaltungs-Plug-ins sollten diese Zeichenfolge nicht verwenden.

 Der `lpSccCaps`-Parameter gibt dem Quellcodeverwaltungs-Plug-in einen Speicherort zum Speichern von Bitflags, die die Funktionen des Plug-ins angeben. (Eine vollständige Liste der funktionsbitflags finden Sie unter [funktionsflags](../extensibility/capability-flags.md)). Wenn das Plug-in beispielsweise Ergebnisse in eine vom Aufrufer bereitgestellte Rückruffunktion schreiben soll, legt das Plug-in das Capability Bit SCC_CAP_TEXTOUT fest. Dadurch wird der IDE signalisiert, ein Fenster für Ergebnisse der Versionskontrolle zu erstellen.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Funktionsflags](../extensibility/capability-flags.md)