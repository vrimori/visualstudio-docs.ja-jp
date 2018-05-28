---
title: '&lt;ドキュメント&gt;要素 (Visual Studio での Office 開発)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;ドキュメント&gt;要素 (Visual Studio での Office 開発)
  `document`の要素、`vstov4`名前空間は、ドキュメント レベルのカスタマイズのカスタマイズに固有の情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 ドキュメント レベルのカスタマイズでのみ必須です。 `document`要素は、`vstov4`名前空間。 `document`要素には、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`solutionId`|必須。 ドキュメント レベルのソリューションを一意に識別する、Visual Studio Tools for Office ランタイムで使用される GUID です。 この値は、_AssemblyLocation カスタム ドキュメント プロパティとして格納されます。 詳細については、次を参照してください。[カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)です。|  
  
 `document` 子要素がありません。  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズの例  
  
### <a name="description"></a>説明  
 次のコード例を示しています、`document`要素を使用して展開のドキュメント レベルの Office ソリューションで[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]です。 このコード例に示されている例の一部である[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
### <a name="code"></a>コード  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  