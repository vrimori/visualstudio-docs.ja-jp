---
title: "オーバーロードされた関数のアドレス | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "関数のオーバー ロードされたアドレス [C++]"
  - "オーバー ロードを返すアドレス [C++]"
  - "関数のオーバー ロード、関数アドレス"
  - "このポインターをオーバー ロードされた関数"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# オーバーロードされた関数のアドレス
引数のない関数名を使用すると、その関数のアドレスが返されます。 次に例を示します。  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 前の例では、`Func` の最初のバージョンが選択され、そのアドレスが `pFunc` にコピーされます。  
  
 コンパイラは、ターゲットの引数リストと完全に一致する引数リストを持つ関数を検索することにより、そのバージョンの関数を選択するかを決定します。 オーバーロード関数宣言の引数は、次のいずれかと一致します。  
  
-   初期化されるオブジェクト \(前の例を参照してください\)  
  
-   代入ステートメントの左側  
  
-   関数への仮引数  
  
-   ユーザー定義演算子に対する仮引数  
  
-   関数の戻り値の型  
  
 厳密な一致が見つからない場合、関数のアドレスを受け取る式があいまいになり、エラーが生成されます。  
  
 前の例では非メンバー関数 `Func` が使用されていましたが、オーバーロードされたメンバー関数のアドレスを受け取るときには同じ規則が適用されることに注意してください。  
  
## 参照  
 [オーバー ロード \(C\+\+\)](../misc/overloading-cpp.md)