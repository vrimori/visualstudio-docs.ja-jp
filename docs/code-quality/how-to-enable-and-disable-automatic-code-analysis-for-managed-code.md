---
title: 有効にするか、コード分析を無効にします。
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1620999385eec0862b4ba2aceadba10bb21d239d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905599"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>方法: 有効にして、マネージ コードの自動コード分析を無効にします。

マネージ コード プロジェクトのビルドのたびに実行する (静的) のコード分析を構成することができます。 別のコードに各ビルド構成に対して分析プロパティを設定などのデバッグおよびリリースします。

この記事はのみに静的コード分析といないライブ コード分析を使用して適用されます[Roslyn コード アナライザー](roslyn-analyzers-overview.md)します。

## <a name="to-enable-or-disable-automatic-code-analysis"></a>自動コード分析を有効または無効にするには

1. **ソリューション エクスプ ローラー** で、プロジェクトを右クリックし、**プロパティ**を選択します。

1. プロジェクトのプロパティ ダイアログ ボックスで、選択、**コード分析**タブ。

   > [!TIP]
   > 新しいプロジェクトの種類など、.NET Core と .NET Standard のアプリケーションはありません、**コード分析**タブ。静的コード分析はこれらのプロジェクトの種類を使用できませんが、ライブ コード分析を使用して取得できます[Roslyn コード アナライザー](roslyn-analyzers-overview.md)します。 Roslyn コード アナライザーからの警告を抑制するのには、この記事の最後にあるメモを参照してください。

1. **プラットフォーム** の **構成およびターゲット プラットフォーム** でビルドの種類を指定します。

1. 自動コード分析を有効または無効にするには、**ビルドに対するコード分析を有効にする**のチェック ボックスをオンまたはオフします。

> [!NOTE]
> **ビルドに対するコード分析を有効にする** チェック ボックスでは、静的コード分析のみに影響します。 影響しない[Roslyn コード アナライザー](roslyn-analyzers-overview.md)、NuGet パッケージとしてインストールした場合、ビルドで常に実行します。 アナライザー エラーをクリアする場合、**エラー一覧**を選択して、現在のすべての違反を抑制する**分析** > **コード分析を実行し、アクティブな抑制問題**メニュー バーでします。 詳細については、次を参照してください。[違反を抑制する](use-roslyn-analyzers.md#suppress-violations)します。
