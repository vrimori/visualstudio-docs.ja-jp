---
title: "例外のトラブルシューティング : System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OutOfMemoryException クラス"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.OutOfMemoryException
<xref:System.OutOfMemoryException> 例外は、メモリの割り当てに失敗するとスローされます。  
  
## 関連するヒント  
 **配列を作成する場合、サイズが適切であることを確認します。**  
 Visual Basic を使用している場合、詳細については、「[配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)」を参照してください。  
  
 C\# を使用している場合、詳細については、「[配列](/dotnet/csharp/programming-guide/arrays/index)」を参照してください。  
  
 **内部処理用および新しいマネージ オブジェクト用に十分なメモリがあることを確認してください。**  
 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] でプログラミングしている場合、内部処理用および新しいマネージ オブジェクト用に十分なメモリがないときは、共通言語ランタイムによってこの例外がスローされます。 この例外を回避するには、64 KB 以上のメモリを消費する大規模メソッドのプログラミングを行わないでください。  
  
## コメント  
 一般に、次の場合には、マネージ メモリの使用量が過度に多くなります。  
  
-   大容量のデータ セットをメモリに読み込んだ。  
  
-   多数のキャッシュ エントリを作成した。  
  
-   大きなファイルをアップロードまたはダウンロードした。  
  
-   ファイルの解析時に正規表現または文字列を過度に使用した。  
  
-   過度のビューステート。  
  
-   セッション状態のデータが大きすぎる。または、セッション数が多すぎる。  
  
 セーフ配列 \(サイズが固定されていない配列\) を含むユーザー定義型を返す COM オブジェクトに対してメソッドを呼び出す場合、"この操作を完了するために利用できる記憶領域が不足しています。" というメッセージと共にこの例外がスローされることがあります。 これは、セーフ配列型を持つ構造体フィールドを .NET Framework がマーシャリングできないために起こります。  
  
## 参照  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)