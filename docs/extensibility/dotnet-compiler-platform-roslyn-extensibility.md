---
title: .NET コンパイラ プラットフォーム (&quot;Roslyn&quot;) Extensibility |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09287c48285bfcdc32b1a7d558d44f9d212f1b41
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126937"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET コンパイラ プラットフォーム (&quot;Roslyn&quot;) の機能拡張
.NET コンパイラ プラットフォーム ("Roslyn") のコア ミッションを c# および Visual Basic コンパイラを開くと、ツールを許可して、プログラムに関する豊富な情報と、コンパイラで共有する開発者が必要です。 コード分析ツールは、コード品質の向上し、アプリケーションの構築のジェネレーターの参考情報をコードします。 スマートなツールとして、詳細とのみコンパイラ保有深いコード知識の詳細にアクセスが必要です。 不透明なトランスレータ (ソース コード内とオブジェクト コードを) するのではなく Roslyn コンパイラは、ツールやアプリケーション内のコードに関連するタスクを使用できる Api が用意されています。  
  
 最も良いところはある Roslyn コンパイラでは、その Api、サンプル、チュートリアル、およびこれらの Api の上に構築される実際のツールをすべて完全にオープン ソース[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)です。 Roslyn の概要と詳細 OSS サイトに移動してください。 リンクを最新 c# および VB の機能、エンド ユーザーとして使用できるを取得するだけでなく概要 Roslyn Api を利用してツール ビルダーとしてへのリンクが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Roslyn アナライザーの概要](../extensibility/getting-started-with-roslyn-analyzers.md)