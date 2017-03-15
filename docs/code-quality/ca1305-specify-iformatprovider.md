---
title: "CA1305: IFormatProvider を指定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1305: IFormatProvider を指定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドまたはコンストラクターが、<xref:System.IFormatProvider?displayProperty=fullName> パラメーターを受け入れるオーバーロードを持つメンバーを 1 つ以上呼び出し、そのメソッドまたはコンストラクターは、<xref:System.IFormatProvider> パラメーターを使用するオーバーロードを呼び出していません。  この規則では、<xref:System.IFormatProvider> パラメーターを無視すると規定されている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] メソッドと、以下に示すその他のメソッドの呼び出しを無視します。  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## 規則の説明  
 <xref:System.Globalization.CultureInfo?displayProperty=fullName> オブジェクトまたは <xref:System.IFormatProvider> オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。  また、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のメンバーは、コードに適していない可能性を考慮して、既定のカルチャと書式指定を選択します。  状況に合わせてコードが適切に機能するように、次のガイドラインに従ってカルチャ固有の情報を指定します。  
  
-   値がユーザーに表示される場合、現在のカルチャを使用します。  「<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>」を参照してください。  
  
-   値が格納され、ソフトウェアからアクセスされる場合 \(ファイルまたはデータベースに保持される場合\)、インバリアント カルチャを使用します。  「<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>」を参照してください。  
  
-   値の出力先がわからない場合、データの使用者または提供者がカルチャを指定するようにします。  
  
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が使用されるのは、<xref:System.Resources.ResourceManager?displayProperty=fullName> クラスのインスタンスを使用して、ローカライズされたリソースを取得する場合のみであることに注意してください。  
  
 オーバーロードされたメンバーの既定の動作がコードの要件に適している場合でも、カルチャ固有のオーバーロードを明示的に呼び出すことをお勧めします。これは、コードが自己文書化され、保守が容易になるためです。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Globalization.CultureInfo> または <xref:System.IFormatProvider> を受け入れるオーバーロードを使用し、上記のガイドラインに従って引数を指定します。  
  
## 警告を抑制する状況  
 既定のカルチャ\/書式プロバイダーが正しく選択されていて、開発上、コードの保守性が重要ではない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 `BadMethod` がこの規則の 2 つの違反を引き起こす例を次に示します。  `GoodMethod` は、インバリアント カルチャを <xref:System.String.Compare%2A> に渡すことで 1 つ目の違反を修正し、現在のカルチャを <xref:System.String.ToLower%2A> に渡すことで 2 つ目の違反を修正します。これは、`string3` がユーザーに表示されているためです。  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## 使用例  
 次の例は、<xref:System.DateTime> 型で選択された既定の <xref:System.IFormatProvider> に与える現在のカルチャの影響を示します。  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **6\/4\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## 関連規則  
 [CA1304: CultureInfo を指定します](../Topic/CA1304:%20Specify%20CultureInfo.md)  
  
## 参照  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/ja-jp/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)