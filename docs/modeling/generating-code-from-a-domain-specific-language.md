---
title: "ドメイン固有言語からのコード生成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# ドメイン固有言語からのコード生成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] はモデルで表されるデータからコード、ドキュメント、構成ファイル、およびそのほかの成果物を生成できる強力な方法を提供します。  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]を使用して、データを表す、名前とプロパティがデータを反映するクラスのテキスト テンプレートを記述できます一連のクラスを作成する。  
  
 たとえば、 Fabrikam に顧客名と電子メール アドレスの XML ファイルがあります。  開発者はプロパティ名、電子メールと顧客はクラスであるモデルを作成します。  これらは HTML ページの一部としてすべての顧客のテーブルを生成するこのフラグメントを含むデータを操作する複数のテキスト テンプレートを作成する:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 顧客データベースを処理するときは、 XML ファイルは、モデル ストアに読込まれます。  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]を使用して作成された *ディレクティブ プロセッサは*、 Customer クラスをテキスト テンプレートにコードで使用できるようにします。 多くのテキスト テンプレートは、同じストアに対して実行できます。  
  
 テキスト テンプレートは [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]に必要です。  それらがドメイン モデルの要素のソース・コードを生成するために使用されますが、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のツールを統合するために使用されるコントロールと VSPackage の場合は。  
  
 このセクションでは [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]で使用されるテキスト テンプレートを作成、変更、およびデバッグする方法のうちのいくつかについて説明します。  
  
## このセクションの内容  
 [テキスト テンプレートからモデルへのアクセス](../modeling/accessing-models-from-text-templates.md)  
  
 テキスト テンプレートのドメイン固有言語の参照についての基本情報を提供します。  
  
 [チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ](../Topic/Walkthrough:%20Debugging%20a%20Text%20Template%20that%20Accesses%20a%20Model.md)  
  
 ドメイン固有言語を示すテキスト テンプレートのトラブルシューティングとデバッグを行う方法について説明します。  
  
 [チュートリアル: 生成済みディレクティブ プロセッサへのホストの接続](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 生成されたディレクティブ プロセッサにカスタム ホストを追加する方法について説明します。  
  
 [DslTextTransform コマンド](../modeling/the-dsltexttransform-command.md)  
  
 ドメイン固有言語を参照するテキスト テンプレートのコマンド ラインの TextTransform の実行可能ファイルを実行するコマンド ファイルについて説明します。  
  
## 関連項目  
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
 テキスト テンプレートのディレクティブと制御ブロックの構文について説明します。  
  
## 関連項目  
 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 テキスト テンプレート変換プロセスを説明します。  
  
 [ビルド処理でのコード生成](../modeling/code-generation-in-a-build-process.md)  
  
 ビルド サーバーで DSL からファイルを生成する場合に、このトピックを読んでください。