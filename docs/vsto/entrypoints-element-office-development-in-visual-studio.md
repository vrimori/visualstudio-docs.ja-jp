---
title: "&lt;entryPoints&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <entryPoints> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: de60c2164bfbb0f7f8f483ab937fed23ecea9195
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;entryPoints&gt;要素 (Visual Studio での Office 開発)
  `entryPoints` 名前空間の `vstav3` の要素には、Office ソリューションに関連付けるすべての `entryPoint` 要素を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `entryPoints` 要素は必須です。この要素は `vstav3` 名前空間にあります。 アプリケーション マニフェストには、Office ソリューションごとに `entryPoints` 要素を 1 つ定義します。 たとえば、複数プロジェクトの配置で 3 つの Office ソリューションを配置する場合は、アプリケーション マニフェストに 3 つの `entryPoints` 要素を定義します。  
  
 `entryPoints` 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|ID|複数プロジェクトの配置の場合は必須です。 Office ソリューションの名前。 ID に等号 (=) は使用できません。|  
  
 `entryPoints` には、次の要素があります。  
  
### <a name="entrypoint"></a>entryPoint  
 必須。 役割、`entryPoint`内の要素、`vstav3`で名前空間が定義されている[&#60; entryPoint &#62;。要素 &#40; Visual Studio &#41; での Office 開発](../vsto/entrypoint-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `entryPoints` を使用して配置するドキュメント レベルのソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:entryPoints>  
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
</vstav3:entryPoints>  
```  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `entryPoints` を使用して配置するアプリケーション レベルのソリューションに対するアプリケーション マニフェストの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:entryPoints>  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="multi-project-deployment-example"></a>複数プロジェクトの配置の例  
  
### <a name="description"></a>説明  
 次のコード例は、複数プロジェクトの配置のためのアプリケーション マニフェストの `entryPoints` 要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:entryPoints   
  id="ContosoExcel">  
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
</vstav3:entryPoints>  
<vstav3:entryPoints   
  id="ContosoOutlook">  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="see-also"></a>参照  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  