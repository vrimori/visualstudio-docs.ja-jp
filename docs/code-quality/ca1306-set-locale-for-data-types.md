---
title: "Ca 1306: データ型のロケールの設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc39ece5eaecfdb36576501caa432abeb365b9cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: データ型のロケールを設定します
|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|CheckId|CA1306|  
|カテゴリ|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 作成された 1 つまたは複数のメソッドまたはコンス トラクター<xref:System.Data.DataTable?displayProperty=fullName>または<xref:System.Data.DataSet?displayProperty=fullName>をインスタンス化し、ロケール プロパティを明示的に設定しなかった (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName>または<xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>)。  
  
## <a name="rule-description"></a>規則の説明  
 ロケールでは、数値、通貨記号、および並べ替え順序を使用している書式などのデータに関するカルチャ固有のプレゼンテーション要素を決定します。 作成するときに、<xref:System.Data.DataTable>または<xref:System.Data.DataSet>ロケールを明示的に設定する必要があります。 既定では、これらの型のロケールは、現在のカルチャです。 データベースまたはファイルに格納され、グローバルに共有されるデータ、ロケール通常に設定してください、インバリアント カルチャ (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>)。 データがカルチャ間で共有される、既定のロケールを使用する可能性がありますの内容、<xref:System.Data.DataTable>または<xref:System.Data.DataSet>に表示されるか、正しく解釈されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、ロケールを明示的に設定、<xref:System.Data.DataTable>または<xref:System.Data.DataSet>です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 限定されたローカル ユーザーのライブラリまたはアプリケーションでは、データが共有されていない、または既定の設定でもサポートされているすべてのシナリオで適切に動作する場合は、この規則による警告を抑制しても安全です。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.Data.DataTable>インスタンス。  
  
 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>