---
title: Herunterladen der Satellitenassembly bei Bedarf mit der API für ClickOnce-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34cde3a2444525e48455e445894fd5ab1c66fab8
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262968"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung
Mit Windows Forms-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden. Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.

 Siehe [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md), können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben einschließen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.

 Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt. Im nachfolgend dargestellten Verfahren werden die im [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]verfügbaren Tools verwendet. Sie können diese Aufgabe auch in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ausführen.  Siehe auch [Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API, die mithilfe des Designers für die ClickOnce-Bereitstellung](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) oder [Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API, die mithilfe des Designers für die ClickOnce-Bereitstellung](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

> [!NOTE]
> In den folgenden Codebeispielen wird die Kultur zu Testzwecken programmgesteuert auf `ja-JP`festgelegt. Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.

## <a name="prerequisites"></a>Vorraussetzungen
 In diesem Thema wird davon ausgegangen, dass Sie wissen, wie der Anwendung mit Visual Studio lokalisierte Ressourcen hinzugefügt werden können. Ausführliche Anweisungen finden Sie unter [Exemplarische Vorgehensweise: Lokalisieren von Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>So laden Sie Satellitenassemblys bei Bedarf herunter

1. Fügen Sie den folgenden Code der Anwendung hinzu, um das bedarfsabhängige Herunterladen von Satellitenassemblys zu aktivieren.

    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]

2. Generieren von Satellitenassemblys für Ihre Anwendung mithilfe von [Resgen.exe (Resource File Generator)](/dotnet/framework/tools/resgen-exe-resource-file-generator) oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

3. Generieren Sie ein Anwendungsmanifest, oder öffnen Sie das vorhandene Anwendungsmanifest, indem Sie *MageUI.exe* verwenden. Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. Klicken Sie auf die Registerkarte **Dateien** .

5. Klicken Sie auf die Schaltfläche mit den **Auslassungszeichen** ( **...** ), und wählen Sie das Verzeichnis aus, das alle Assemblys und Dateien der Anwendung enthält, einschließlich der Satellitenassemblys, die Sie mit *Resgen.exe* generiert haben. (Der Name einer Satellitenassembly besitzt folgendes Format: *\<ISO-Code>\Anwendungsname.resources.dll*. Dabei entspricht \<ISO-Code> einer Sprachen-ID im Format RFC 1766.)

6. Klicken Sie auf **Auffüllen** , um die Dateien zu Ihrer Bereitstellung hinzuzufügen.

7. Aktivieren Sie für jede Satellitenassembly das Kontrollkästchen **Optional** .

8. Legen Sie für das Gruppenfeld jeder Satellitenassembly ihren ISO-Sprachenbezeichner fest. Für eine japanische Satellitenassembly würden Sie beispielsweise den Downloadgruppennamen `ja-JP`verfügbaren Tools verwendet. Damit kann der Code, den Sie in Schritt 1 hinzugefügt haben, je nach der Einstellung der <xref:System.Threading.Thread.CurrentUICulture%2A> -Benutzereigenschaft die entsprechende Satellitenassembly herunterladen.

## <a name="next-steps"></a>Nächste Schritte
 In einer Produktionsumgebung müssen Sie im Codebeispiel wahrscheinlich die Zeile entfernen, die für <xref:System.Threading.Thread.CurrentUICulture%2A> einen bestimmten Wert festlegt, denn auf Clientcomputern ist standardmäßig der richtige Wert festgelegt. Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP` . Diesen Wert programmgesteuert festzulegen bietet eine gute Möglichkeit zum Testen Ihrer Satellitenassemblys, bevor Sie Ihre Anwendung bereitstellen.

## <a name="see-also"></a>Siehe auch
- [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md)
