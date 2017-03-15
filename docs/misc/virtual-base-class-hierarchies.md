---
title: "仮想基本クラスの階層 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "仮想基底クラスのクラス [C++]"
  - "クラスの階層構造、仮想基底クラス"
  - "派生クラス、クラス階層の考慮事項"
  - "仮想基本クラスの階層内の仮想関数"
  - "仮想基本クラス"
  - "仮想基底クラスの階層"
  - "仮想基底クラスの階層"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 仮想基本クラスの階層
一部のクラス階層は広範になりますが、多くの共通事項を持ちます。 共通コードは基底クラスに実装されますが、特定のコードは派生クラスに実装されます。  
  
 基底クラスにとって、派生クラスが最大の機能を持てるプロトコルを構築できることが重要です。 これらのプロトコルは、一般に、仮想関数を使用して実装されます。 基底クラスは、このような関数に既定の実装を提供します。 などのクラス階層構造で、 `Document` サンプルの有向非循環グラフの図の階層 \(を参照してください [単一継承](/visual-cpp/cpp/single-inheritance)\)、2 つの便利な関数 `Identify` と `WhereIs`です。  
  
 `Identify` 関数が呼び出されると、ドキュメントの種類に適した正しい ID が返されます。`Book` の場合は `doc->Identify()` などの関数呼び出しで ISBN 数を返す必要がありますが、`HelpFile` の場合は製品名およびリビジョン番号の方が適切です。 同様に、`WhereIs` は `Book` の列と棚を返しますが、`HelpFile` の場合はディスク上の場所 \(ディレクトリとファイル名\) を返します。  
  
 `Identify` 関数と `WhereIs` 関数のすべての実装が同じ種類の情報を返すことが重要です。 この場合、文字列が適切です。  
  
 これらの関数は仮想関数として実装され、次に基底クラスへのポインターを使用して呼び出されます。 実際のコードへのバインディングは実行時に発生し、正しい `Identify` 関数または `WhereIs` 関数を選択ます。  
  
## 参照  
 [派生クラスの概要](../misc/overview-of-derived-classes.md)