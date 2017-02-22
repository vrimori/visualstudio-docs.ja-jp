---
title: "CA1821: 空のファイナライザーを削除します | Microsoft Docs"
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
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1821: 空のファイナライザーを削除します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 型が空のファイナライザーを実装しているか、基本型ファイナライザーのみを呼び出しているか、条件付きで出力されたメソッドのみを呼び出しています。  
  
## 規則の説明  
 オブジェクトの有効期間の追跡に関連するパフォーマンス オーバーヘッドが増大するため、ファイナライザーは可能な限り使用しないでください。  ガベージ コレクターはファイナライザーを実行してからオブジェクトを収集します。  そのため、オブジェクトの収集には 2 つのコレクションが必要となります。  空のファイナライザーを使用すると、オーバーヘッドが増大するだけで何の利点もありません。  
  
## 違反の修正方法  
 空のファイナライザーを削除します。  デバッグのためにファイナライザーが必要な場合は、ファイナライザー全体を `#if DEBUG / #endif` ディレクティブで囲んでください。  
  
## 警告を抑制する状況  
 この規則によるメッセージは抑制しないでください。  終了処理を省略した場合のエラーによってパフォーマンスが低下します。また何も利点がありません。  
  
## 使用例  
 次の例は、削除する必要のある空のファイナライザー、`#if DEBUG / #endif` ディレクティブで囲む必要のあるファイナライザー、および `#if DEBUG / #endif` ディレクティブを正しく使用しているファイナライザーを示しています。  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]