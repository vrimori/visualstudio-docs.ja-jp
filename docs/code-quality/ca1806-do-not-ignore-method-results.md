---
title: "CA1806: メソッドの結果を無視しない | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806: メソッドの結果を無視しない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 この警告には複数の原因が考えられます。  
  
-   新しいオブジェクトが作成されましたが、使用されていません。  
  
-   新しい文字列を作成して返すメソッドが呼び出されましたが、新しい文字列が使用されていません。  
  
-   COM メソッドまたは P\/Invoke メソッドから返された HRESULT またはエラー コードが使用されていません。  規則の説明  
  
 不要なオブジェクトの作成や、使用されないオブジェクトに関連するガベージ コレクションは、パフォーマンスの低下を招きます。  
  
 文字列は変更できないので、String.ToUpper などのメソッドは、呼び出し元メソッドで文字列のインスタンスを変更するのではなく、文字列の新しいインスタンスを返します。  
  
 HRESULT またはエラー コードを無視すると、エラー状態で予期しない動作が発生したり、リソース不足状態になったりする可能性があります。  
  
## 違反の修正方法  
 メソッド A でオブジェクト B の新しいインスタンスを作成し、そのインスタンスが使用されていない場合は、そのインスタンスを別のメソッドに引数として渡して、変数に代入します。  オブジェクトを作成する必要がなければ、そのコードを削除します。または  
  
 メソッド A でメソッド B を呼び出し、メソッド B から返された新しい文字列インスタンスを使用していない場合は、  そのインスタンスを別のメソッドに引数として渡して、変数に代入します。  または、必要なければ呼び出しを削除します。  
  
 または  
  
 メソッド A でメソッド B を呼び出し、メソッド B から返された HRESULT またはエラー コードを使用していない場合は、  その結果を条件付きステートメントで使用して、結果を変数に割り当てます。または、その結果を別のメソッドに引数として渡します。  
  
## 警告を抑制する状況  
 オブジェクト作成の操作に何らかの目的がある場合を除いて、この規則による警告は抑制しないでください。  
  
## 使用例  
 String.Trim を呼び出した結果を無視するクラスの例を次に示します。  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## 使用例  
 String.Trim の結果を呼び出し元の変数に代入することによって前述の違反を修正するコード例を次に示します。  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## 使用例  
 作成したオブジェクトを使用しないメソッドの例を次に示します。  
  
> [!NOTE]
>  この違反は、Visual Basic では再現できません。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## 使用例  
 オブジェクトの不要な作成を削除することによって上記の違反を修正するコード例を次に示します。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## 使用例  
 GetShortPathName というネイティブ メソッドから返されたエラー コードを無視するメソッドの例を次に示します。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## 使用例  
 呼び出しに失敗したときに、エラー コードをチェックして例外をスローすることによって上記の違反を修正するコード例を次に示します。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]