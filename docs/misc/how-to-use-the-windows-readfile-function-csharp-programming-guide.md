---
title: "方法: Windows の ReadFile 関数を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile 関数 [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# 方法: Windows の ReadFile 関数を使用する (C# プログラミング ガイド)
この例では、テキスト ファイルの読み取りと表示を行うことにより、Windows の `ReadFile` 関数を示します。  `ReadFile` 関数では、パラメーターとしてポインターを必要とするため、`unsafe` コードを使用する必要があります。  
  
 `Read` 関数に渡されるバイト配列はマネージ型です。  つまり、共通言語ランタイム \(CLR: Common Language Runtime\) のガベージ コレクターは、配列が使用するメモリを自由に再配置できます。  これを防ぐために、[fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) を使用して、メモリへのポインターを取得し、ガベージ コレクターがそれを移動しないようにマークします。  `fixed` ブロックの末尾で、メモリはガベージ コレクションによる移動の対象に自動的に戻ります。  
  
 この機能は、*宣言固定*と呼ばれます。  メモリを固定すると、ガベージ コレクションが `fixed` ブロック内で発生しない限り \(ほとんど発生しません\)、オーバーヘッドがきわめて少なくなります。  ただし、メモリの固定によって、グローバル ガベージ コレクションの実行中に望ましくない副作用が生じる場合があります。  固定されたバッファーによって、メモリの領域を圧縮するガベージ コレクターの機能が大幅に制限されます。  したがって、メモリの固定は可能な限り避ける必要があります。  
  
## 使用例  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](/dotnet/csharp/programming-guide/index)   
 [C\# リファレンス](/dotnet/csharp/language-reference/index)   
 [unsafe コードとポインター](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [ポインター型](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)