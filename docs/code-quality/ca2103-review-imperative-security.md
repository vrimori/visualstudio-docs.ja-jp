---
title: "CA2103: 命令型のセキュリティを確認します | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103: 命令型のセキュリティを確認します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドが強制セキュリティを使用しています。また、そのメソッドで、確認要求がアクティブな場合に変更できるステータス情報または戻り値を使用して、アクセス許可を構築している可能性があります。  
  
## 規則の説明  
 強制セキュリティでは、マネージ オブジェクトを使用して、コード実行時のアクセス許可とセキュリティ アクションを指定しています。一方、宣言セキュリティでは、属性を使用して、メタデータにアクセス許可とアクションを格納しています。  強制セキュリティには、アクセス許可オブジェクトの状態を設定し、実行時まで使用できない情報を使用してセキュリティ アクションを選択できるという高い柔軟性があります。  この柔軟性は、アクセス許可の状態を判断するときに使用する実行時の情報が、アクションの実行中に変更されるリスクにもつながります。  
  
 できる限り、宣言セキュリティを使用します。  宣言的な確認要求は理解が容易です。  
  
## 違反の修正方法  
 強制セキュリティの確認要求を再確認し、アクセス許可の状態が、そのアクセス許可の使用中に変更できる情報に依存しないようにします。  
  
## 警告を抑制する状況  
 アクセス許可が変化するデータに依存していない場合は、この規則による警告を抑制しても安全です。  ただし、強制の確認要求を宣言の確認要求に変更することをお勧めします。  
  
## 参照  
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)