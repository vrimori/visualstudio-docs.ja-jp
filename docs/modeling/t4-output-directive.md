---
title: "T4 出力ディレクティブ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 出力ディレクティブ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テキスト テンプレートでは、`output` ディレクティブを使用してファイル名の拡張子と変換ファイルのエンコードを定義します。  
  
 たとえば、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトに **MyTemplate.tt** という名前のテンプレート ファイルがあり、次のディレクティブが含まれるとします。  
  
 `<#@output extension=".cs"#>`  
  
 その場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は **MyTemplate.cs** という名前のファイルを生成します。  
  
 `output` ディレクティブは、実行時 \(前処理済み\) のテキスト テンプレートには必要ありません。  その代わりに、アプリケーションは `TextTransform()` を呼び出して、生成済みの文字列を取得します。  詳細については、「[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)」を参照してください。  
  
## 出力ディレクティブの使用  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 各テキスト テンプレートには複数の `output` ディレクティブを含めてはいけません。  
  
## extension 属性  
 生成されたテキスト出力ファイルのファイル名の拡張子を指定します。  
  
 既定値は **.cs** です。  
  
 次に例を示します。  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 許容される値:  
 任意の有効なファイル名の拡張子。  
  
## encoding 属性  
 出力ファイルが生成されるときに使用するエンコードを指定します。  次に例を示します。  
  
 `<#@ output encoding="utf-8"#>`  
  
 既定値は、テキスト テンプレート ファイルが使用するエンコードです。  
  
 許容される値:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` \(システムの既定値\)  
  
 一般に、<xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> が返す任意のエンコードの WebName 文字列または CodePage 数値を使用できます。