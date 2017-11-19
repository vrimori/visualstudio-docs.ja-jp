---
title: ".NET コンパイラ プラットフォーム (&quot;Roslyn&quot;) Extensibility |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f9811440146e1d758158a64fd227ba0a2c2e1e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET コンパイラ プラットフォーム (&quot;Roslyn&quot;) の機能拡張
.NET コンパイラ プラットフォーム ("Roslyn") のコア ミッションを c# および Visual Basic コンパイラを開くと、ツールを許可して、プログラムに関する豊富な情報と、コンパイラで共有する開発者が必要です。 コード分析ツールは、コード品質の向上し、アプリケーションの構築のジェネレーターの参考情報をコードします。 スマートなツールとして、詳細とのみコンパイラ保有深いコード知識の詳細にアクセスが必要です。 不透明なトランスレータ (ソース コード内とオブジェクト コードを) するのではなく Roslyn コンパイラは、ツールやアプリケーション内のコードに関連するタスクを使用できる Api が用意されています。  
  
 最も良いところはある Roslyn コンパイラでは、その Api、サンプル、チュートリアル、およびこれらの Api の上に構築される実際のツールをすべて完全にオープン ソース[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)です。 Roslyn の概要と詳細 OSS サイトに移動してください。 リンクを最新 c# および VB の機能、エンド ユーザーとして使用できるを取得するだけでなく概要 Roslyn Api を利用してツール ビルダーとしてへのリンクが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Roslyn アナライザーの概要](../extensibility/getting-started-with-roslyn-analyzers.md)