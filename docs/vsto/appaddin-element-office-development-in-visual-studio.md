---
title: '&lt;appAddin&gt;要素 (Visual Studio での Office 開発)'
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7f6caeafc95541cdc939220d76451c4cf5efdb0
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803034"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt;要素 (Visual Studio での Office 開発)
  **AppAddin**の要素、`vstov4`名前空間は、VSTO アドインのカスタマイズに固有の情報を格納します。

## <a name="syntax"></a>構文

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>要素と属性
 **AppAddin**要素が必要であり、`vstov4`名前空間。 1 つしかない**appAddin**アプリケーション マニフェストで定義された要素。

 **AppAddin**要素には、次の属性。

|属性|説明|
|---------------|-----------------|
|**アプリケーション**|必須。 Microsoft Office アプリケーションを指定します。 値は次のいずれかになります。Excel、InfoPath、Outlook、PowerPoint、Project、Visio、または Word。|
|**LoadBehavior**|任意。 既定で、 **loadBehavior**はこの値を設定で有効にします。 デバッグする場合は、この値を 2 に設定して VSTO アドインを無効にできます。 詳細については、LoadBehavior の値」というタイトルの表を参照してください。 [VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)します。|
|**キー名**|必須。 この値は、アプリケーションが VSTO アドインを読み込むのに使用するレジストリ キーの名前です。 詳細については、次を参照してください。 [VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)します。|

 **AppAddin**要素には、次の子要素。

### <a name="friendlyname"></a>friendlyName
 任意。 **FriendlyName**要素については[ &#60;friendlyName&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)します。

### <a name="description"></a>説明
 任意。 **説明**要素については[&#60;説明&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/description-element-office-development-in-visual-studio.md)します。

### <a name="formregions"></a>formRegions
 フォーム領域を含む Outlook VSTO アドインにのみ必須です。 **FormRegions**要素については[ &#60;formRegions&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)します。

## <a name="vsto-add-in-example"></a>VSTO アドインの例

### <a name="description"></a>説明
 次のコード例を示しています**appAddin**要素を使用して配置される Outlook ソリューション[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]します。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
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
```

## <a name="see-also"></a>関連項目

- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)