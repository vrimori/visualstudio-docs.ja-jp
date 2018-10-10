---
title: JavaScript IntelliSense の拡張 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 59189ae35ce43877e59309382dfd9cbf278ce8f0
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881125"
---
# <a name="extending-javascript-intellisense"></a>JavaScript IntelliSense の拡張
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](/visualstudio/)します。  
  
JavaScript IntelliSense の拡張機能では、サードパーティ製のライブラリの JavaScript エディターで IntelliSense の結果をカスタマイズすることができます。 これにより、これらのライブラリを使用する開発者のエクスペリエンスが向上することができます。  
  
 JavaScript language service は、プロジェクトに追加されるサードパーティ製の JavaScript ライブラリの IntelliSense 機能を提供します。 ほとんどのライブラリには、言語サービスで、ステートメント入力候補が自動的に提供します。 次の図は、ステートメント入力候補の例を示します。  
  
 ![ステートメント入力候補の例](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 ライブラリでは、標準の JavaScript コメント タグで変数、関数、およびオブジェクトの説明が含まれている場合 (または/)、既定では、ポップアップ ボックスにわかりやすい情報を提供する IntelliSense 拡張機能から、自動的に利用します。入力候補一覧、または関数呼び出しにかっこを入力すると要素の右側に表示されます。 ポップアップ ボックス内のコメントには、メンバーの説明が含まれています。 次の例では、入力候補一覧のポップアップ ボックスを表示します。  
  
 ![クイック ヒント ポップアップの例&#45;ボックス](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 開発者エクスペリエンスをさらに強化するには、ポップアップ ボックスで開発者に型情報を提供する可能性があります。 JavaScript を使用して型情報を提供できます[XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)の標準のコメント用タグの代わりにします。 XML ドキュメントのコメントを追加するには、トリプル スラッシュ コメント タグ (///) と定義された一連の XML 要素を使用します。  
  
 また、JavaScript IntelliSense の機能拡張を使用して型情報を提供できます。 この機能では、JavaScript の拡張機能の作成と、スクリプトのコンテキストに追加することによって IntelliSense の結果をカスタマイズすることができます。 によって公開されているイベントにサブスクライブする JavaScript ファイルには、拡張機能で、`intellisense`言語サービスのオブジェクト。 場合、宣言型 XML の代替とライブラリの動作パターンが原因で、JavaScript 言語サービスが、必要なレベルの IntelliSense のサポートを提供する場合、JavaScript IntelliSense の機能拡張は、ライブラリに推奨されるソリューションドキュメントのコメントも必要です。 IntelliSense の結果をカスタマイズすることで、言語サービスの既定の機能を妨げる可能性のある動作パターンに関係なく、最上級の IntelliSense エクスペリエンスを作成できます。 詳細については、次を参照してください。[識別子の入力候補](../ide/statement-completion-for-identifiers.md)します。  
  
## <a name="adding-an-extension-to-the-script-context"></a>スクリプト コンテキストへの拡張機能の追加  
 実行される IntelliSense の拡張機能、現在のスクリプト コンテキストに追加するが必要です。 拡張機能に自動的に追加できるスクリプトのコンテキスト、自動検出メカニズムによってまたはできる拡張機能のスクリプト コンテキストに手動で追加する参照グループまたは reference ディレクティブを使用しています。  
  
 自動検出メカニズムにより、ファイルの名前付け規則に準拠する拡張機能を自動的に検出する言語サービス*libraryname*intellisense.js、、がライブラリと同じディレクトリ内にある。拡張機能が適用されます。 たとえば、jQuery ライブラリの有効な拡張子は jQuery.intellisense.js になります。 制限の厳しい jQuery の拡張機能、jQuery 1.7.1.intellisense.js (バージョン固有の拡張機能) または jQuery.ui.intellisense.js (スコープを持つ jQuery ライブラリの拡張機能) などのファイル名を使用できます。 拡張機能の最も制限の厳しいバージョンは、指定したライブラリの 1 つ以上の拡張機能が検出された場合に使用されます。  
  
 すべての JavaScript プロジェクト ファイルの拡張機能を使用する場合は、参照グループに、拡張機能を追加するように選択可能性があります。 複数の種類のいずれかが含まれている暗黙の参照と専用のワーカーの参照が含まれている、参照グループがあります。 拡張機能を追加するには、通常、暗黙の参照グループとしてか、ファイルを追加する必要が**暗黙 (Windows)**、**暗黙 (Web)** します。 暗黙的な参照は、コード エディターで開かれるすべての .js ファイルのスコープになります。 このメソッドを使用する場合は、拡張機能と拡張機能を補完するファイルの両方を追加する必要があります。  
  
 使用して、 **IntelliSense**のページ、**オプション**参照グループとして拡張機能を追加する ダイアログ ボックス。 アクセスできる、 **IntelliSense**を選択してページ**ツール**、**オプション**メニュー バー、およびクリックした後で**テキスト エディター**、 **JavaScript**、 **IntelliSense**、**参照**します。 参照グループの詳細については、次を参照してください。 [JavaScript IntelliSense](../ide/javascript-intellisense.md)と[、オプション、テキスト エディター、JavaScript IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)します。  
  
 特定の一連のファイルの拡張機能を使用する場合は、参照ディレクティブを使用します。 このメソッドを使用する場合は、拡張機能と拡張機能を補うため、ファイルの両方を参照する必要があります。 参照ディレクティブの使用方法の詳細については、次を参照してください。 [JavaScript IntelliSense](../ide/javascript-intellisense.md)します。  
  
## <a name="handling-intellisense-events"></a>IntelliSense のイベントの処理  
 拡張機能などのイベントにサブスクライブすることによって IntelliSense の結果をカスタマイズすることができます、`statementcompletion`言語サービスのイベント`intellisense`オブジェクト。 次の例では、ステートメント入力候補からアンダー スコアで始まるメンバーを非表示にする、言語サービスで使用される単純な拡張機能を示します。 このコードは underscorefilter.js に含まれているし、では、 \\ \\ *Visual Studio インストール パス*\JavaScript\References フォルダー。  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 上記のコードでは、拡張機能を確認します、 [targetName プロパティ](#TargetName)と[対象になるプロパティ](#Target)のプロパティ、`statementcompletion`などのオブジェクトを除外するイベント オブジェクト`this`と`window`、し、有効なステートメント入力候補一覧が識別されることを確認します。 入力候補一覧が識別できる場合、拡張機能の更新ステートメント入力候補[項目のプロパティ](#Items)アンダー スコアで始まるメンバーが除外されるコレクション。  
  
 その他の例では、検索、 \\ \\ *Visual Studio インストール パス*\JavaScript\References フォルダー。 このフォルダーに showPlainComments.js ファイルは、標準の JavaScript コメント タグの既定の IntelliSense サポートを提供するその他のイベントを使用しての例を示します (//)。 Underscorefilter.js のような showPlainComments.js 既に作業の拡張機能として利用可能な変数、関数、およびオブジェクトをコード内のコメント用タグを使用する場合は、IntelliSense の結果として得られる情報を確認できます。 その他の例では、次を参照してください。[コード例](#CodeExamples)します。  
  
> [!WARNING]
>  Visual Studio に含まれている拡張機能のファイルを変更する場合、JavaScript IntelliSense や、拡張機能でサポートされている機能を無効にする可能性があります。  
  
 使用して、次のイベントの種類のハンドラーを作成する、拡張機能コードで`addEventListener`:  
  
-   `statementcompletion`、ステートメントの完了イベントのハンドラーを追加します。 ステートメント入力候補は、入力中、または ctrl キーを押しながら j. を押したときに表示される識別子の一覧またはピリオド (.) などの特殊文字を入力した後に表示される特定の型のメンバーの一覧を提供します。ハンドラーが型のイベント オブジェクトを受け取る`CompletionEvent`、次のメンバーをサポートしています:[項目のプロパティ](#Items)、[対象になるプロパティ](#Target)、 [targetName プロパティ](#TargetName)、[スコープ プロパティ](#Scope)します。  
  
-   `signaturehelp`、パラメーターの IntelliSense のヒントのハンドラーを追加します。 パラメーター情報は、数、名前、および関数に必要なパラメーターの型に関する情報を提供します。 ハンドラーが型のイベント オブジェクトを受け取る`SignatureHelpEvent`、次のメンバーをサポートしています:[対象になるプロパティ](#Target)、 [parentObject プロパティ](#ParentObject)、 [functionCommentsプロパティ](#FunctionComments)、 [functionHelp プロパティ](#FunctionHelp)します。  
  
-   `statementcompletionhint`、IntelliSense によるクイック ヒントのハンドラーを追加します。 クイック ヒント ポップアップ ボックスでは、コード内の識別子に関する完全な宣言を示します。 ハンドラーが型のイベント オブジェクトを受け取る`CompletionHintEvent`、次のメンバーをサポートしています: [completionItem プロパティ](#CompletionItem)、および[symbolHelp プロパティ](#SymbolHelp)します。  
  
 ステートメント入力候補、パラメーター情報、およびクイック ヒントなどの IntelliSense 機能を示す例については、次を参照してください。[を使用して IntelliSense](../ide/using-intellisense.md)します。  
  
> [!NOTE]
>  JavaScript では、クイック ヒントは、入力候補一覧の右側に表示されるポップアップ ボックスを参照します。 クイック ヒントを手動で起動することはできません。  
  
##  <a name="intellisenseObject"></a> intellisense オブジェクト  
 次の表に、使用可能な関数、`intellisense`オブジェクト。 `intellisense`オブジェクトは、デザイン時にのみ使用します。  
  
|関数|説明|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|IntelliSense のイベントのイベント ハンドラーを追加します。<br /><br /> `type` 文字列値です。 有効な値は`statementcompletion`、 `signaturehelp`、および`statementcompletionhint`します。<br /><br /> `handler` 次の種類のいずれかのイベント オブジェクトを受信するイベント ハンドラー関数。<br /><br /> -   `CompletionEvent`で使用される、`statementcompletion`イベント。<br />-   `SignatureHelpEvent`で使用される、`signaturehelp`イベント。<br />-   `CompletionHintEvent`で使用される、`statementcompletionhint`イベント。<br /><br /> この関数を使用する例については、次を参照してください。[コード例](#CodeExamples)します。|  
|`annotate(obj, doc);`|オブジェクトのドキュメントを指定するには、ドキュメントのコメントを 1 つのオブジェクトから別のオブジェクトにコピーします。<br /><br /> `obj` ドキュメントのコピー先となるオブジェクトを指定します。<br /><br /> `doc` ドキュメントのコピー元のオブジェクトを指定します。<br /><br /> この関数を使用する方法を示しますたとえば、次を参照してください。 [IntelliSense 注釈の追加](#Annotations)します。|  
|`getFunctionComments(func);`|指定された関数は、コメントを返します。<br /><br /> `func` コメントが返される関数を指定します。<br /><br /> 設定することができます、`func`パラメーターを使用して`completionItem.value`します。<br /><br /> 返された`functionComments`オブジェクトには、次のメンバーが含まれています: `above`、 `inside`、および`paramComment`します。 詳細については、次を参照してください。、 [functionComments プロパティ](#FunctionComments)プロパティ。<br /><br /> `getFunctionComments` 内で登録されているイベント ハンドラーのいずれかからのみ呼び出すことが`addEventListener`します。<br /><br /> この関数を使用する方法を示しますたとえば、次を参照してください。 \\ \\ *Visual Studio インストール パス*\JavaScript\References\showPlainComments.js します。|  
|`logMessage(msg);`|出力ウィンドウには、診断メッセージを送信します。<br /><br /> `msg` メッセージを含む文字列です。<br /><br /> この関数を使用する方法を示しますたとえば、次を参照してください。[出力ウィンドウにメッセージを送信する](#Logging)します。|  
|`nullWithCompletionsOf(value);`|コンプリート リストは 渡されたオブジェクトによって決まります特別な null 値を返します、`value`パラメーター。<br /><br /> `value` 返される値の入力候補一覧を決定します。 `value` 任意の型を指定できます。<br /><br /> Null の戻り値はデザイン時に、null として扱われますが、戻り値の入力候補一覧は、入力候補一覧と同じ、`value`パラメーター。<br /><br /> この関数の用途の 1 つは、戻り値の型は、実行時に予測可能な場合、戻り値は、戻り値に対して IntelliSense を提供する`null`デザイン時にします。|  
|`redirectDefinition(func, definition);`|IntelliSense パラメーター ヘルプときに、元の func 関数の代わりに、指定された定義の関数を使用するように指示または**定義へ移動**を要求します。<br /><br /> `func` 対象の関数を指定します。<br /><br /> `definition` パラメーターは、対象の関数の代わりに使用する関数を指定し、**定義へ移動**します。|  
|`setCallContext(func, thisArg);`|呼び出しコンテキスト、または指定された関数のスコープを設定します。<br /><br /> `func` スコープを設定する対象の関数を指定します。<br /><br /> `thisArg` オブジェクトをリテラルにするには、`this`キーワードを参照できるメンバーの新しいスコープを指定します。 たとえば、このパラメーターに渡す引数を含めることができます。 `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` 似た動作を提供します。`Function.prototype.bind`デザイン時の IntelliSense サポートに対してのみに使用される点を除き、します。 使用することができます`setCallContext`関数を呼び出すことができるようにしない場合は到達可能であるコードの呼び出しをシミュレートする必要がある場合は、関数のスコープを設定するに正しいスコープと引数、関数呼び出しが含まれます。|  
|`undefinedWithCompletionsOf(value);`|コンプリート リストは渡されたオブジェクトによって決まりますが、特別な未定義の値を返します、`value`パラメーター。<br /><br /> `value` 返される値の入力候補一覧を決定します。 `value` 任意の型を指定できます。<br /><br /> 値が扱われます、undefined を返すがデザイン時に、完了時に undefined として戻り値の一覧は、入力候補一覧と同じ、`value`パラメーター。<br /><br /> この関数の 1 つの用途は、戻り値の型は、実行時に予測可能な戻り値は、デザイン時に定義されているがない場合、戻り値の IntelliSense を提供します。|  
|`version()`|Visual Studio のバージョンを返します。|  
  
## <a name="event-members"></a>イベント メンバー  
 次のセクションでは、次のイベントのイベント オブジェクトで公開されるメンバーを示しています。: `statementcompletion`、 `signaturehelp`、および`statementcompletionhint`します。  
  
###  <a name="CompletionItem"></a> completionItem プロパティ  
 クイック ヒント ポップアップ ボックスが要求される、入力候補アイテムと呼ばれる識別子を返します。 このプロパティは使用できます、`statementcompletionhint`イベント オブジェクトと、[項目のプロパティ](#Items)のプロパティ、`statementcompletion`イベント オブジェクト。  
  
 戻り値:`completionItem`オブジェクト  
  
 メンバーを次に、`completionItem`オブジェクト。  
  
-   `name`。 読み取り/書き込みで使用すると、`items`コレクション。 それ以外の場合、読み取り専用です。 入力候補アイテムを識別する文字列を返します。  
  
-   `kind`。 読み取り/書き込みで使用すると、`items`コレクション。 それ以外の場合、読み取り専用です。 入力候補アイテムの型を表す文字列を返します。 使用可能な値は、メソッド、フィールド、プロパティ、パラメーター、変数とに予約されています。  
  
-   `glyph`。 読み取り/書き込みで使用すると、`items`コレクション。 それ以外の場合、読み取り専用です。 入力候補一覧に表示されるアイコンを表す文字列を返します。 使用可能な値を`glyph`、次の形式を使用して: vs:*glyphType*ここで、 *glyphType*で言語に依存しないメンバーに対応して、<xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>列挙体。 たとえば、`vs:GlyphGroupMethod`に対して 1 つの可能な値は、`glyph`します。 ときに`glyph`が設定されていない、`kind`プロパティの既定のアイコンを決定します。  
  
-   `parentObject`。 読み取り専用。 親オブジェクトを返します。  
  
-   `value`。 読み取り専用。 入力候補アイテムの値を表すオブジェクトを返します。  
  
-   `comments`。 読み取り専用。 フィールドまたは変数のより上位にあるコメントを含む文字列を返します。  
  
-   `scope`。 読み取り専用。 入力候補アイテムのスコープを返します。 可能な値は、グローバル、ローカル、パラメーターおよびメンバーです。  
  
###  <a name="Items"></a> 項目のプロパティ  
 取得またはステートメントの配列の入力候補の項目を設定します。 配列内の各要素は、 [completionItem プロパティ](#CompletionItem)オブジェクト。 `items`プロパティは使用できます、`statementcompletion`イベント オブジェクト。  
  
 戻り値: 配列  
  
###  <a name="FunctionComments"></a> functionComments プロパティ  
 関数は、コメントを返します。 このプロパティは使用できます、`signaturehelp`イベント オブジェクト。  
  
 戻り値:`comments`オブジェクト  
  
 メンバーを次に、`comments`オブジェクト。  
  
-   `above`。 関数の上にコメントを返します。  
  
-   `inside`。 通常、関数内でコメント VSDoc 形式を返します。  
  
-   `paramComments`。 関数の各パラメーターにコメントを表す配列を返します。 配列のメンバーは次のとおりです。  
  
    -   `name`。 パラメーター名を表す文字列を返します。  
  
    -   `comment`。 パラメーターのコメントを含む文字列を返します。  
  
###  <a name="FunctionHelp"></a> functionHelp プロパティ  
 関数のヘルプを返します。 このプロパティは使用できます、`signaturehelp`イベント オブジェクト。  
  
 戻り値:`functionHelp`オブジェクト  
  
 メンバーを次に、`functionHelp`オブジェクト。  
  
-   `functionName`。 読み取り/書き込み。 関数名を含む文字列を返します。  
  
-   `signatures`。 読み取り/書き込み。 取得または関数のシグネチャの配列を設定します。 配列内の各要素は、`signature`オブジェクト。 いくつか`signature`プロパティなど`locid`、共通に対応して[XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)属性。  
  
     メンバー、`signature`オブジェクトが含まれます。  
  
    -   `description`。 読み取り/書き込み。 機能を説明する文字列を返します。  
  
    -   `locid`。 読み取り/書き込み。 関数に関するローカライズ情報を含む文字列識別子を返します。  
  
    -   `helpKeyword`。 読み取り/書き込み。 ヘルプ キーワードを含む文字列を返します。  
  
    -   `externalFile`。 読み取り/書き込み。 メンバー ID を含むファイルを表す文字列を返します  
  
    -   `externalid`。 読み取り/書き込み。 関数のメンバー ID を表す文字列を返します。  
  
    -   `params`。 読み取り/書き込み。 取得または関数のパラメーターの配列を設定します。 パラメーター配列内の各要素は、`parameter`オブジェクトの次の属性に対応するプロパティを持つ、 [ \<param >](../ide/param-javascript.md)要素。  
  
        -   `name`。 読み取り/書き込み。 パラメーター名を表す文字列を返します。  
  
        -   `type`。 読み取り/書き込み。 パラメーターの型を表す文字列を返します。  
  
        -   `elementType`。 読み取り/書き込み。 型の場合`Array`配列内の要素の型を表す文字列を返します。  
  
        -   `description`。 読み取り/書き込み。 パラメーターを説明する文字列を返します。  
  
        -   `locid`。 読み取り/書き込み。 関数に関するローカライズ情報を含む文字列識別子を返します。  
  
        -   `optional`。 読み取り/書き込み。 パラメーターは省略可能かどうかを示す文字列を返します。 `true` パラメーターが省略可能です。`false`がないことを示します。  
  
    -   `returnValue`。 読み取り/書き込み。 取得または次の属性に対応するプロパティを使用して、戻り値オブジェクトを設定、 [\<返します >](../ide/returns-javascript.md)要素。  
  
        -   `type`。 読み取り/書き込み。 戻り値の型を表す文字列を返します。  
  
        -   `elementType`。 読み取り/書き込み。 型の場合`Array`配列内の要素の型を表す文字列を返します。  
  
        -   `description`。 読み取り/書き込み。 戻り値を記述する文字列を返します。  
  
        -   `locid`。 読み取り/書き込み。 関数に関するローカライズ情報を含む文字列識別子を返します。  
  
        -   `helpKeyword`。 読み取り/書き込み。 ヘルプ キーワードを含む文字列を返します。  
  
        -   `externalFile`。 読み取り/書き込み。 メンバー ID を含むファイルを表す文字列を返します  
  
        -   `externalid`。 読み取り/書き込み。 関数のメンバー ID を表す文字列を返します。  
  
###  <a name="ParentObject"></a> parentObject プロパティ  
 メンバー関数の親オブジェクトを返します。 たとえば、 `document.getElementByID`、`parentObject`を返します、`document`オブジェクト。 このプロパティは使用できます、`signaturehelp`イベント オブジェクト。  
  
 戻り値: オブジェクト  
  
###  <a name="Target"></a> ターゲット プロパティ  
 ピリオド (.) は、トリガーの文字の左側に項目を表すオブジェクトを返します。 関数では、`target`パラメーター情報を要求する対象の関数を返します。 このプロパティは使用できます、`statementcompletion`と`signaturehelp`イベント オブジェクト。  
  
 戻り値: オブジェクト  
  
###  <a name="TargetName"></a> targetName プロパティ  
 ターゲットを表す文字列を返します。 たとえば、"this."、 `targetName` "this"を返します。 "A.B"("B"の後にカーソルがある) 場合の`targetName`"B"を返します。 このプロパティは使用できます、`statementcompletion`イベント オブジェクト。  
  
 戻り値: 文字列  
  
###  <a name="SymbolHelp"></a> symbolHelp プロパティ  
 クイック ヒント ポップアップ ボックスが要求される入力候補の項目を返します。 このプロパティは使用できます、`statementcompletionhint`イベント オブジェクト。  
  
 戻り値:`symbolHelp`オブジェクト。  
  
 一部のプロパティ、`symbolHelp`などオブジェクト`locid`、共通に対応して[XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)属性。  
  
 メンバーを次に、`symbolHelp`オブジェクト。  
  
-   `name`。 読み取り/書き込み。 識別子名を含む文字列を返します。  
  
-   `symbolType`。 読み取り/書き込み。 記号の型を表す文字列を返します。 使用可能な値には、不明なブール値、数値、文字列、オブジェクト、関数、配列、日付、および正規表現が含まれます。  
  
-   `symbolDisplayType`。 読み取り/書き込み。 表示する型名を含む文字列を返します。 場合`symbolDisplayType`設定されていない`symbolType`使用されます。  
  
-   `elementType`。 読み取り/書き込み。 場合、`symbolType`は`Array`配列内の要素の型を表す文字列を返します。  
  
-   `scope`。 読み取り/書き込み。 シンボルのスコープを表す文字列を返します。 使用可能な値には、グローバル、ローカル、パラメーター、およびメンバーが含まれます。  
  
-   `description`。 読み取り/書き込み。 シンボルの説明を含む文字列を返します。  
  
-   `locid`。 読み取り/書き込み。 シンボルに関するローカライズ情報を含む文字列識別子を返します。  
  
-   `helpKeyword`。 読み取り/書き込み。 ヘルプ キーワードを含む文字列を返します。  
  
-   `externalFile`。 読み取り/書き込み。 メンバー ID を含むファイルを表す文字列を返します  
  
-   `externalid`。 読み取り/書き込み。 シンボルのメンバー ID を表す文字列を返します。  
  
-   `functionHelp`。 読み取り/書き込み。 返します、 [functionHelp プロパティ](#FunctionHelp)、情報が含まれているときに、`symbolType`関数は、します。  
  
###  <a name="Scope"></a> スコープ プロパティ  
 イベントの完了スコープを返します。 完了時に使用できる値はグローバルとメンバーをスコープします。 このプロパティは使用できます、`statementcompletion`イベント オブジェクト。  
  
 戻り値: 文字列  
  
## <a name="debugging-intellisense-extensions"></a>IntelliSense の拡張機能のデバッグ  
 拡張機能をデバッグすることはできませんが、使用することができます、 [intellisense オブジェクト](#intellisenseObject)Visual Studio の出力ウィンドウに情報を送信します。 この関数を使用する方法を示しますたとえば、次を参照してください。[出力ウィンドウにメッセージを送信する](#Logging)このトピックで後述します。 `logMessage`の拡張機能でするのには、少なくとも 1 つのイベント ハンドラーを登録する必要があります。  
  
##  <a name="CodeExamples"></a> コード例  
 このセクションには、IntelliSense の機能拡張 Api を使用する方法を示すコード例が含まれています。 これらの Api を使用する他の方法もあります。 その他の例では、次のファイルを参照してください、 \\ \\ *Visual Studio インストール パス*\JavaScript\References フォルダー。 これらは、JavaScript 言語サービスで使用される例を作業しています。  
  
-   underscoreFilter.js します。 このコードでは、IntelliSense からのプライベート メンバーを非表示にします。 イベント ハンドラーが含まれています、`statementcompletion`イベント。  
  
-   showPlainComments.js します。 このコードは、標準のコメントの IntelliSense サポートを提供します。 イベント ハンドラーが含まれています、`signaturehelp`と`statementcompletionhint`イベント。  
  
###  <a name="Annotations"></a> IntelliSense の注釈を追加します。  
 次の手順では、ライブラリを直接変更することがなく、サード パーティ製ライブラリの IntelliSense ドキュメントのサポートを提供する方法を示します。 これを行うには、使用することができます`intellisense.annotate`の拡張機能で。  
  
 この例を実行するには、プロジェクトに次の JavaScript ファイルが必要です。  
  
-   demoLib.js はサード パーティ製ライブラリを表すプロジェクト ファイルです。  
  
-   demoLib.intellisense.js は IntelliSense の拡張機能です。 このファイルは、プロジェクトに含める必要はありませんが、exampleLib.js と同じフォルダーに含める必要があります。  
  
-   appCode.js (アプリケーション コードを表すプロジェクト ファイル)。  
  
##### <a name="to-add-an-intellisense-annotation"></a>IntelliSense 注釈を追加するには  
  
1.  DemoLib.js するには、次のコードを追加します。  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2.  DemoLib.intellisense.js するには、次のコードを追加します。  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3.  次の reference ディレクティブを appCode.js の最初の行として追加します。 ここで使用するパスは、JavaScript ファイルが同じフォルダーにあることを示しています。  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4.  appCode.js で、次のコードを入力します。 パラメーターの IntelliSense のヒントとして表示拡張機能で XML ドキュメントのコメントが表示されます。  
  
     ![Intellisense.annotate の使用例](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5.  appCode.js で、次のコードを入力します。 入力するときに、IntelliSense によるクイック ヒントとして表示拡張機能では、標準のコメントを確認します。  
  
     ![Intellisense.annotate の使用例](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
###  <a name="Logging"></a> 出力ウィンドウにメッセージを送信します。  
 次の手順では、出力ウィンドウにメッセージを送信する方法を示します。 IntelliSense の拡張機能をデバッグする際にメッセージを送信することができます。  
  
 この例を実行するには、プロジェクトに次の JavaScript ファイルが必要です。  
  
-   exampleLib.js はサード パーティ製ライブラリを表すプロジェクト ファイルです。  
  
-   exampleLib.intellisense.js は IntelliSense の拡張機能です。 このファイルは、プロジェクトに含める必要はありませんが、exampleLib.js と同じフォルダーに含める必要があります。  
  
-   appCode.js (アプリケーション コードを表すプロジェクト ファイル)。  
  
##### <a name="to-send-a-message-to-the-output-window"></a>出力ウィンドウにメッセージを送信するには  
  
1.  ExampleLib.js するには、次のコードを追加します。  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2.  ExampleLib.intellisense.js するには、次のコードを追加します。  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3.  次の reference ディレクティブを appCode.js の最初の行として追加します。 ここで使用するパスは、JavaScript ファイルが同じフォルダーにあることを示しています。  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  [出力] ウィンドウで次のように選択します。 **JavaScript Language Service**で、**から出力の表示**一覧。 (出力ウィンドウを表示する選択**出力**表示 メニューから)。  
  
5.  appCode.js で、次のコードを入力します。 入力するときに、出力ウィンドウには、言語サービスからのメッセージが表示されます。 出力ウィンドウの最初のメッセージは、現在のスコープの入力候補が要求されていることを示します。  
  
    ```javascript  
    some  
    ```  
  
     表示される出力の部分的なビューを次に示します。  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6.  選択、**すべてクリア**出力ウィンドウにボタンをクリックします。  
  
7.  次のコードを入力します。 出力ウィンドウの最初のメッセージは、メンバーの一覧が要求されていることを示します。  
  
    ```javascript  
    someVar.  
    ```  
  
     表示される出力の部分的なビューを次に示します。  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
###  <a name="Icons"></a> IntelliSense アイコンを変更します。  
 次の手順では、既定では、IntelliSense によって表示されるアイコンを変更する方法を示します。 名前空間、クラス、インターフェイス、および列挙体などのライブラリに固有な概念についての IntelliSense 情報を提供する場合に便利ですがあります。  
  
 使用可能なアイコンの値を参照してください。<xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>します。  
  
 この例を実行するには、プロジェクトに次の JavaScript ファイルが必要です。  
  
-   exampleLib.js で、プロジェクトは、その represens サード パーティのライブラリをファイルします。  
  
-   exampleLib.intellisense.js は IntelliSense の拡張機能です。 このファイルは、プロジェクトに含める必要はありませんが、exampleLib.js と同じフォルダーに含める必要があります。  
  
-   appCode.js (アプリケーション コードを表すプロジェクト ファイル)。  
  
##### <a name="to-change-the-icons"></a>アイコンを変更するには  
  
1.  ExampleLib.js するには、次のコードを追加します。  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2.  ExampleLib.intellisense.js するには、次のコードを追加します。  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3.  次の reference ディレクティブを appCode.js の最初の行として追加します。 ここで使用するパスは、JavaScript ファイルが同じフォルダーにあることを示しています。  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  appCode.js で、次のコードを入力します。 入力するときに、名前空間のアイコンに変更されたことが表示されます"{}"、c# で使用されているためです。  
  
     ![グリフのプロパティの使用例](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5.  appCode.js で、次のコードを入力します。 入力するときに、Enum1 メンバー用の新しい列挙アイコンと SomeClass1 メンバーのクラスの新しいアイコンが表示されます。  
  
     ![グリフのプロパティの使用例](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
###  <a name="Overriding"></a> IntelliSense の結果に対する実行時の影響を回避します。  
 JavaScript 言語サービスでは、動的に IntelliSense の情報を提供するコードを実行します。 その結果、実行時の動作が場合によっては干渉を目的の結果。 次の手順では、不適切な IntelliSense、実行時の動作になる場合、IntelliSense の結果をオーバーライドする方法を示します。  
  
 この例を実行するには、プロジェクトに次の JavaScript ファイルが必要です。  
  
-   exampleLib.js はサード パーティ製ライブラリを表すプロジェクト ファイルです。  
  
-   exampleLib.intellisense.js は IntelliSense の拡張機能です。 このファイルは、プロジェクトに含める必要はありませんが、exampleLib.js と同じフォルダーに含める必要があります。  
  
-   appCode.js (アプリケーション コードを表すプロジェクト ファイル)。  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>IntelliSense の結果に対する実行時の影響を回避するには  
  
1.  ExampleLib.js するには、次のコードを追加します。  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     上記のコードでラップされた関数がの値に基づいて最初の呼び出しを無視`count`結果は返されません。  
  
2.  次の reference ディレクティブを appCode.js の最初の行として追加します。 ここで使用するパスは、JavaScript ファイルが同じフォルダーにあることを示しています。  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3.  appCode.js で、次のコードを入力します。 つまり、ラップされた関数が呼び出されることはありませんので、IntelliSense ではなく、識別子の一覧が表示されます、`throttled`関数結果が返されない。  
  
     ![Intellisense の結果をオーバーライドする例](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4.  ExampleLib.intellisense.js するには、次のコードを追加します。 期待どおりに、ラップされた関数の IntelliSense が表示されるように、デザイン時動作を変更これは。  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5.  AppCode.js では、以前に入力したのと同じコードを入力して結果をテストします。 今回は、IntelliSense は、必要な情報を提供します。  
  
     ![IntelliSense の結果をオーバーライドする例](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>関連項目  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [識別子の入力候補](../ide/statement-completion-for-identifiers.md)



