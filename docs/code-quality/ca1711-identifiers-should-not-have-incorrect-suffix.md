---
title: "CA1711: 識別子は、不適切なサフィックスを含むことはできません | Microsoft Docs"
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
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711: 識別子は、不適切なサフィックスを含むことはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 識別子のサフィックスが不適切です。  
  
## 規則の説明  
 規則では、特定の基本型を拡張する型、特定のインターフェイスを実装する型、またはそのような型から派生した型の名前にのみ、固有の予約済みサフィックスを末尾に付けます。  その他の型名では、予約済みのサフィックスを使用しないでください。  
  
 予約済みのサフィックス、および関連付けられている基本型とインターフェイスを次の表に示します。  
  
|サフィックス|基本型\/インターフェイス|  
|------------|-------------------|  
|Attribute|<xref:System.Attribute?displayProperty=fullName>|  
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|イベント ハンドラーのデリゲート|  
|Exception|<xref:System.Exception?displayProperty=fullName>|  
|Permission|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Stream|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 その他に、次のサフィックスは使用しないでください。  
  
-   Delegate  
  
-   Enum  
  
-   Impl – 代わりに ”Core” を使用します。  
  
-   型を以前のバージョンと区別するための Ex または類似のサフィックス  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## 違反の修正方法  
 型名からサフィックスを削除します。  
  
## 警告を抑制する状況  
 アプリケーション ドメインでサフィックスに明確な意味がある場合を除き、この規則による警告を抑制しないでください。  
  
## 関連規則  
 [CA1710: 識別子は、正しいサフィックスを含んでいなければなりません](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)  
  
## 参照  
 [属性](../Topic/Attributes1.md)   
 [イベントとデリゲート](http://msdn.microsoft.com/ja-jp/d98fd58b-fa4f-4598-8378-addf4355a115)