---
title: "ドメイン固有言語から、コードの生成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 98811cc3e7830dfcbf548bc34c5b3ee268e6f858
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="generating-code-from-a-domain-specific-language"></a>ドメイン固有言語からのコード生成
Microsoft[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]モデルで表されるデータからコード、ドキュメント、構成ファイル、および他の成果物を生成する強力な手段を提供します。 使用して[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]データを表すクラスのセットを作成することができますとで記述できるテキスト テンプレートをクラス名およびプロパティがそのデータを反映します。  
  
 たとえば、Fabrikam では、顧客の名前と電子メール アドレスの XML ファイルがあります。 開発者は、顧客のプロパティの名前と電子メールを持つ、クラス、モデルを作成します。 この HTML ページの一部としてすべての顧客のテーブルを生成するフラグメントを含む、データを処理するいくつかのテキスト テンプレートを記述するには。  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 顧客データベースを処理すると、モデル ストアに XML ファイルが読み取られます。 A*ディレクティブ プロセッサ*を使用して作成された、 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]、Customer クラスをテキスト テンプレートで、コードを使用できるようにします。 多くのテキスト テンプレートは、同じストアに対して実行することができます。  
  
 テキスト テンプレートに不可欠な[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]します。 ドメイン モデルは、VSPackage とコントロールを使用して、ツールを統合するために使用する場合と同様の要素のソース コードの生成に使用される、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
 このセクションでは、作成、変更、およびで使われるテキスト テンプレートをデバッグする方法のいくつかについて説明[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テキスト テンプレートからモデルへのアクセス](../modeling/accessing-models-from-text-templates.md)  
  
 テキスト テンプレートでのドメイン固有言語に参照に関する基本的な情報を提供します。  
  
 [チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 トラブルシューティングやドメイン固有言語を表すテキスト テンプレートでのデバッグを行う方法について説明します。  
  
 [チュートリアル: 生成済みディレクティブ プロセッサへのホストの接続](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 カスタム生成されたディレクティブ プロセッサをホストに接続する方法について説明します。  
  
 [DslTextTransform コマンド](../modeling/the-dsltexttransform-command.md)  
  
 ドメイン固有言語を参照するテキスト テンプレートのコマンドラインで TextTransform 実行可能ファイルを実行するコマンド ファイルについて説明します。  
  
## <a name="reference"></a>参照  
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
 テキスト テンプレートのディレクティブとコントロール ブロックの構文を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 テキスト テンプレート変換プロセスをについて説明します。  
  
 [ビルド処理でのコード生成](../modeling/code-generation-in-a-build-process.md)  
  
 ビルド サーバーでの DSL からファイルを生成する場合は、このトピックの内容を読み取る。