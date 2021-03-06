---
title: Roslyn アナライザーの概要 |Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57573adeceda942b2968bfe07108ff4d54a8435f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927695"
---
# <a name="get-started-with-roslyn-analyzers"></a>Roslyn アナライザーを概要します。

Visual Studio で、プロジェクト ベースのライブ コード アナライザー、API の作成者は、NuGet パッケージの一部としてドメイン固有のコード分析を送付できます。 これらのアナライザーを活用するには、.NET コンパイラ プラットフォーム (コードネーム"Roslyn") してため、(これ以上待機している問題を検出するコードをビルドする)、行が完了する前に入力すると、コードで警告する可能性があります。 アナライザーは、すぐに、コードをクリーンアップできるようにする Visual Studio 電球プロンプトを通じて、コードの自動修正も出現できます。

## <a name="get-started"></a>作業開始

[Roslyn のライブ コード アナライザーの概要とチュートリアル](https://msdn.microsoft.com/magazine/dn879356.aspx)

[チュートリアルのコード修正を追加します。アナライザーの問題に対してユーザーの修正を提供します。](https://msdn.microsoft.com/magazine/dn904670.aspx)

[概要と現実の世界のアナライザーのチュートリアルを説明します。](https://channel9.msdn.com/events/Build/2015/3-725)

[現実世界の Roslyn アナライザー](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)としても視聴できる[説明](https://channel9.msdn.com/events/Build/2015/3-725)

[GitHub、アナライザーの 3 種類にグループ化にいくつかの例](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[概要と、いくつかのアナライザーのツアー](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>関連項目

- [Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)
- [チュートリアル: 最初、アナライザーとコード修正を記述します。](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)
- [.NET コンパイラ プラットフォーム パッケージのバージョンのリファレンス](roslyn-version-support.md)
- [OSS の GitHub サイトの複数のドキュメント](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [FxCop ルールが Roslyn アナライザーの実装](http://roslynanalyzersstatus.azurewebsites.net/)
