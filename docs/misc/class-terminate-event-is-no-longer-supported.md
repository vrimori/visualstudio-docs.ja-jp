---
title: "&#39;Class_Terminate&#39; イベントはサポートされなくなりました | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Class_Terminate&#39; イベントはサポートされなくなりました
'Class\_Terminate' イベントはサポートされなくなりました。 リソースを解放するには、'Sub Finalize' を使用します。  
  
 以前のバージョンの Visual Basic の `Class_Terminate` イベントは、クラスのデストラクターに置き換えられています。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42002  
  
### このエラーを解決するには  
  
-   `Finalize` という名前の `Sub` プロシージャを宣言して、クラスを終了します。 インスタンスへのアクティブな参照がこれ以上存在しないことをガベージ コレクターが検出すると、`Sub Finalize` が呼び出されます。  
  
## 参照  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/ja-jp/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [ビルド内にありません: 方法: Dispose Finalize パターンを実装する \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/adf7a232-4ebb-485d-8626-8d64421eb0c4)