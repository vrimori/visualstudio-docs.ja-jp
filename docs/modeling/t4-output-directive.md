---
title: T4 出力ディレクティブ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 40ade1ec02c940270b3a0540b11e719081f1a6de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="t4-output-directive"></a>T4 出力ディレクティブ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テキスト テンプレートでは、`output` ディレクティブを使用してファイル名の拡張子と変換ファイルのエンコードを定義します。  
  
 たとえば場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前のテンプレート ファイルがプロジェクトに含まれる**MyTemplate.tt**次のディレクティブが含まれています。  
  
 `<#@output extension=".cs"#>`  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前のファイルが生成されます**MyTemplate.cs**  
  
 `output` ディレクティブは、実行時 (前処理済み) のテキスト テンプレートには必要ありません。 その代わりに、アプリケーションは `TextTransform()` を呼び出して、生成済みの文字列を取得します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
## <a name="using-the-output-directive"></a>出力ディレクティブの使用  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 各テキスト テンプレートには複数の `output` ディレクティブを含めてはいけません。  
  
## <a name="extension-attribute"></a>拡張属性  
 生成されたテキスト出力ファイルのファイル名の拡張子を指定します。  
  
 既定値は**.cs**  
  
 次に例を示します。  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 許容される値:  
 任意の有効なファイル名の拡張子。  
  
## <a name="encoding-attribute"></a>エンコーディング属性  
 出力ファイルが生成されるときに使用するエンコードを指定します。 次に例を示します。  
  
 `<#@ output encoding="utf-8"#>`  
  
 既定値は、テキスト テンプレート ファイルが使用するエンコードです。  
  
 許容される値:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (システムの既定値)  
  
 一般に、<xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> が返す任意のエンコードの WebName 文字列または CodePage 数値を使用できます。