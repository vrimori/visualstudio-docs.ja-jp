---
title: "&lt;postActionData&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ea65f8789e3106abe8da46ae0302cdf0f4f47ef7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt;要素 (Visual Studio での Office 開発)
  `postActionData` 名前空間の `vstav3` 要素は、Office ソリューションをインストールした後に実行されるすべての配置後アクションに関連付けられているデータを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `postActionData` 要素は省略可能であり、 `vstav3` 名前空間にあります。 アプリケーション マニフェストには、配置後アクションごとに `postActionData` 要素を 1 つ定義します。  
  
 `postActions` 要素には属性がありません。  
  
 `postActions` に子要素はありません。  
  
## <a name="post-deployment-action-example"></a>配置後アクションの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `postAction` を使用して配置する Office ソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>参照  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  