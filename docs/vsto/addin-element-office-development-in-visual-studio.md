---
title: "&lt;addin&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b362894449670a7c672d36fa5b7421a9efb0976b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;addin&gt;要素 (Visual Studio での Office 開発)
  名前空間 `addin` の `vstav3` 要素には、Visual Studio で開発した Microsoft Office VSTO アドインとドキュメント レベルのカスタマイズに関する情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 名前空間 `addin` の `vstav3` 要素には、Office ソリューションと Microsoft Office アプリケーションに関する情報を格納します。 この要素は、名前空間 `vstav3=urn:schemas-microsoft-com:vsta.v3`に存在する必要があります。 子要素もこの名前空間に存在する必要があります。  
  
 `addin` 要素に属性はありません。  
  
 `addin` 要素には、次の子要素があります。  
  
### <a name="entrypoints"></a>entryPoints  
 必須。 `entryPoints`要素については、「 [&#60; entryPoints &#62;。要素 &#40; Visual Studio &#41; での Office 開発](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="update"></a>更新  
 必須。 `update`要素については、「 [&#60;以外の場合は更新 &#62;。要素 &#40; Visual Studio &#41; での Office 開発](../vsto/update-element-office-development-in-visual-studio.md).  
  
### <a name="postactions"></a>postActions  
 任意。 `postActions`要素については、「 [&#60; postActions &#62;。要素 &#40; Visual Studio &#41; での Office 開発](../vsto/postactions-element-office-development-in-visual-studio.md).  
  
### <a name="application"></a>アプリケーション  
 必須。 `application`要素については、「 [&#60; アプリケーション &#62;。要素 &#40; Visual Studio &#41; での Office 開発](../vsto/application-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `addin` を使用して配置するドキュメント レベルの Office ソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:addIn   
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">  
  <vstav3:entryPointsCollection>  
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
  </vstav3:entryPointsCollection>  
  <vstav3:update   
    enabled="true">  
    <vstav3:expiration   
      maximumAge="7"   
      unit="days" />  
  </vstav3:update>  
  <vstav3:application>  
    <vstov4:customizations   
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
      <vstov4:customization>  
        <vstov4:document   
          solutionId="73e" />  
      </vstov4:customization>  
    </vstov4:customizations>  
  </vstav3:application>  
</vstav3:addIn>  
```  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>説明  
 次のコード例は、 `addin` を使用して配置するアプリケーション レベルの Office ソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:addIn   
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">  
  <vstav3:entryPointsCollection>  
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
  </vstav3:entryPointsCollection>  
  <vstav3:update   
    enabled="true">  
    <vstav3:expiration   
      maximumAge="7"   
      unit="days" />  
  </vstav3:update>  
  <vstav3:application>  
    <vstov4:customizations   
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
      <vstov4:customization>  
        <vstov4:appAddIn   
          application="Outlook"   
          loadBehavior="3"   
          keyName="ContosoOutlookAddIn">  
          <vstov4:friendlyName>  
            ContosoOutlookAddIn  
          </vstov4:friendlyName>  
          <vstov4:description>  
            ContosoOutlookAddIn - Outlook VSTO Add-in   
            created with Visual Studio Tools for Office  
          </vstov4:description>  
          <vstov4:formRegions>  
            <vstov4:formRegion  
                name="OutlookAddIn1.FormRegion1">  
              <vstov4:messageClass name="IPM.Note" />  
              <vstov4:messageClass name="IPM.Contact" />  
              <vstov4:messageClass name="IPM.Appointment" />  
            </vstov4:formRegion>  
          </vstov4:formRegions>  
        </vstov4:appAddIn>  
      </vstov4:customization>  
    </vstov4:customizations>  
  </vstav3:application>  
</vstav3:addIn>  
```  
  
## <a name="see-also"></a>参照  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  