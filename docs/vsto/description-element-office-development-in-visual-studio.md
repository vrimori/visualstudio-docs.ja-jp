---
title: "&lt;説明&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2fdb8fb394ce2ccb7bb549df55ef1649b68d5cb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;説明&gt;要素 (Visual Studio での Office 開発)
  `description` 名前空間の `vstov4` 要素は、Microsoft Office アプリケーションの [COM アドイン] ダイアログ ボックスに表示される Office ソリューションの説明を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 任意。 `description` 要素は `vstov4` 名前空間に属します。 この要素は、Microsoft Office アプリケーションの [COM アドイン] ダイアログ ボックスに表示されるアドインの説明を格納します。  
  
 `description` 要素には、属性も要素もありません。  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>vstov4  
 次のコード例は、 `description` を使用して配置されるアプリケーションレベルのソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>参照  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  