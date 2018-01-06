---
title: "フラグの要素をコマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ff9458eed7f9c77a964240f81017d27d95d9622
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="command-flag-element"></a>コマンド フラグ要素
その親要素を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 次のセクションでは、有効な要素の値について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|[値]|説明|  
|-----------|-----------------|  
|AllowParams|ユーザーがのコマンド パラメーターを入力できることを示します、**コマンド**ウィンドウのコマンドは、の正規の名前を入力したとき。<br /><br /> に対して有効です。`Button`|  
|通常|グループやボタンれていない場合でも、メニューが作成されます。<br /><br /> に対して有効です。`Menu`|  
|CaseSensitive|ユーザーのエントリは、大文字小文字を区別します。<br /><br /> に対して有効です。`Combo`|  
|CommandWellOnly|トップレベル メニューのコマンドは表示されず、キーボード ショートカットにバインドするための他のシェルのカスタマイズ、たとえば、使用できるようにする場合は、このフラグを適用します。 開くことによってこれらのコマンドをカスタマイズするには、VSPackage をインストールした後、**オプション**] ダイアログ ボックスと [コマンドの配置を編集し、**キーボード環境**カテゴリ。 このフラグは、ショートカット メニューのツールバー、メニュー コント ローラー、またはサブメニューの配置には影響しません。<br /><br /> 無効: `Button`、`Combo`|  
|DefaultDisabled|既定では、コマンドが無効になっていますそれを実装する VSPackage が読み込まれていない場合、または`QueryStatus`メソッドが呼び出されていません。<br /><br /> 無効: `Button`、`Combo`|  
|DefaultDocked|既定ではドッキングされています。 この設定は、不要になったはツールバーに適用される、常にドッキングされているためです。|  
|DefaultInvisible|既定では、コマンドはそれを実装する VSPackage が読み込まれていない場合は表示されませんか`QueryStatus`メソッドが呼び出されていません。<br /><br /> これを結合することをお勧め、`DynamicVisibility`フラグ。<br /><br /> 無効: `Button`、 `Combo`、`Menu`|  
|DontCache|開発環境をキャッシュしません、`QueryStatus`メソッドこのコマンドの結果。<br /><br /> メニューのこれは、そのメニュー項目のテキストをキャッシュにないメニュー コント ローラーを示しています。 動的項目または動的なテキストがある項目、メニューが含まれている場合は、このフラグを使用します。<br /><br /> 無効: `Button`、`Menu`|  
|DynamicItemStart|動的な一覧の先頭を示します。 これにより、連続して呼び出すことによって、リストを構築する環境、 `QueryStatus` OLECMDERR_E_UNSUPPORTED フラグが返されるまで、リスト項目のメソッドです。 これは、最近使用した (MRU) のリストとウィンドウのリストなどのアイテムに適しています。<br /><br /> に対して有効です。`Button`|  
|DynamicVisibility|を介して、コマンドの可視性を変更することができます、`QueryStatus`メソッドまたはコンテキストに含まれている GUID を`VisibilityConstraints`セクションです。<br /><br /> メニューとツール ウィンドウのツールバーではなくのメイン ウィンドウに表示される最上位のツールバーに表示されるコマンドに適用されます。 最上位のツールバー項目を無効になっていることができますが、非表示から OLECMDF_INVISIBLE フラグが返されるときに、`QueryStatus`メソッドです。 ツール ウィンドウのツールバーに表示されるツール バー コマンドを非表示にすることができます。<br /><br /> メニューのことが自動的に非表示にするすべてのメンバーは非表示になるをこのフラグも示します。 このフラグは、トップレベルのメニューでは、この動作が既にあるために通常サブメニューに割り当てられます。<br /><br /> このフラグと組み合わせる必要があります、`DefaultInvisible`フラグ。<br /><br /> 無効: `Button`、 `Combo`、`Menu`|  
|フィルター キー機能|キーのフィルタ リングを参照してください[コンボ要素](../extensibility/combo-element.md)です。<br /><br /> に対して有効です。`Combo`|  
|FixMenuController|このコマンドは、メニュー コント ローラーに配置されているのコマンドは常に既定値です。メニュー コント ローラー ボタン自体が選択されているときに、コマンドを選択します。 メニュー コント ローラーがある場合、`TextIsAnchorCommand`フラグが設定、メニュー コント ローラーもを持つコマンドからテキストを取得し、`FixMenuController`フラグ。<br /><br /> メニュー コント ローラーでコマンドを 1 つだけ必要がありますが、`FixMenuController`フラグ。 複数のコマンドがマークされているため、メニューの最後のコマンドが既定のコマンドになります。<br /><br /> に対して有効です。`Button`|  
|IconAndText|メニューとツールバー、アイコンとテキストを表示します。<br /><br /> 無効: `Button`、 `Combo`、`Menu`|  
|NoAutoComplete|オートコンプリート機能は無効です。<br /><br /> に対して有効です。`Combo`|  
|NoButtonCustomize|ユーザーは、このボタンをカスタマイズすることはできません。<br /><br /> 無効: `Button`、`Combo`|  
|NoKeyCustomize|キーボードのカスタマイズを有効にしないでください。<br /><br /> 無効: `Button`、`Combo`|  
|NoShowOnMenuController|このコマンドがメニュー コント ローラーに配置されている場合、コマンドはドロップダウン リストでは表示されません。<br /><br /> に対して有効です。`Button`|  
|NotInTBList|使用可能なツールバーの一覧にありません。 これは、ツール バー メニュー型に対してのみ有効です。<br /><br /> に対して有効です。`Menu`|  
|NoToolbarClose|ユーザーは、ツールバーを閉じることはできません。 これは、ツール バー メニュー型に対してのみ有効です。<br /><br /> に対して有効です。`Menu`|  
|Pict|ツールバーはメニューのテキストのみで、アイコンのみを表示します。 アイコンが指定されていない場合は、ツールバーにある空のクリックできる領域を示します。<br /><br /> に対して有効です。`Button`|  
|PostExec|コマンド非ブロッキングします。 開発環境は、処理前のすべてのクエリが完了するまで実行を延期します。<br /><br /> に対して有効です。`Button`|  
|RouteToDocs|コマンドは、作業中の文書にルーティングされます。<br /><br /> に対して有効です。`Button`|  
|StretchHorizontally|このフラグが設定されている場合、幅、コンボ ボックスに最小の幅になり、コンボ ボックスが使用可能な領域を埋めるように拡大ツールバーの余裕がある場合。 これは、ツールバーが水平にドッキングされているし、ツールバーの 1 つだけのコンボ ボックスは、(最初のコンボ ボックス以外のすべてのフラグは無視されます)、フラグを使用している場合にのみ発生します。<br /><br /> に対して有効です。`Combo`|  
|TextMenuUseButton|使用して、`ButtonText`メニューに対応するフィールドです。 既定のフィールドは`MenuText`指定されている場合。<br /><br /> に対して有効です。`Button`|  
|テキスト|コマンドまたはメニューのテキストで変更できます実行時に、通常、`QueryStatus`メソッドです。<br /><br /> 無効: `Button`、`Menu`|  
|TextChangesButton|に対して有効です。`Button`|  
|TextIsAnchorCommand|メニュー コント ローラーの場合、メニューのテキストは、既定 (アンカー) のコマンドから取得されます。 アンカー コマンドは、最後のコマンドを選択またはラッチがします。 このフラグが設定されていない場合、メニュー コント ローラーを使用して独自`MenuText`フィールドです。 ただし、メニュー コント ローラーをクリックすると引き続きにより、そのコント ローラーから最後の選択したコマンド。<br /><br /> このフラグとを組み合わせて使用することをお勧め、`TextChanges`フラグ。<br /><br /> このフラグは、MenuController または MenuControllerLatched 型のメニューにのみ適用されます。<br /><br /> に対して有効です。`Menu`|  
|TextMenuCtrlUseMenu|使用して、`MenuText`フィールド メニュー コント ローラーにします。 既定のフィールドは`ButtonText`します。<br /><br /> に対して有効です。`Button`|  
|TextMenuUseButton|使用して、`ButtonText`メニューに対応するフィールドです。 既定のフィールドは`MenuText`指定されている場合。<br /><br /> に対して有効です。`Button`|  
|TextOnly|アイコンが指定されている場合でも、ツールバーまたはメニューがアイコンなしのテキストのみを表示します。<br /><br /> に対して有効です。`Button`|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)|グループを提供[ボタン要素](../extensibility/button-element.md)要素。|  
|[Menus 要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
  
## <a name="see-also"></a>参照  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)