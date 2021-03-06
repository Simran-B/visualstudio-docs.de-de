---
title: '&lt;Signatur&gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db696546fdd64199753054b38fa2ac554f6a774f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295074"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signatur&gt; Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält die notwendigen Informationen, um dieses Bereitstellungsmanifest digital zu signieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Signieren eines Bereitstellungs Manifests mithilfe einer Umschlag Signatur ist optional, wird jedoch empfohlen. Weitere Informationen zum Signieren von XML-Dateien finden Sie in der World Wide Web Consortium Empfehlung "Syntax und Verarbeitung von XML-Signaturen", die unter [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/)beschrieben wird.  
  
 Wenn Sie das Manifest signieren möchten, müssen Sie Hashes für alle Dateien bereitstellen. Ein Manifest mit Dateien, die nicht als Hash verwendet werden, kann nicht signiert werden, da Benutzer den Inhalt von Dateien ohne Hash überprüfen können.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht ein `Signature`-Element in einem Bereitstellungs Manifest, das in einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Bereitstellung verwendet wird.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
