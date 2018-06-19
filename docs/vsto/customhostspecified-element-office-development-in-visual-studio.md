---
title: '&lt;customHostSpecified&gt;要素 (Visual Studio での Office 開発)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4eaf874a259251c35a6b01c08f544993092ff4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264036"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt;要素 (Visual Studio での Office 開発)
  `customHostSpecified`要素は、このソリューションは、スタンドアロン アプリケーションではないことを示します。 Office ソリューションには、Microsoft Office アプリケーション内でホストされるコンポーネントが含まれます。  
  
## <a name="syntax"></a>構文  
  
```xml
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `customHostSpecified`要素は、Office ソリューションのために必要です。 この要素は、`co.v1`名前空間のカスタム ホスト内で展開されるコンポーネントがこの展開に含まれているを指定し、スタンドアロン アプリケーションではありません。  
  
 この要素は、最初の子`<entrypoint>`アプリケーション マニフェスト内の要素。 他の子要素にすることは`<entrypoint>`要素または[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]のインストール時に検証エラーが発生します。  
  
 この要素にはない属性や子要素です。  
  
## <a name="example"></a>例  
 次のコード例を示しています、 `customHostSpecified` Office ソリューションに対するアプリケーション マニフェストの要素。 このコード例に示されている例の一部である[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
```xml
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  