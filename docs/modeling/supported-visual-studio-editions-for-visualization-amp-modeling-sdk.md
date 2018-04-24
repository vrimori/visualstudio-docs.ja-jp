---
title: 視覚エフェクトに対してサポートされている Visual Studio エディション&amp;モデリング SDK
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4ec6528176b02684a4235be29f4387da26193810
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>視覚エフェクトに対してサポートされている Visual Studio エディション&amp;モデリング SDK
サポートされている Visual Studio のエディションの一覧は、次のとおり[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]オーサリングとデプロイ環境でします。 これらのエディションの詳細については、Microsoft を参照してください。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=75628)です。

## <a name="authoring-edition"></a>作成エディション
 DSL を定義するには、以下のコンポーネントをインストールしておく必要があります。

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>配置エディション
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] では、作成したドメイン固有言語を配置するために、以下の構成がサポートされています。

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Visual Studio Shell (integrated mode) 再頒布可能パッケージの再頒布可能パッケージ

-   Visual Studio Shell (分離モード) 再頒布可能パッケージ

> [!NOTE]
>  DSL シェル製品を実行することをするためには、設定する必要があります、 **VS エディションのサポートされている**拡張機能マニフェスト内のフィールドです。 詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)です。

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
