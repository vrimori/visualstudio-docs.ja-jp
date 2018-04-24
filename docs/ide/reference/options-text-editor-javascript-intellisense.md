---
title: '[オプション]、[テキスト エディター]、[JavaScript]、[IntelliSense] | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe387287b9b46e6fdd2972ce1a3f77e4f5349414
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-javascript-intellisense"></a>[オプション]、[テキスト エディター]、[JavaScript]、[IntelliSense]
JavaScript での IntelliSense の動作設定を変更するには、 **[オプション]** ダイアログ ボックスの **[IntelliSense]** ページを使用します。 **[IntelliSense]** ページにアクセスするには、メニュー バーの **[ツール]**, **[オプション]** をクリックし、 **[テキスト エディター]**, **[JavaScript]**, **[IntelliSense].** と展開します。  
  
[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
**[IntelliSense]** ページには、以下のセクションがあります。  
  
## <a name="validation"></a>検証  
 これらの設定を使用して、JavaScript エディターがドキュメントの構文を検証する方法を設定できます。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **[構文エラーの表示]**  
 このチェック ボックスをオフにすると、JavaScript エディターに構文エラーが表示されなくなります。 このオプションは、自分が記述したものではなく、構文エラーを修正する必要がないコードを扱うときに便利です。  
  
 このチェック ボックスをオンにすると、 **[エラーを警告として表示]** チェック ボックスをオンにできるようになります。  
  
 **[エラーを警告として表示]**  
 このチェック ボックスをオンにすると、JavaScript のエラーがエラー一覧ウィンドウにエラーではなく警告として表示されます。  
  
 **[その他のファイル プロジェクト内のファイルのリモート参照 (http:// など) をダウンロードする]**  
 このチェック ボックスをオンにすると、プロジェクトのコンテキストの外部で開かれる JavaScript ファイルがある場合、IntelliSense の情報を提供するために、Visual Studio によってそのファイルで参照されているリモート JavaScript ファイルがダウンロードされます。 このオプションを選択している場合、JavaScript ファイルに参照として含まれるファイルがダウンロードされます。  
  
> [!NOTE]
>  Web プロジェクトでは、プロジェクトで参照されるリモート ファイルは既定でダウンロードされます。  
  
## <a name="statement-completion"></a>[入力候補]  
 これらのオプションを使用して、IntelliSense のステートメントの入力候補の動作を変更できます。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **[Tab キーと Enter キーのみをコミットに使用する]**  
 このチェック ボックスをオンにすると、Tab または Enter キーを選択した後にのみ、JavaScript コード エディターによって入力候補一覧で選択された項目を含むステートメントが追加されます。 このチェック ボックスがオフの場合、ピリオド、コンマ、コロン、始めかっこ、始め中かっこ ({) など、その他の文字でも選択された項目を含むステートメントを追加できます。  
  
## <a name="references"></a>参照  
 これらのオプションを使用して、JavaScript のさまざまなプロジェクトの種類のスコープ内にある IntelliSense (.js) ファイルの種類を指定できます。 通常、IntelliSense 参照は、グローバル オブジェクトに IntelliSense サポートを提供するために使用されます。 このページを使用して、実行時に読み込む必要があるスクリプトの読み込み順序を設定したり、IntelliSense の拡張ファイルを追加したりすることもできます。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **[参照グループ]**  
 このオプションで、参照グループの種類を指定します。 3 つの参照グループがサポートされています。  
  
 定義済みの参照グループを使用して、特定の IntelliSense (.js) ファイルがさまざまな JavaScript プロジェクトのスコープ内にあることを指定できます。 4 つの参照グループを使用できます。  
  
-   暗黙 (Windows *バージョン*)、JavaScript を使用する [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] アプリケーション用。 このグループに含まれるファイルは、JavaScript を使用する [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] アプリケーションのコード エディターで開かれる、すべての .js ファイルのスコープ内にあります。  
  
-   暗黙 (Web)、HTML5 プロジェクト用。 このグループに含まれるファイルは、これらのプロジェクト タイプのコード エディターで開かれる、すべての .js ファイルのスコープ内にあります。  
  
-   専用のワーカーの参照グループ、HTML5 Web ワーカー用。 このグループで指定されたファイルは、専用のワーカーの参照グループへの明示的な参照がある .js ファイルのスコープ内にあります。  
  
-   ジェネリック、他の JavaScript プロジェクト タイプ用。  
  
**[インクルード ファイル]**  
このオプションで、ファイルが言語サービスのコンテキストに読み込まれる順序を指定します。 **[削除]**、 **[上へ移動]**、および **[下へ移動]** ボタンを使用して順序を構成できます。 IntelliSense が正しく動作するためには、別のファイルに依存しているファイルはその別のファイルの後に読み込む必要があります。  
  
> [!CAUTION]
>  オブジェクトが複数の暗黙的な参照で無条件で定義されている場合、その一覧内の最後の参照を使用してオブジェクトが定義されます。  
  
**[Add a reference to the group] (グループへの参照の追加)**  
このオプションを使用すると、適切なファイルを参照して IntelliSense (.js) ファイルを追加できます。  
  
## <a name="see-also"></a>参照  
[JavaScript IntelliSense](../../ide/javascript-intellisense.md)