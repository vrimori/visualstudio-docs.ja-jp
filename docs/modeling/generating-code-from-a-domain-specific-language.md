---
title: ドメイン固有言語からのコード生成
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 77d26595bd97a98ef9a4cd1f72c14739695bb755
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859849"
---
# <a name="generating-code-from-a-domain-specific-language"></a>ドメイン固有言語からのコード生成
Microsoft[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]モデルで表されたデータから、コード、ドキュメント、構成ファイル、およびその他の成果物を生成する強力な手段を提供します。 使用して[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]、データを表すクラスのセットを作成すると記述できます、テキスト テンプレート クラスの名前を持つプロパティには、そのデータが反映されます。

 たとえば、Fabrikam では、顧客名と電子メール アドレスの XML ファイルがあります。 開発者は、顧客が、クラス、プロパティ名と電子メールを使用するモデルを作成します。 これらは、HTML ページの一部として、すべての顧客のテーブルを生成するこのフラグメントを含む、データを処理するいくつかのテキスト テンプレートを記述します。

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 顧客データベースを処理すると、XML ファイルは、モデル ストアに読み取られます。 A*ディレクティブ プロセッサ*を使用して作成された[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]、Customer クラスをテキスト テンプレートで、コードを使用できるようにします。 多くのテキスト テンプレートは、同じストアに対して実行できます。

 テキスト テンプレートに不可欠な[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]します。 ドメイン モデルは、VSPackage とツールを Visual Studio と統合に使用されるコントロールの場合と同様の要素のソース コードの生成に使用されます。

 このセクションでは、作成、変更で使用するテキスト テンプレートをデバッグする方法のいくつかについて説明します[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]します。

## <a name="in-this-section"></a>このセクションの内容
 [テキスト テンプレートからモデルへのアクセス](../modeling/accessing-models-from-text-templates.md)

 テキスト テンプレートでのドメイン固有言語を参照する基本について説明します。

 [チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 トラブルシューティングと、ドメイン固有言語を表すテキスト テンプレートでのデバッグを行う方法について説明します。

 [チュートリアル: 生成済みディレクティブ プロセッサへのホストの接続](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 生成済みディレクティブ プロセッサへのカスタム ホストを接続する方法について説明します。

 [DslTextTransform コマンド](../modeling/the-dsltexttransform-command.md)

 ドメイン固有言語を参照するテキスト テンプレートのコマンドラインで TextTransform 実行可能ファイルを実行するコマンド ファイルについて説明します。

## <a name="reference"></a>参照
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)

 テキスト テンプレートのディレクティブとコントロール ブロックの構文について説明します。

## <a name="related-sections"></a>関連項目
 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 テキスト テンプレート変換プロセスをについて説明します。

 [ビルド処理でのコード生成](../modeling/code-generation-in-a-build-process.md)

 ビルド サーバーでの DSL からファイルを生成している場合は、このトピックを読みます。