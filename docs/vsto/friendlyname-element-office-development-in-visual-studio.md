---
title: '&lt;friendlyName&gt;要素 (Visual Studio での Office 開発)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 26842ab926ed7ef0ea2cfd62bf032c25b2c69d02
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt;要素 (Visual Studio での Office 開発)
  `friendlyName` 名前空間の `vstov4` 要素には、インストールしたプロフラムの一覧に表示される名前を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `friendlyName` 要素は、 `vstov4` 名前空間内にあります。 この値は、コンピューターにインストールされているプログラムの一覧と、Microsoft Office アプリケーションの COM VSTO アドイン ダイアログ ボックスに表示されます。  
  
 `friendlyName` 要素には、属性も子要素もありません。  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `friendlyName` を使用して配置されるアプリケーションレベルのソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例に示されている例の一部である[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
### <a name="code"></a>コード  
  
```xml  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  