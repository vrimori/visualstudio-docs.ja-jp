---
title: "コンパイラ エラー CS0400 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0400"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0400"
ms.assetid: 58f91f3b-30f4-433b-9a13-0cff258a2630
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0400
型または名前空間名 'identifier' はグローバル名前空間に見つかりませんでした。アセンブリ参照が不足しています。  
  
 グローバル スコープ演算子 \(`::`\) で定義された識別子が、グローバル名前空間に見つかりません。 その識別子を格納するアセンブリ参照を指定していないか、グローバル名前空間以外のクラスまたは名前空間で識別子が宣言されている可能性があります。 このエラーは、グローバルなスコープを持つ識別子が宣言されていなかったり、スペルに誤りがあったりする場合にも発生します。  
  
 このエラーを回避するには、識別子の宣言を探して正しいスペルを確認します。宣言が別のアセンブリに存在する場合は、アセンブリ参照が適切であることを確認します。 識別子が別の型または名前空間の中で宣言されていた場合は、:: の後に完全修飾名をご使用ください。 次の例では CS0400 エラーが生成されます。  
  
```  
// CS0400.cs class C { public static void Main() { // CS0400 - D could not be found // in the global namespace. global::D d = new global::D(); } }  
```