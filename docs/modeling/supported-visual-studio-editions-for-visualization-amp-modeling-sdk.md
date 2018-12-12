---
title: Visualization and Modeling SDK for Visual Studio のエディションがサポートされています
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 65014d8c697adbf5fb8e13d28708090360bb9c17
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049957"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Visualization and Modeling SDK に対してサポートされている Visual Studio のエディション

サポートされている Visual Studio のエディションの一覧を以下に[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]オーサリングとデプロイ環境にします。 これらのエディションの詳細については、Microsoft Visual Studio を参照してください。[デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=75628)します。

## <a name="authoring-edition"></a>作成エディション

DSL を定義するには、以下のコンポーネントをインストールしておく必要があります。

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>配置エディション

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] では、作成したドメイン固有言語を配置するために、以下の構成がサポートされています。

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Visual Studio Shell (統合モード) 再頒布可能パッケージの再頒布可能パッケージ

-   Visual Studio Shell (分離モード) 再頒布可能パッケージ

> [!NOTE]
> DSL を Shell 製品上で実行可能にするには、設定する必要があります、**サポートされている VS エディション**フィールドに、拡張機能マニフェストします。 詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)します。

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)