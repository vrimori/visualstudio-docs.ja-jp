---
title: "CA1306: データ型のロケールを設定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1306: データ型のロケールを設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドまたはコンストラクターで、1 つ以上の <xref:System.Data.DataTable?displayProperty=fullName> インスタンスまたは <xref:System.Data.DataSet?displayProperty=fullName> インスタンスが作成され、ロケール プロパティ \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> または <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\) が明示的に設定されませんでした。  
  
## 規則の説明  
 ロケールによって、データに関するカルチャ固有の表示要素が決まります。たとえば、数値、通貨記号、並べ替え順序に使用する形式などです。  <xref:System.Data.DataTable> または <xref:System.Data.DataSet> を作成するときは、ロケールを明示的に設定する必要があります。  既定で、この型のロケールは現在のカルチャです。  データベースまたはファイルに格納され、グローバルに共有されているデータの場合、通常、ロケールはインバリアント カルチャ \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\) に設定します。  データを複数のカルチャで共有する場合、既定のロケールを使用すると、<xref:System.Data.DataTable> または <xref:System.Data.DataSet> のコンテンツが誤って表示されたり解釈されたりすることがあります。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Data.DataTable> または <xref:System.Data.DataSet> のロケールを明示的に設定します。  
  
## 警告を抑制する状況  
 ライブラリまたはアプリケーションが限定されたローカル ユーザーを対象にしている場合、データを共有していない場合、または既定の設定でどのような状況でも適切に動作する場合、この規則による警告を抑制しても安全です。  
  
## 使用例  
 次の例では、2 つの <xref:System.Data.DataTable> インスタンスを作成します。  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## 参照  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>