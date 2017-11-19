---
title: "&lt;ドキュメント&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48995b4a40d4e67b0c0e2e44d66545c4c90dd26b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;ドキュメント&gt;要素 (Visual Studio での Office 開発)
  `document`の要素、`vstov4`名前空間は、ドキュメント レベルのカスタマイズのカスタマイズに固有の情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 ドキュメント レベルのカスタマイズでのみ必須です。 `document`要素は、`vstov4`名前空間。 `document`要素には、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`solutionId`|必須です。 ドキュメント レベルのソリューションを一意に識別する、Visual Studio Tools for Office ランタイムで使用される GUID です。 この値は、_AssemblyLocation カスタム ドキュメント プロパティとして格納されます。 詳細については、「 [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md)」を参照してください。|  
  
 `document`子要素がありません。  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズの例  
  
### <a name="description"></a>説明  
 次のコード例を示しています、`document`要素を使用して展開のドキュメント レベルの Office ソリューションで[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]です。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>関連項目  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  