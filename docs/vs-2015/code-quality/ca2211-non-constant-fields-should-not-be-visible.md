---
title: 'CA2211: nicht konstante Felder sollten nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: db2c667d0a3823460a084dc1e4806501d9b26693
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662956"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Nicht konstante Felder sollten nicht sichtbar sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentliches oder geschütztes statisches Feld ist nicht konstant und ist nicht schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
 Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Der Zugriff auf ein solches Feld muss sorgfältig gesteuert werden und erfordert erweiterte Programmierverfahren für die Synchronisierung des Zugriffs auf das Klassenobjekt. Da es schwierig ist, die Kenntnisse zu erlernen und zu meistern, und das Testen eines solchen Objekts seine eigenen Herausforderungen darstellt, werden statische Felder am besten zum Speichern von Daten verwendet, die sich nicht ändern. Diese Regel gilt für Bibliotheken. Anwendungen sollten keine Felder verfügbar machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie das statische Feld konstant oder schreibgeschützt. Wenn dies nicht möglich ist, sollten Sie den Typ so umgestalten, dass er einen alternativen Mechanismus verwendet, wie z. b. eine Thread sichere Eigenschaft, die den Thread sicheren Zugriff auf das zugrunde liegende Feld verwaltet. Beachten Sie, dass Probleme, wie z. b. Sperr Konflikte und Deadlocks, die Leistung und das Verhalten der Bibliothek beeinflussen können.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie eine Anwendung entwickeln und daher die vollständige Kontrolle über den Zugriff auf den Typ haben, der das statische Feld enthält. Bibliotheks-Designer sollten eine Warnung aus dieser Regel nicht unterdrücken. durch die Verwendung nicht konstanter statischer Felder kann die Verwendung der Bibliothek für Entwickler schwierig werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
