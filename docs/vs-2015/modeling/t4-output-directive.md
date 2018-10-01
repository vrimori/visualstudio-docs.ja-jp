---
title: T4 出力ディレクティブ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e0eaa2d8e3fc257e14e04bad3cac706b8a3bc92a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539009"
---
# <a name="t4-output-directive"></a>T4 出力ディレクティブ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[T4 出力ディレクティブ](https://docs.microsoft.com/visualstudio/modeling/t4-output-directive)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] テキスト テンプレートでは、`output` ディレクティブを使用してファイル名の拡張子と変換ファイルのエンコードを定義します。  
  
 たとえば場合、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]という名前のテンプレート ファイルがプロジェクトに含まれています**MyTemplate.tt**次のディレクティブが含まれています。  
  
 `<#@output extension=".cs"#>`  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]という名前のファイルが生成されます**MyTemplate.cs**  
  
 `output` ディレクティブは、実行時 (前処理済み) のテキスト テンプレートには必要ありません。 その代わりに、アプリケーションは `TextTransform()` を呼び出して、生成済みの文字列を取得します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)します。  
  
## <a name="using-the-output-directive"></a>出力ディレクティブの使用  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 各テキスト テンプレートには複数の `output` ディレクティブを含めてはいけません。  
  
## <a name="extension-attribute"></a>拡張属性  
 生成されたテキスト出力ファイルのファイル名の拡張子を指定します。  
  
 既定値は **.cs**  
  
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



