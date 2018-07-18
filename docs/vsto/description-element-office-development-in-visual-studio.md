---
title: '&lt;説明&gt;要素 (Visual Studio での Office 開発)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9fcdac1e950d98394b5703322f40dd1823b246f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265116"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;説明&gt;要素 (Visual Studio での Office 開発)
  `description` 名前空間の `vstov4` 要素は、Microsoft Office アプリケーションの [COM アドイン] ダイアログ ボックスに表示される Office ソリューションの説明を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 任意。 `description` 要素は `vstov4` 名前空間に属します。 この要素は、Microsoft Office アプリケーションの [COM アドイン] ダイアログ ボックスに表示されるアドインの説明を格納します。  
  
 `description` 要素には、属性も要素もありません。  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `description` を使用して配置されるアプリケーションレベルのソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例に示されている例の一部である[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
### <a name="code"></a>コード  
  
```xml  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  