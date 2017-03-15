---
title: "型または &#39;New&#39; が必要です | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32092"
  - "bc32092"
helpviewer_keywords: 
  - "BC32092"
ms.assetid: b3041c1d-837c-4d58-bbb4-5c46f227b66d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型または &#39;New&#39; が必要です
ジェネリック型の宣言に含まれる型パラメーターは `As` キーワードを使用して制約リストを導入していますが、有効な制約が指定されていません。  
  
 型パラメーターの制約は、有効なクラスかインターフェイス、または、`Class`、`Structure`、`New` キーワードのいずれかにする必要があります。 無効な制約を指定するか、いずれも指定しない場合、コンパイラはこのエラーを生成します。  
  
 **エラー ID:** BC32092  
  
### このエラーを解決するには  
  
1.  型パラメーターが制約を受ける方法を判別し、制約リストで適切な制約を指定します。  
  
2.  クラスまたはインターフェイスによって型パラメーターを制限する場合は、制約のスペルが正しいことを確認します。  
  
3.  1 つの型パラメーターで複数の制約を分離する場合はコンマで区切り、制約のリストを中かっこで囲みます \(`{ }`\)。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)