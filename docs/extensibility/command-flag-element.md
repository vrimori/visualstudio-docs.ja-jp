---
title: "コマンドのフラグ要素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandFlag 要素 (VSCT XML スキーマ)"
  - "CommandFlag、VSCT XML スキーマ要素"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# コマンドのフラグ要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

その親要素を変更します。  
  
## 構文  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## 属性および要素  
 次のセクションでは、有効な要素の値について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|値|説明|  
|-------|--------|  
|AllowParams|コマンドのパラメーターをユーザーが入力できることを示す、 **コマンド** コマンドの標準的な名前を入力した場合は、ウィンドウです。<br /><br /> 有効期間: `Button`|  
|通常|グループやボタンれていない場合でも、メニューが作成されます。<br /><br /> 有効期間: `Menu`|  
|CaseSensitive|ユーザーのエントリは、大文字小文字が区別されます。<br /><br /> 有効期間: `Combo`|  
|CommandWellOnly|トップレベルのメニューにコマンドが表示されないと、カスタマイズ可能なその他のシェル、たとえば、キーボード ショートカットにバインドするためにする場合は、このフラグを適用します。 開いて次のコマンドをカスタマイズするには、VSPackage をインストールした後、 **オプション** \] ダイアログ ボックスと \[コマンドの配置を編集して、 **キーボード環境** カテゴリ。 このフラグは、ショートカット メニューのツールバー、メニューのコント ローラー、またはサブメニューの配置には影響しません。<br /><br /> に対して無効です: `Button`, 、`Combo`|  
|DefaultDisabled|既定では、コマンドが無効になっているそれを実装する VSPackage が読み込まれていない場合、または `QueryStatus` メソッドが呼び出されていません。<br /><br /> に対して無効です: `Button`, 、`Combo`|  
|DefaultDocked|既定では、ドッキングされています。 この設定は不要になったはツールバーに適用されます、常にドッキングされているため。|  
|DefaultInvisible|既定では、コマンドはそれを実装する VSPackage が読み込まれていない場合に表示されていない、または `QueryStatus` メソッドが呼び出されていません。<br /><br /> これを組み合わせることをお勧めします `DynamicVisibility` フラグ。<br /><br /> に対して無効です: `Button`, 、`Combo`, 、`Menu`|  
|DontCache|開発環境はキャッシュしていない、 `QueryStatus` メソッドのこのコマンドの結果。<br /><br /> メニューのこれは、そのメニュー項目のテキストをキャッシュしなければ\] メニューの \[コント ローラーを示しています。 メニューには、動的または動的テキストを持つアイテムが含まれている場合は、このフラグを使用します。<br /><br /> に対して無効です: `Button`, 、`Menu`|  
|DynamicItemStart|動的な一覧の先頭を示します。 これにより、連続して呼び出すことによって、リストを構築する環境、 `QueryStatus` OLECMDERR\_E\_UNSUPPORTED フラグが返されるまで、リスト項目のメソッドです。 これは、最近使用した \(MRU\) リストとウィンドウの一覧などのアイテムに適しています。<br /><br /> 有効期間: `Button`|  
|DynamicVisibility|を介して、コマンドの表示\/非表示を変更すること、 `QueryStatus` メソッドまたはコンテキストに含まれている GUID を `VisibilityConstraints` セクションです。<br /><br /> メニューとツール ウィンドウのツールバーではなく、メイン ウィンドウに表示される最上位レベルのツールバーに表示されるコマンドに適用されます。 最上位レベルのツールバー項目を無効になりますが、非表示に、OLECMDF\_INVISIBLE フラグがから返されると、 `QueryStatus` メソッドです。 ツール ウィンドウのツールバーに表示されるツールバーのコマンドを非表示にすることができます。<br /><br /> メニューのことに自動的に非表示にするすべてのメンバーは非表示になるをこのフラグも示されます。 このフラグは、トップレベルのメニューでは、この動作が既にあるために通常サブメニューに割り当てられます。<br /><br /> このフラグと結合する、 `DefaultInvisible` フラグ。<br /><br /> に対して無効です: `Button`, 、`Combo`, 、`Menu`|  
|フィルター キー機能|\[キーのフィルタ リングのトピックを参照して [コンボ要素](../extensibility/combo-element.md)します。<br /><br /> 有効期間: `Combo`|  
|FixMenuController|コマンドが、既定では常にこのコマンドがメニュー コント ローラーに配置されている場合つまり、\] メニューの \[コント ローラー ボタン自体が選択されるたびに、コマンドが選択されます。 メニューの \[コント ローラーがある場合、 `TextIsAnchorCommand` \] メニューの \[コント ローラーはそのテキストを持つコマンドからも使用し、設定、フラグを設定、 `FixMenuController` フラグ。<br /><br /> メニューの \[コント ローラーでコマンドを 1 つだけ必要がありますが、 `FixMenuController` フラグ。 複数のコマンドは、マークされている、最後のコマンド、メニューで、既定のコマンドになります。<br /><br /> 有効期間: `Button`|  
|IconAndText|\[メニューとツールバー、アイコンとテキストを表示します。<br /><br /> に対して無効です: `Button`, 、`Combo`, 、`Menu`|  
|NoAutoComplete|オートコンプリート機能は無効です。<br /><br /> 有効期間: `Combo`|  
|NoButtonCustomize|ユーザーは、このボタンをカスタマイズすることはできません。<br /><br /> に対して無効です: `Button`, 、`Combo`|  
|NoKeyCustomize|キーボードのカスタマイズを有効にしないでください。<br /><br /> に対して無効です: `Button`, 、`Combo`|  
|NoShowOnMenuController|このコマンドがメニュー コント ローラーに配置されている場合、コマンドがドロップダウン リストに表示されません。<br /><br /> 有効期間: `Button`|  
|NotInTBList|使用可能なツールバーの一覧には表示されません。 これはツールバー メニュー型に対してのみ有効です。<br /><br /> 有効期間: `Menu`|  
|NoToolbarClose|ユーザーは、ツールバーを閉じることはできません。 これはツールバー メニュー型に対してのみ有効です。<br /><br /> 有効期間: `Menu`|  
|Pict|ツールバーはメニューにテキストだけでにアイコンのみが表示されます。 アイコンが指定されていない場合は、ツールバーのクリック可能な空白を示しています。<br /><br /> 有効期間: `Button`|  
|PostExec|コマンド以外のブロックを使用できます。 開発環境は、処理前のすべてのクエリが完了するまで実行を延期します。<br /><br /> 有効期間: `Button`|  
|RouteToDocs|コマンドは、アクティブなドキュメントにルーティングされます。<br /><br /> 有効期間: `Button`|  
|StretchHorizontally|このフラグが設定されている場合、幅、コンボ ボックスの幅の最小になり、コンボ ボックスが使用可能な領域を埋めるように拡大して、ツールバーの余裕がある場合。 これは、ツールバーが水平方向にドッキングされているし、ツールバーの 1 つだけのコンボ ボックスは、\(最初のコンボ ボックス以外のすべてのフラグは無視されます\)、フラグを使用している場合にのみ発生します。<br /><br /> 有効期間: `Combo`|  
|TextMenuUseButton|使用して、 `ButtonText` メニューに対応するフィールドです。 既定のフィールドは `MenuText` 指定されている場合。<br /><br /> 有効期間: `Button`|  
|\[テキスト|コマンドまたはメニュー テキストは、実行時に通常を通じて、 `QueryStatus` メソッドです。<br /><br /> に対して無効です: `Button`, 、`Menu`|  
|TextChangesButton|有効期間: `Button`|  
|TextIsAnchorCommand|メニューの \[コント ローラーの場合、メニューのテキストは、\(アンカー\) を既定のコマンドから取得されます。 アンカー コマンドは、最後のコマンドを選択またはラッチです。 メニューの \[コント ローラーが使用して、独自このフラグが設定されていない場合 `MenuText` フィールドです。 ただし、\] メニューの \[コント ローラー\] をクリックすると、そのコント ローラーから選択した最後のコマンドも、できます。<br /><br /> このフラグと組み合わせることをお勧めします `TextChanges` フラグ。<br /><br /> このフラグは、MenuController または MenuControllerLatched に、型のメニューにのみ適用されます。<br /><br /> 有効期間: `Menu`|  
|TextMenuCtrlUseMenu|使用して、 `MenuText` フィールド\] メニューの \[コント ローラーにします。 既定のフィールドは `ButtonText`です。<br /><br /> 有効期間: `Button`|  
|TextMenuUseButton|使用して、 `ButtonText` メニューに対応するフィールドです。 既定のフィールドは `MenuText` 指定されている場合。<br /><br /> 有効期間: `Button`|  
|TextOnly|アイコンが指定されている場合でも、ツールバーまたはメニュー、アイコンが表示されないテキストのみを表示します。<br /><br /> 有効期間: `Button`|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[ボタン要素](../extensibility/buttons-element.md)|グループは、 [Button 要素](../extensibility/button-element.md) 要素。|  
|[メニュー要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)