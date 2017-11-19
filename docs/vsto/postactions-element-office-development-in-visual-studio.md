---
title: "&lt;postActions&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 282a1bff821ee032d0d08038858c3a04fc7796ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt;要素 (Visual Studio での Office 開発)
  `postActions` 名前空間の `vstav3` の要素には、Office ソリューションのインストール後に実行する配置後アクションを説明する `postAction` 要素がすべて含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `postActions` 要素は省略可能であり、 `vstav3` 名前空間にあります。 アプリケーション マニフェストで定義される `postActions` 要素が 1 つだけあります。  
  
 `postActions` 要素に属性はありません。  
  
 `postActions` には次の要素があります。  
  
### <a name="postaction"></a>postAction  
 省略可能です。 役割、`postAction`内の要素、`vstav3`で名前空間が定義されている[&#60; postAction &#62;。要素 &#40; Visual Studio &#41; での Office 開発](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>配置後アクションの例  
  
### <a name="description"></a>説明  
 次のコード例では、 `postActions` を使用して展開した Office ソリューションのアプリケーション マニフェストにある [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:postActions>  
  <vstav3:postAction>  
    <vstav3:entryPoint   
      class="PostDeploymentAction.PostDeploymentActionSample">  
      <assemblyIdentity   
        name="PostDeploymentAction"   
        version="1.0.0.0"   
        language="neutral"   
        processorArchitecture="msil" />  
    </vstav3:entryPoint>  
    <vstav3:postActionData>  
    </vstav3:postActionData>  
  </vstav3:postAction>  
</vstav3:postActions>  
```  
  
## <a name="see-also"></a>関連項目  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  