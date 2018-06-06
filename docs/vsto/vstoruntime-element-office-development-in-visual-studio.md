---
title: '&lt;vstoRuntime&gt;要素 (Visual Studio での Office 開発)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d21e097c0a05dfba2aa15bc41e37441ae02a63e4
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768067"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt;要素 (Visual Studio での Office 開発)
  `vstoRuntime` 名前空間の `vstav3` 要素は、特定の Office ソリューション用の、Visual Studio Tools for Office ランタイムのサポートされるバージョンを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `vstoRuntime` 要素は必須です。この要素は `vstav3` 名前空間にあります。 Office ソリューションが 2 つのバージョンの Visual Studio Tools for Office ランタイムをサポートする場合、アプリケーション マニフェストには 2 つの `vstoRuntime` 要素があります。  
  
 `vstoRuntime` 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`release`|必須。 Visual Studio Tools for Office ランタイムのリリース バージョン。|  
|`version`|必須。 Visual Studio Tools for Office ランタイムのバージョン番号。|  
|`supportUrl`|任意。 Visual Studio Tools for Office ランタイムのインストール場所へのリンク。|  
  
 `vstoRuntime` には要素がありません。  
  
## <a name="example"></a>例  
 次のコード例は、 `vstoRuntime` を使用して配置する Office ソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例に示されている例の一部である[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
```xml  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  