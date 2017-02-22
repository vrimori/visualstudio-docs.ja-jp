---
title: "CA1061: 基本クラス メソッドを非表示にしません | Microsoft Docs"
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
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1061: 基本クラス メソッドを非表示にしません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 派生型が、基本メソッドの 1 つと同じ名前および同じ数のパラメーターを使用してメソッドを宣言しています。1 つまたは複数のパラメーターは基本メソッドの対応するパラメーターの基本型であり、残りのパラメーターの型がすべて基本メソッドの対応するパラメーターの型と同一です。  
  
## 規則の説明  
 派生メソッドのパラメーター シグネチャ内のある型が、基本メソッドのパラメーター シグネチャ内のそれに対応する型より弱く型指定されていることが、両者の唯一の相違点である場合、基本型内のメソッドが派生型内の同じ名前のメソッドによって隠ぺいされます。  
  
## 違反の修正方法  
 この規則の違反を修正するには、メソッドを削除するか、メソッドの名前を変更するか、またはパラメーター シグネチャを変更して、メソッドが基本メソッドを隠ぺいしないようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反するメソッドを次の例に示します。  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]