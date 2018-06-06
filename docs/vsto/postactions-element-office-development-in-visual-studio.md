---
title: '&lt;postActions&gt;要素 (Visual Studio での Office 開発)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6542344d5e0967504eccbedd4986cd80ef04f40a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692575"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt;要素 (Visual Studio での Office 開発)
  `postActions` 名前空間の `vstav3` の要素には、Office ソリューションのインストール後に実行する配置後アクションを説明する `postAction` 要素がすべて含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
 `postActions` 要素には属性がありません。  
  
 `postActions` には次の要素があります。  
  
### <a name="postaction"></a>postAction  
 任意。 役割、`postAction`内の要素、`vstav3`で名前空間が定義されている[ &#60;postAction&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)です。  
  
## <a name="post-deployment-action-example"></a>配置後アクションの例  
  
### <a name="description"></a>説明  
 次のコード例では、 `postActions` を使用して展開した Office ソリューションのアプリケーション マニフェストにある [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例に示されている例の一部である[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
### <a name="code"></a>コード  
  
```xml  
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
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  