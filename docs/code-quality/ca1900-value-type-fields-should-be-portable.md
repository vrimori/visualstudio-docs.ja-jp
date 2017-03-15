---
title: "CA1900: 値型フィールドはポータブルでなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1900: 値型フィールドはポータブルでなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|分類|Microsoft.Portability|  
|互換性に影響する変更点|あり – フィールドがアセンブリの外部で参照できる場合<br /><br /> なし \- フィールドがアセンブリの外部で参照できない場合|  
  
## 原因  
 この規則は、明示的なレイアウトによって宣言された構造体が、64 ビット オペレーティング システムでアンマネージ コードにマーシャリングされるときに、適切にアライメントされるかどうかを確認します。  IA\-64 は、アライメントされていないメモリのアクセスを許可しません。この違反が修正されない場合、プロセスはクラッシュします。  
  
## 規則の説明  
 明示的なレイアウトを持つ構造体に、正しくアライメントされていないフィールドが含まれていると、64 ビット オペレーティング システムでクラッシュが発生します。  
  
## 違反の修正方法  
 8 バイト未満のすべてのフィールドは、それぞれのサイズの倍数のオフセットを持つ必要があります。また、8 バイト以上のフィールドは、8 の倍数のオフセットを持つ必要があります。  状況に応じて、`LayoutKind.Explicit` の代わりに  `LayoutKind.Sequential` を使用して修正することもできます。  
  
## 警告を抑制する状況  
 この警告は、エラーで生成された場合にのみ抑制します。