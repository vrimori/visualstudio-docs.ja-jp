---
title: .NET コンパイラ プラットフォーム (&quot;Roslyn&quot;) 拡張機能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26196b18c6e44ec8f0697fbc656f2934eff1904b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918811"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET コンパイラ プラットフォーム (&quot;Roslyn&quot;) 拡張機能
.NET コンパイラ プラットフォーム ("Roslyn") の主要な目的は、c# および Visual Basic コンパイラを開くと、ツールを許可して、プログラムについて豊富な情報コンパイラを共有する開発者があります。 コード分析ツールでは、コードの品質を向上させ、コード ジェネレーターの補助アプリケーションの構築にします。 スマートなツールとして、コンパイラのみが知っているコードの深い知識の詳細と詳細にアクセスが必要があります。 不透明なトランスレーター (内のソース コードおよびオブジェクト コード) ではなく、Roslyn コンパイラは、ツールやアプリケーション内のコード関連のタスクに使用できる Api を提供します。

 最も重要な部分は Roslyn コンパイラ、その Api、サンプルとチュートリアル、およびこれらの Api の上に構築された実際のツールがすべて完全にオープン ソースがある[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)します。 詳細については、Roslyn を使用するには、OSS サイトにアクセスしてください。 最新情報へのリンクが表示されますC#と Visual Basic の機能として、Roslyn Api を利用するツールのビルダーを開始するエンドユーザーだけでなく、リンクとして使用できます。

## <a name="see-also"></a>関連項目
 [Roslyn アナライザーを概要します。](../extensibility/getting-started-with-roslyn-analyzers.md)