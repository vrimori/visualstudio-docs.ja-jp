---
title: IntelliCode に関する質問と回答
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079312"
---
# Visual Studio IntelliCode のよくあるご質問

Visual Studio IntelliCode にご関心をお寄せいただきありがとうございます。 この短い FAQ で一部のご質問にお答えできれば幸いです。

## Q. Visual Studio IntelliCode とは何ですか?

Microsoft がビルド 2018 で発表した Visual Studio IntelliCode は、AI を利用してソフトウェア開発を強化する新しい機能です。 IntelliCode を利用すると、開発者や開発チームは自信を持ってコードを記述し、問題を早期発見し、重要な領域に焦点を合わせてコードをレビューできます。

IntelliCode がいかにしてソフトウェア開発プロセスを強化するのか、そのしくみを先行公開しました。次の点で強化されます。

- 文脈に合わせてコードの入力候補を示す
- チームのパターンやスタイルに準拠するように開発者を導く
- 見つけにくいコード問題を見つける
- コード レビューの焦点を本当に重要な領域に向ける

開発者は [https://aka.ms/intellicode](https://aka.ms/intellicode) で他の情報を見つけたり、新規登録してニュースや今後のプライベート プレビューを購読したりできます。

## Q. Visual Studio IntelliCode でお客様は何ができるようになりますか?

Visual Studio IntelliCode は一連の機能から構成され、人工知能 (AI) を利用して新しい生産性を作り出します。

開発者は、Visual Studio 2017 バージョン 15.7 以降の[試験的拡張機能をダウンロード](https://go.microsoft.com/fwlink/?linkid=872707)できます。 現在、次の拡張機能が提供されています。

- AI で強化された IntelliSense は、API の一覧をアルファベット順に提示するのではなく、開発者にとってそれを使うことが正解となる可能性が最も高い API を予測します。 開発者が現在記述しているコードの文脈とパターンを使用し、この一覧を動的に提供します。

- コード スタイルおよびフォーマット規則の推論では、コーディング スタイルとフォーマットを定義するコードベースから [.editorconfig ファイル](../create-portable-custom-editor-options.md)を動的に作成することによって、コードの整合性を維持できるようにします。 これらの規則により、Visual Studio では、ドキュメントをクリーンアップするための、スタイルとフォーマットの自動修正を提供することができます。

今後の数か月で、この拡張をアップデートし、さらに機能を増やす予定です。

## Q. EditorConfig 推論によってファイル名の先頭に 1 が追加されるのはどうしてですか?

Visual Studio 拡張機能の既知の問題に原因があります。 右クリックしてから、**[追加]、[新しい項目]** の順に選択して .editorconfig を作成すると、ファイル名の先頭に 1 が追加されます。 このようにして名前が付けられたファイルは、Visual Studio の editorconfig プロセッサによって認識されません。 この問題は Visual Studio 2017 バージョン 15.8 Preview 4 で修正されますが、それまでは、**[新しい項目の追加]** ダイアログで 1 を削除することができます。

## Q. EditorConfig 規則が有効になっているかどうかを確認できません。どうしてですか?
この問題は、いくつかの一般的な理由により、発生する可能性があります。

- 15.8 Preview 3 よりも前の Visual Studio 2017 のバージョンで、作成した EditorConfig ファイル内の規則が有効になっているかを確認するには、開いているすべてのドキュメントを閉じてから再度開く必要があります。 この問題は 15.8 Preview 3 のリリースで修正されます。
- フォーマット規則は、**エラー一覧**に表示されることもなければ、コード内に "波線" としても表示されることもありません。 ただし、Visual Studio 2017 のバージョン 15.8 Preview 3 以降では、[ドキュメントのフォーマット] の新しい拡張機能 (Ctrl + K、Ctrl + D) を使用してフォーマット規則を修正することができます。

## Q. [ドキュメントのフォーマット] によってスタイル規則が修正されないのはどうしてですか?
この問題は、いくつかの一般的な理由により、発生する可能性があります。

- Visual Studio 2017 バージョン 15.8 Preview 3 以降を使用していないことが考えられます。 拡張された [ドキュメントのフォーマット] コマンドを使用して現在のドキュメントに対する追加のコード クリーンアップを実行するには、このバージョンが必要です。
- スタイルの修正に対してオプトインされていない可能性があります。 [ドキュメントのフォーマット] の拡張機能である、規則に基づく機能を修正する機能では、修正対象の問題のみが処理されます。 修正する問題を変更するには、**[テキスト エディター]、[C#]、[コード スタイル]、[フォーマット]、[全般]、[ドキュメントのフォーマット設定 (試験的)]** の順に進み、さらに、**[ツール]、[オプション]** の順に進みます。 既定の設定では、一部のスタイル規則が修正されないので注意してください。 これらにオプトインするには、**[ツール] > [オプション]** を使用します。 たとえば、"暗黙的/明示的な型の初期設定の適用" では、`var` の使用に関するスタイル ルールが実行されます。

## Q. Visual Studio IntelliCode で推論できる EditorConfig 規則はどれですか?

現時点でこの機能は実験段階にあります。したがって、[コード スタイル設定のリファレンス](../editorconfig-code-style-settings-reference.md)に記載されているフルセットの規則をサポートしているわけではありません。

現在、IntelliCode では次の規則を推論できます。

フォーマット規則:

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

表記規則
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## Q. Visual Studio IntelliCode 拡張機能に追加される予定の機能は他にもありますか?

Microsoft では、利用可能になり次第、公開して共有することを楽しみにしている多数の機能に積極的に取り組んでいます。 公開された新機能を真っ先にお知りになりたい場合は、ニュースと更新プログラムを [https://aka.ms/intellicode](https://aka.ms/intellicode) でサインアップしてください。

## Q: IntelliCode が動力となる “AI 支援 IntelliSense” が通常の IntelliSense より優れているのはなぜですか?

IntelliCode の入力候補一覧では、API の一覧を単純にアルファベット順で提示するのではなく、開発者にとってそれを使うことが正解となる可能性が最も高い API を提案します。 この動的一覧には開発者が現在記述しているコードの文脈とパターンが利用されますが、その基盤となるのが GitHub に存在する、100 個以上の星が付いた 2,000 件の高品質なオープンソース プロジェクトです。 結果的に、最も関連性があり、最も適切な API 呼び出しを予測するモデルが作られます。

## Q: IntelliCode の入力候補はどれくらい優れていますか?

IntelliCode のおすすめ候補を Microsoft 内部で使用していますが、この入力候補が非常に役に立っています。 しかし、最終的には、実際にコーディングでお使いいただくことで、このおすすめ候補が非常に便利であることを実感していただけるでしょう。 ぜひ、Visual Studio の [IntelliCode 拡張機能](https://go.microsoft.com/fwlink/?linkid=872707)をお試しください。 お使いになった感想をフィードバックでお送りください。 おすすめ候補の選択内容に基づいたモデルのトレーニングも行っています。モデルの改善に応じて拡張機能も更新していきます。

> [!NOTE]
> ユーザー定義のコードが収集されることはありません。 [プライバシー](#privacy)に関する質問を参照してください。

## Q. IntelliCode は今後どうなりますか?

Microsoft は、AI やその他の最新技術を利用して開発者の生産性を上げるさまざまな手法を模索しています。 Microsoft ビルド 2018 では、AI が開発者を支援するシナリオの一部を先行公開しましたが、シナリオはそれだけではありません。 Microsoft はこれまでに提示した機能を実際に試してみた開発者の意見に興味があります。[https://aka.ms/intellicode](https://aka.ms/intellicode) で新規登録し、ニュースやアップデートを定期購読してください。

## Q. いくらになりますか?

現在のところ、価格設定に関しては告知していません。

## Q. IntelliCode はいつリリースされますか?

IntelliCode の AI 支援 IntelliSense は現在、最初の試験的プレビュー段階にあります。 今後も試験的拡張機能をアップデートし、機能をさらに追加する予定です。 最終リリースに関する予定はございませんが、開発者からのフィードバックは歓迎しております。可能な限り便利な機能を提供するために、フィードバックを活用しております。 [https://aka.ms/intellicode](https://aka.ms/intellicode) で新規登録し、ニュースやアップデートを定期購読できます。

## Q. この機能は Visual Studio と C# 以外では利用できませんか?

この機能は C# コードベースの Visual Studio 2017 のビルド 2018 で公開されましたが、 将来的には Visual Studio 製品群の他のツールにも IntelliCode を導入できればと、また、利用できる言語が増えればと考えております。

## Q. <a name="whynointellisense"/> C# を編集しているときに IntelliCode の候補が表示されません。どうしてでしょうか?

IntelliCode の候補は、標準の Visual Studio IntelliSense UI で C# を使用しているときに表示されます。 その UI をオーバーライドする拡張機能を使用している場合、一覧の上部に IntelliCode の "星印付きの" の候補は表示されません。 この動作の原因が拡張機能であるかどうかを確認するには、IntelliSense をオフにしてから再度オンにしてください。

これで問題を解決できない場合、Visual Studio の[問題を報告する](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)機能を使用して問題を報告してください。レポートには IntelliCode を含めてください。

## Q. この拡張機能を実行するには、どのリリースの Visual Studio が必要ですか?

Visual Studio IntelliCode 拡張機能は、Visual Studio 2017 バージョン 15.7 Preview 5 以降 (すべての SKU) でサポートされています。 最低限必要なバージョンがインストールされていない場合に拡張機能をインストールすると、"この拡張機能は、現在インストール済みの製品にはインストールできません。" という メッセージにより終了します。

## Q. この機能は英語以外では利用できませんか?

現在、IntelliCode はプレビューの拡張機能であり、幅広いお客様にこの便利な機能をご理解いただきたいと考えています。 IntelliCode のプレビューが終了したら、フィードバックに基づき、最初にサポートするロケールや言語、パッケージ化の方法について検討いたします。

## <a name="privacy"/> Q: プライバシーについてはどうですか? 開発者のコードをクラウドに送信しますか? どのような顧客データが Microsoft に送信されますか?

現在のところ、開発者には Visual Studio IntelliCode の試験的プレビュー拡張をお試しいただいています。 この拡張の目的は、開発者が IntelliCode の機能をテストし、製品チームにフィードバックを提供できるようにすることにあります。

Microsoft は、製品を改善する目的で、この拡張から一部の利用状況データやエラー報告データを匿名化した上で入手しています。 ユーザー定義のコードが Microsoft に送信されることはありませんが、IntelliCode が提示した結果を開発者がどのように利用しているかについて、Microsoft はデータを取得しています。 そのデータには、オープンソース型、.NET 型、IntelliCode が提案した一覧から開発者が選択した入力候補のみが含まれます。 開発者は [Visual Studio エクスペリエンス向上プログラム](../../ide/visual-studio-experience-improvement-program.md)を無効にできます。その場合、IntelliCode 拡張機能のデータ収集も無効になります。 メニュー バーで、**[ヘルプ]**、**[フィードバックの送信]**、**[設定]** の順に選択します。 **[Visual Studio エクスペリエンス向上プログラム]** ダイアログで **[いいえ、参加しません]** を選択し、**[OK]** を選択します。

IntelliCode 拡張では、アンケートの記入を開発者に定期的に依頼することがあります。これもまた、匿名化されます。 ユーザーは新規登録し、ニュースや今後のプライベート プレビューを定期購読できますが、現在のところ、登録しなくても試験的拡張をご利用いただけます。

今後、機能によっては、新規登録が必要なサービスへのアクセスが必要になる場合があります。 そのような機能がプライベート プレビューで利用できるようになった場合、Microsoft は詳細を公開します。
