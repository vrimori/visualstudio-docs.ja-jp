---
title: '&lt;entryPoint&gt;要素 (Visual Studio での Office 開発)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f28da1a564196833adff530c3c7d31eb9ea9bb4e
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648653"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint&gt;要素 (Visual Studio での Office 開発)
  `entryPoint` 名前空間の各 `vstav3` 要素によって、この [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] アプリケーションのインストール時に実行する必要のあるカスタマイズ アセンブリを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `entryPoint` 要素は必須です。この要素は `vstav3` 名前空間に属します。  
  
 `entryPoint` 要素ごとに、1 つのカスタマイズ アセンブリのみを含めることができます。 アプリケーション マニフェストには、複数の `entryPoint` 要素を定義できます。  
  
 `entryPoint` 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`class`|必須。 実行するカスタマイズ アセンブリを指定します。 この属性の構文は、 *NamespaceName.ClassName*です。|  
  
 `entryPoint` には、次の要素があります。  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 必須。 `assemblyIdentity` 名前空間の `vstav3` 要素は、 `assemblyIdentity` アプリケーション マニフェストで定義された既存の [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 要素を参照します。  
  
 ロール`assemblyIdentity`でその属性が定義されていると[ &#60;assemblyIdentity&#62;要素&#40;ClickOnce アプリケーション&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application)します。  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズ例  
  
### <a name="description"></a>説明  
 次のコード例は、 `entryPoint` を使用して配置するドキュメント レベルの Office ソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。  
  
### <a name="code"></a>コード  
  
```xml  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `entryPoint` を使用して配置するアプリケーション レベルの Office ソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。  
  
### <a name="code"></a>コード  
  
```xml
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  