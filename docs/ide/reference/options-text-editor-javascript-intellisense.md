---
title: '[オプション]、[テキスト エディター]、[JavaScript]、[IntelliSense]'
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fad8ba4b41768246fcd14bd6c3aed8b31c1647b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927675"
---
# <a name="options-text-editor-javascript-intellisense"></a>[オプション]、[テキスト エディター]、[JavaScript]、[IntelliSense]
JavaScript での IntelliSense の動作設定を変更するには、 **[オプション]** ダイアログ ボックスの **[IntelliSense]** ページを使用します。 **[IntelliSense]** ページにアクセスするには、メニュー バーの **[ツール]** > **[オプション]** を選択し、**[テキスト エディター]** > **[JavaScript]** > **[IntelliSense]** の順に展開します。

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**[IntelliSense]** ページには、以下のセクションがあります。

## <a name="statement-completion"></a>[入力候補]
 これらのオプションを使用して、IntelliSense のステートメントの入力候補の動作を変更できます。

### <a name="uielement-list"></a>UIElement の一覧
 **[Tab キーと Enter キーのみをコミットに使用する]**

 このチェック ボックスをオンにすると、**Tab** または **Enter** キーを押した後でのみ、JavaScript コード エディターによって入力候補一覧で選択された項目を含むステートメントが追加されます。 このチェック ボックスをオフにすると、ピリオド、コンマ、コロン、左かっこ、左中かっこ ({) など、その他の文字でも選択された項目を含むステートメントを追加できます。

## <a name="references"></a>参照
 これらのオプションを使用して、JavaScript のさまざまなプロジェクトの種類のスコープ内にある IntelliSense (.js) ファイルの種類を指定できます。 通常、IntelliSense 参照は、グローバル オブジェクトに IntelliSense サポートを提供するために使用されます。 このページを使用して、実行時に読み込む必要があるスクリプトの読み込み順序を設定したり、IntelliSense の拡張ファイルを追加したりすることもできます。

### <a name="uielement-list"></a>UIElement の一覧
 **[参照グループ]**

 このオプションで、参照グループの種類を指定します。 3 つの参照グループがサポートされています。

 定義済みの参照グループを使用して、特定の IntelliSense (.js) ファイルがさまざまな JavaScript プロジェクトのスコープ内にあることを指定できます。 4 つの参照グループを使用できます。

- 暗黙 (Windows *バージョン*)、JavaScript を使用する [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] アプリケーション用。 このグループに含まれるファイルは、JavaScript を使用する [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] アプリケーションのコード エディターで開かれる、すべての .js ファイルのスコープ内にあります。

- 暗黙 (Web)、HTML5 プロジェクト用。 このグループに含まれるファイルは、これらのプロジェクト タイプのコード エディターで開かれる、すべての .js ファイルのスコープ内にあります。

- 専用のワーカーの参照グループ、HTML5 Web ワーカー用。 このグループで指定されたファイルは、専用のワーカーの参照グループへの明示的な参照がある .js ファイルのスコープ内にあります。

- ジェネリック、他の JavaScript プロジェクト タイプ用。

**[インクルード ファイル]**

このオプションで、ファイルが言語サービスのコンテキストに読み込まれる順序を指定します。 **[削除]**、 **[上へ移動]**、および **[下へ移動]** ボタンを使用して順序を構成できます。 IntelliSense が正しく動作するためには、別のファイルに依存しているファイルはその別のファイルの後に読み込む必要があります。

> [!CAUTION]
> オブジェクトが複数の暗黙的な参照で無条件で定義されている場合、その一覧内の最後の参照を使用してオブジェクトが定義されます。


**[Add a reference to the group] (グループへの参照の追加)**

このオプションを使用すると、適切なファイルを参照して IntelliSense (.js) ファイルを追加できます。

**[その他のファイル プロジェクト内のファイルのリモート参照 (http:// など) をダウンロードする]**

このチェック ボックスをオンにすると、プロジェクトのコンテキストの外部で開かれる JavaScript ファイルがある場合、IntelliSense の情報を提供するために、Visual Studio によってそのファイルで参照されているリモート JavaScript ファイルがダウンロードされます。 このオプションを選択している場合、JavaScript ファイルに参照として含まれるファイルがダウンロードされます。

> [!NOTE]
> Web プロジェクトでは、プロジェクトで参照されるリモート ファイルは既定でダウンロードされます。



## <a name="see-also"></a>「

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)