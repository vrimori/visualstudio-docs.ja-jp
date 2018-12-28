---
title: '&lt;ドキュメント&gt;要素 (Visual Studio での Office 開発)'
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
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: ac66f4f7dd458ecba5f26cc99ad795540dba648d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802473"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;ドキュメント&gt;要素 (Visual Studio での Office 開発)
  `document`の要素、`vstov4`名前空間は、ドキュメント レベルのカスタマイズのカスタマイズに固有の情報を格納します。

## <a name="syntax"></a>構文

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>要素と属性
 ドキュメント レベルのカスタマイズでのみ必須です。 `document` 要素は、 `vstov4` 名前空間内にあります。 `document` 要素には、次の属性があります。

|属性|説明|
|---------------|-----------------|
|`solutionId`|必須。 ドキュメント レベルのソリューションを一意に識別する、Visual Studio Tools for Office ランタイムによって使用される GUID です。 この値は、カスタムのドキュメントの _AssemblyLocation プロパティとして格納されます。 詳細については、次を参照してください。[カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)します。|

 `document` に子要素はありません。

## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズ例

### <a name="description"></a>説明
 次のコード例を示しています、`document`要素を使用して配置されるドキュメント レベルの Office ソリューション[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]します。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>関連項目

- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)