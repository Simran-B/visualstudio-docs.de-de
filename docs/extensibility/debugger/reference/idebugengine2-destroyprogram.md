---
title: IDebugEngine2::DestroyProgram | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c20459329eeb9e61447c707ef6c95adf01945e5d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330086"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informiert einer Debug-Engine (DE), die das angegebene Programm ungewöhnlich beendet wurde und die der DE sollten alle Verweise auf die Anwendung bereinigen, und Senden eines Programms zerstört Ereignis.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parameter
`pProgram`\
[in] Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, die ungewöhnlich beendet wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Nachdem diese Methode aufgerufen wird, sendet der DE anschließend ein [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) Ereignis an die sitzungsbasierter Debug-Manager (SDM).

 Diese Methode ist nicht implementiert (gibt `E_NOTIMPL`) Wenn die DE in demselben Prozess wie das derzeit debuggte Programm ausgeführt wird. Diese Methode wird implementiert, nur dann, wenn die DE in demselben Prozess wie das SDM ausgeführt wird.

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)