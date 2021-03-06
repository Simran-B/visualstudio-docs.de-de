---
title: 'CA2118: Überprüfen der Verwendung von SuppressUnmanagedCodeSecurityAttribute | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb7404d9add159f182ae44b22444dded1aafca20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658638"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Überprüfen der Verwendung von SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ oder Member verfügt über das <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>-Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code mit COM-Interop oder Platt Form Aufruf ausführen. Im Allgemeinen erstellt das System eine [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) für nicht verwalteten Code. Diese Anforderung tritt zur Laufzeit für jeden Aufruf des Members auf und überprüft jeden Aufrufer in der Aufruf Listen-Berechtigung. Wenn das-Attribut vorhanden ist, führt das System einen [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) für die Berechtigung aus: die Berechtigungen des unmittelbaren Aufrufers werden bei der JIT-Kompilierung des Aufrufers geprüft.

 Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher. Wenn Sie das-Attribut in öffentlichen Membern platzieren, die Native Methoden aufzurufen, benötigen die Aufrufer in der Aufruf Listen-Datei (mit Ausnahme des unmittelbaren Aufrufers) keine Berechtigung für nicht verwalteten Code, um nicht verwalteten Code auszuführen. Abhängig von den Aktionen des öffentlichen Members und der Eingabe Behandlung können nicht vertrauenswürdige Aufrufer auf Funktionen zugreifen, die normalerweise auf vertrauenswürdigen Code beschränkt sind.

 Der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] stützt sich auf Sicherheitsüberprüfungen, um zu verhindern, dass Aufrufer direkt auf den Adressraum des aktuellen Prozesses zugreifen können. Da dieses Attribut die normale Sicherheit umgeht, stellt der Code eine ernsthafte Bedrohung dar, wenn er verwendet werden kann, um den Arbeitsspeicher des Prozesses zu lesen oder zu schreiben. Beachten Sie, dass das Risiko nicht auf Methoden beschränkt ist, die absichtlich Zugriff auf den Prozess Speicher bereitstellen. Es ist auch in jedem Szenario vorhanden, in dem bösartiger Code auf beliebige Weise Zugriff erhalten kann, z. b. durch die Bereitstellung von überraschenden, falsch formatierten oder ungültigen Eingaben.

 Die Standard Sicherheitsrichtlinie gewährt einer Assembly keine Berechtigung für den nicht verwalteten Code, es sei denn, Sie wird auf dem lokalen Computer ausgeführt oder ist Mitglied einer der folgenden Gruppen:

- Arbeitsplatz Zonen-Code Gruppe

- Microsoft-Code Gruppe mit starkem Namen

- ECMA-Code Gruppe mit starkem Namen

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie sorgfältig den Code, um sicherzustellen, dass dieses Attribut unbedingt erforderlich ist. Wenn Sie mit der Sicherheit von verwaltetem Code nicht vertraut sind oder die Auswirkungen der Verwendung dieses Attributs auf die Sicherheit nicht verstehen, entfernen Sie Sie aus dem Code. Wenn das Attribut erforderlich ist, müssen Sie sicherstellen, dass der Code von Aufrufern nicht bösartig verwendet werden kann. Wenn der Code nicht über die Berechtigung zum Ausführen von nicht verwaltetem Code verfügt, hat dieses Attribut keine Auswirkung und sollte entfernt werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass der Code den Aufrufern keinen Zugriff auf systemeigene Vorgänge oder Ressourcen bereitstellt, die auf zerstörerische Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gegen die Regel verstoßen.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel stellt die `DoWork`-Methode einen öffentlich zugänglichen Codepfad zur Platt Form Aufruf Methode `FormatHardDisk` bereit.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel verursacht die öffentliche Methode `DoDangerousThing` eine Verletzung. Zum Beheben des Verstoßes sollten `DoDangerousThing` als privat festgestellt werden, und der Zugriff darauf sollte über eine öffentliche Methode erfolgen, die durch eine Sicherheitsanforderung gesichert ist, wie in der `DoWork`-Methode veranschaulicht.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Sicherheits Optimierungen](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [und Modellierungs](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) Aufrufe
