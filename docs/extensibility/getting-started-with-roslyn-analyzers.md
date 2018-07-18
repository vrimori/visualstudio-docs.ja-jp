---
title: Roslyn アナライザーの概要 |Microsoft ドキュメント
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b887703343dab10f9cc1f0cbf8e2e2b37b0065b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126810"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Roslyn アナライザーの概要

Visual Studio で、プロジェクト ベースのライブ コード アナライザーと API できます作成者ドメイン固有のコード分析、NuGet パッケージの一部として提供します。 これらのアナライザーは、.NET コンパイラ プラットフォーム (コード ネーム"Roslyn") で電源がため、(なくなるを待機している問題を検出するようにコードをビルド) 行する作業を完了する前であってもに、入力すると、コードで警告を生成できます。 アナライザーは、すぐに、コードをクリーンアップできるようにするには Visual Studio 電球のプロンプトで、コードの自動修正を画面もできます。

## <a name="getting-started"></a>作業の開始

[Roslyn ライブ コード アナライザーの概要とチュートリアル](https://msdn.microsoft.com/magazine/dn879356.aspx)

[アナライザーの問題についてのユーザーの修正プログラムを提供するチュートリアルを解決するコードを追加してください。](https://msdn.microsoft.com/magazine/dn904670.aspx)

[概要、および、現実世界アナライザー トークのチュートリアル](http://channel9.msdn.com/events/Build/2015/3-725)

[現実の世界 Roslyn アナライザー](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)することができますもとして、[との通信](http://channel9.msdn.com/events/Build/2015/3-725)

[アナライザーの 3 種類にグループ化、github のいくつかの例](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[概要と、いくつかのアナライザーのツアーを説明します。](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>関連項目

- [Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)
- [Github OSS サイトで複数のドキュメント](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Github の Roslyn アナライザーを使用して実装 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)