---
title: Verwalten von Verweisen in einem Projekt
description: In diesem Artikel erfahren Sie, wie Sie Verweise in einem Projekt in Visual Studio für Mac verwalten können.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: a14630c5448632a939e1768040b910caf6276c2a
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692919"
---
# <a name="managing-references-in-a-project"></a>Verwalten von Verweisen in einem Projekt

Visual Studio für Mac bietet zwei Möglichkeit zum Hinzufügen von zusätzlichen Verweisen zu Ihrem Projekt:

![Projektverweise](media/projects-and-solutions-image10.png)

Diese lauten wie folgt:

* Verweise
* NuGets (hinzufügbar über den Ordner „Pakete“)

Darüber hinaus können zu jedem Projekt auch Webverweise und native Verweise hinzufügt werden.

## <a name="assembly-references"></a>Assemblyverweise

Jedes Framework innerhalb von Xamarin umfasst über ein Dutzend Assemblys. Nicht auf alle dieser Assemblypakete wird standardmäßig in Ihrem Projekt verwiesen.

Sie können über das Dialogfeld **Verweise bearbeiten** Pakete bearbeiten, auf die in Ihrem Projekt verwiesen wird. Das Dialogfeld kann durch Doppelklicken auf den Ordner „Verweise“ angezeigt werden oder indem Sie in den Kontextmenüaktionen auf **Verweise bearbeiten** klicken:

![Dialogfeld „Assemblyverweise“](media/projects-and-solutions-image11.png)

Weitere Informationen zu den Assemblys, die für jedes Xamarin-Framework verfügbar sind, finden Sie im Leitfaden für [Available Assemblies (verfügbare Assemblys)](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet ist der beliebteste Paket-Manager für die .NET-Entwicklung. Die NuGet-Unterstützung von Visual Studio für Mac ermöglicht Ihnen die Suche nach Paketen, die Sie Ihrem Projekt hinzufügen können.

Klicken Sie dazu mit der rechten Maustaste auf den Ordner **Pakete** im Projektmappenpad, und klicken Sie dann auf „Pakete hinzufügen“.

Weitere Informationen zur Verwendung eines NuGet-Pakets finden Sie in der exemplarischen Vorgehensweise [Including a NuGet package in your Project (Einfügen eines NuGet-Pakets in Ihr Projekt)](nuget-walkthrough.md).

## <a name="see-also"></a>Siehe auch

- [Verwalten von Verweisen (Visual Studio unter Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Hinzufügen von Verweisen mithilfe von NuGet im Vergleich zu einer SDK-Erweiterung (Visual Studio unter Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)