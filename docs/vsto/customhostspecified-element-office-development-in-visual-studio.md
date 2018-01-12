---
title: "&lt;customHostSpecified&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 80007310f5556bcc8c67b61e7ff41953cc7c900e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt;要素 (Visual Studio での Office 開発)
  `customHostSpecified`要素は、このソリューションは、スタンドアロン アプリケーションではないことを示します。 Office ソリューションには、Microsoft Office アプリケーション内でホストされるコンポーネントが含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `customHostSpecified`要素は、Office ソリューションのために必要です。 この要素は、`co.v1`名前空間のカスタム ホスト内で展開されるコンポーネントがこの展開に含まれているを指定し、スタンドアロン アプリケーションではありません。  
  
 この要素は、最初の子`<entrypoint>`アプリケーション マニフェスト内の要素。 他の子要素にすることは`<entrypoint>`要素または[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]のインストール時に検証エラーが発生します。  
  
 この要素にはない属性や子要素です。  
  
## <a name="example"></a>例  
 次のコード例を示しています、 `customHostSpecified` Office ソリューションに対するアプリケーション マニフェストの要素。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>参照  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  