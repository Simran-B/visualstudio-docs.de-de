---
title: Ermitteln, ob meine Zeiger eine Speicheradresse beschädigen | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc178675e6d2423336c38e69691f081bf4b447a4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916173"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Wie wird festgestellt, ob Zeiger eine Speicheradresse zerstören?
## <a name="problem-description"></a>Problembeschreibung
 Vermutlich wird der Speicher an der Adresse 0x00408000 von einem Zeiger des Programms zerstört. Wie kann festgestellt werden, was dort geschieht?

## <a name="solution"></a>Lösung

#### <a name="check-for-heap-corruption"></a>Überprüfen des Heaps auf Beschädigungen

- Ein Speicherschaden ist eigentlich die Folge einer Heapbeschädigung. Verwenden Sie in diesem Fall das Global Flags-Dienstprogramm (gflags.exe) oder "pageheap.exe". Siehe [/Windows-Hardware/Drivers/Debugger/Gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>So finden Sie die geänderte Stelle der Speicheradresse

1. Legen Sie einen Datenhaltepunkt bei 0x00408000 fest. Weitere Informationen finden Sie unter [Set a data change breakpoint (native C++ only) (Festlegen eines Haltepunkts für Datenänderungen (nur nativer C++-Code))](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Zeigen Sie den Speicherinhalt bei Erreichen eines Haltepunkts im Fenster **Speicher** ab Adresse 0x00408000 an. Weitere Informationen finden Sie unter Arbeits [Speicherfenster](../debugger/memory-windows.md).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
