---
title: '&lt;カスタマイズ&gt;要素 (Visual Studio での Office 開発)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 798cb2e7a8526e97a3d97240e181ef2e35ed21b1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869084"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;カスタマイズ&gt;要素 (Visual Studio での Office 開発)
  `customization` 名前空間の `vstov4` 要素では、特定の Office ソリューションについて記述します。 ドキュメント レベルのカスタマイズと VSTO アドインでは、子要素が異なります。

## <a name="syntax-for-document-level-customizations"></a>ドキュメント レベルのカスタマイズの構文

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO アドインの構文

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>要素と属性
 `customization` 要素には、カスタマイズ固有の情報が含まれています。 この要素は、名前空間 `vstov4=urn:schemas-microsoft-com:vsto.v4`に存在する必要があります。 Office ソリューションごとに、 `customization` 要素が 1 つあります。 たとえば、複数プロジェクトの配置で 3 つの Office ソリューションを配置する場合は、アプリケーション マニフェストに 3 つの `customization` 要素を定義します。

 アセンブリの子要素が、この名前空間に存在する必要もあります。

 `customization` 要素には、次の属性があります。

|属性|説明|
|---------------|-----------------|
|`id`|複数プロジェクトの配置の場合は必須です。 `id` 要素によって、Office ソリューションを一意に識別します。|

### <a name="document-level-customizations"></a>ドキュメント レベルのカスタマイズ
 `customization` 要素には、次の子要素があります。

#### <a name="document"></a>ドキュメント
 `document`内の要素、`vstov4`で名前空間が定義されている[&#60;ドキュメント&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/document-element-office-development-in-visual-studio.md)します。

### <a name="vsto-add-ins"></a>VSTO アドイン
 `customization` 要素には、次の子要素があります。

#### <a name="appaddin"></a>appAddin
 `appAddin`内の要素、`vstov4`で名前空間が定義されている[ &#60;appAddin&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)します。

## <a name="example-of-a-document-level-customization"></a>ドキュメント レベルのカスタマイズの例

### <a name="description"></a>説明
 次のコード例は、ドキュメント レベルのカスタマイズの `customization` 要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO アドインの例

### <a name="description"></a>説明
 次のコード例を示しています、 `customization` VSTO アドインの要素。 この例は、フォーム領域が含まれた Outlook VSTO アドインです。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
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
```

## <a name="see-also"></a>関連項目

- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)