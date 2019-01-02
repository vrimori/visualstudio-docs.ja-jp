---
title: '&lt;entryPointsCollection&gt;要素 (Visual Studio での Office 開発)'
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
- <entryPointsCollection> element
- application manifests [Office development in Visual Studio], <entryPointsCollection> element
- entryPointsCollection element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 473168bea81b28de70b46baab6c3a1c7f3f0ea2e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803698"
---
# <a name="ltentrypointscollectiongt-element-office-development-in-visual-studio"></a>&lt;entryPointsCollection&gt;要素 (Visual Studio での Office 開発)
  `entryPointsCollection` 名前空間の `vstav3` 要素は、Office ソリューションに関連付けられているすべての `entryPoints` 要素を格納します。

## <a name="syntax"></a>構文

```xml
<entryPointsCollection>
  <entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
  </entryPoints>
</entryPointsCollection>
```

## <a name="elements-and-attributes"></a>要素と属性
 `entryPointsCollection` 要素は必須です。この要素は `vstav3` 名前空間に属します。 子要素もこの名前空間に属している必要があります。 アプリケーション マニフェストで定義される `entryPointsCollection` 要素が 1 つだけあります。

 `entryPointsCollection` 要素に属性はありません。

 `entryPointsCollection` には、次の要素があります。

### <a name="entrypoints"></a>entryPoints
 必須。 ロール、`entryPoints`内の要素、`vstav3`で名前空間が定義されている[ &#60;entryPoints&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)します。

## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズ例

### <a name="description"></a>説明
 次のコード例では、 `entryPointsCollection` を使用して配置したドキュメント レベルのソリューションのアプリケーション マニフェストにある [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
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
```

## <a name="vsto-add-in-example"></a>VSTO アドインの例

### <a name="description"></a>説明
 次のコード例では、 `entryPointsCollection` を使用して配置したアプリケーション レベルのソリューションのアプリケーション マニフェストにある [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
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
```

## <a name="multi-project-deployment-example"></a>複数プロジェクトの配置例

### <a name="description"></a>説明
 次のコード例では、2 つの Office ソリューションを使用した複数プロジェクトの配置でのアプリケーション マニフェストにある `entryPointsCollection` 要素を示しています。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
<vstav3:entryPointsCollection>
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
    </vstav3:entryPointsCollection>
```

## <a name="see-also"></a>関連項目

- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)