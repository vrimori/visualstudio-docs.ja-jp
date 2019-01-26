---
title: '&lt;customHostSpecified&gt;要素 (Visual Studio での Office 開発)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26597796c99d3ab8740812819cf3aa5568e2985b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874381"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt;要素 (Visual Studio での Office 開発)
  `customHostSpecified`要素は、このソリューションは、スタンドアロン アプリケーションではないことを示します。 Office ソリューションには、Microsoft Office アプリケーション内でホストされているコンポーネントが含まれます。

## <a name="syntax"></a>構文

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>要素と属性
 `customHostSpecified`要素は Office ソリューションの必須です。 この要素は、`co.v1`名前空間にこの展開にカスタム ホストの内部で展開されるコンポーネントが格納されているし、スタンドアロン アプリケーションではありません。

 この要素は、最初の子`<entrypoint>`アプリケーション マニフェスト内の要素。 必要がありますには、他の子要素`<entrypoint>`要素または[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]のインストール時に検証エラーが発生します。

 この要素は、属性や子要素があります。

## <a name="example"></a>例
 次のコード例を示しています、 `customHostSpecified` Office ソリューションに対するアプリケーション マニフェスト内の要素。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>関連項目

- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)