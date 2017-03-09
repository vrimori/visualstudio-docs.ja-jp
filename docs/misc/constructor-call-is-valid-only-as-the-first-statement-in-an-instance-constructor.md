---
title: "コンストラクターの呼び出しは、インスタンス コンストラクター内の最初のステートメントとしてのみ有効です | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コンストラクターの呼び出しは、インスタンス コンストラクター内の最初のステートメントとしてのみ有効です
`New()` への呼び出しが、コンストラクターの最初のステートメントの後に発生します。 1 つのコンストラクターが別のコンストラクターを明示的に呼び出す場合、`Sub New()` ステートメントに続く最初のステートメントで呼び出す必要があります。  
  
 **エラー ID:** BC30282  
  
### このエラーを解決するには  
  
-   `New()` への呼び出しを削除するか、コンストラクターの先頭に移動します。  
  
## 参照  
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)