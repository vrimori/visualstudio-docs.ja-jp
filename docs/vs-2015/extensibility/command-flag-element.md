---
title: フラグの要素をコマンド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32e1e5f4c5bf236ec1c38f6a0a5314eb278a59f8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272195"
---
# <a name="command-flag-element"></a>Command Flag 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|AllowParams|ユーザーがコマンドのパラメーターを入力できることを示します、**コマンド**ウィンドウ、コマンドの標準名を入力するとき。<br /><br /> に対して有効です。 `Button`|  
|通常|グループやボタンれていない場合でも、メニューが作成されます。<br /><br /> に対して有効です。 `Menu`|  
|CaseSensitive|ユーザーのエントリは、区別されます。<br /><br /> に対して有効です。 `Combo`|  
|CommandWellOnly|キーボード ショートカットにバインドするための他のシェル カスタマイズに使用できるようにする、コマンドは、最上位のメニューに表示されない場合は、このフラグを適用します。 開いてこれらのコマンドをカスタマイズするには、VSPackage をインストールした後、**オプション**] ダイアログ ボックスと [コマンドの配置を編集し、**キーボード環境**カテゴリ。 このフラグは、ショートカット メニューのツールバー、メニュー コント ローラー、またはサブメニューへの配置には影響しません。<br /><br /> に対して無効です: `Button`、 `Combo`|  
|DefaultDisabled|既定では、それを実装する VSPackage が読み込まれていない場合のコマンドは、無効には、または`QueryStatus`メソッドが呼び出されていません。<br /><br /> に対して無効です: `Button`、 `Combo`|  
|DefaultDocked|既定でドッキングします。 この設定は不要になったはツールバーに適用されます、常にドッキングされているためです。|  
|DefaultInvisible|既定では、コマンドはそれを実装する VSPackage が読み込まれていない場合に表示されていない、または`QueryStatus`メソッドが呼び出されていません。<br /><br /> これを組み合わせることをお勧め、`DynamicVisibility`フラグ。<br /><br /> に対して無効です: `Button`、 `Combo`、 `Menu`|  
|DontCache|開発環境をキャッシュしません、`QueryStatus`このコマンドのメソッドの結果。<br /><br /> メニューのこれは、そのメニュー項目のテキストをキャッシュにないメニュー コント ローラーを指示します。 メニューには、動的な項目または動的テキストを含む項目が含まれている場合は、このフラグを使用します。<br /><br /> に対して無効です: `Button`、 `Menu`|  
|DynamicItemStart|動的なリストの先頭を示します。 これにより、連続して呼び出すことによってリストを作成する環境、 `QueryStatus` OLECMDERR_E_UNSUPPORTED フラグが返されるまで、リスト項目のメソッド。 これは、最近使用した (MRU) のリストとウィンドウのリストなどの項目に適してします。<br /><br /> に対して有効です。 `Button`|  
|DynamicVisibility|コマンドの可視性を変更できます、`QueryStatus`メソッドまたはコンテキストに含まれている GUID によって、`VisibilityConstraints`セクション。<br /><br /> メイン ウィンドウに表示される最上位レベルのツールバーではなくメニューやツール ウィンドウのツールバーに表示されるコマンドに適用されます。 トップレベルのツール バー アイテムを無効になっていることができますが、非表示に、OLECMDF_INVISIBLE フラグから返されるときに、`QueryStatus`メソッド。 ツール ウィンドウのツールバーに表示されるツールバーのコマンドを非表示にすることができます。<br /><br /> メニューのことが自動的に非表示にするすべてのメンバーが非表示をこのフラグも示します。 通常、このフラグは、トップレベルのメニューでは、この動作が既にあるため、サブメニューに割り当てられます。<br /><br /> このフラグと組み合わせる必要があります、`DefaultInvisible`フラグ。<br /><br /> に対して無効です: `Button`、 `Combo`、 `Menu`|  
|フィルター キー機能|キーのフィルタ リングのトピックを参照して[Combo 要素](../extensibility/combo-element.md)します。<br /><br /> に対して有効です。 `Combo`|  
|FixMenuController|コマンドは、常に既定では、このコマンドは、メニュー コント ローラーに配置されているが場合、つまり、メニュー コント ローラー ボタン自体が選択されるたびに、コマンドを選択します。 メニュー コント ローラーがある場合、`TextIsAnchorCommand`フラグが設定、メニュー コント ローラーでは、テキストを持つコマンドからもその後、`FixMenuController`フラグ。<br /><br /> メニュー コント ローラーでコマンドを 1 つだけ必要がありますが、`FixMenuController`フラグ。 1 つ以上のコマンドがマークされているため、メニューの最後のコマンドが既定のコマンドになります。<br /><br /> に対して有効です。 `Button`|  
|IconAndText|メニューとツールバーのアイコンとテキストを表示します。<br /><br /> に対して無効です: `Button`、 `Combo`、 `Menu`|  
|NoAutoComplete|オートコンプリート機能は無効です。<br /><br /> に対して有効です。 `Combo`|  
|NoButtonCustomize|ユーザーは、このボタンをカスタマイズすることはできません。<br /><br /> に対して無効です: `Button`、 `Combo`|  
|NoKeyCustomize|キーボードのカスタマイズを有効にしないでください。<br /><br /> に対して無効です: `Button`、 `Combo`|  
|NoShowOnMenuController|このコマンドは、メニュー コント ローラーに配置されて場合、コマンドは、ドロップダウン リストでは表示されません。<br /><br /> に対して有効です。 `Button`|  
|NotInTBList|使用可能なツールバーの一覧には表示されません。 これは、ツール バー メニュー型に対してのみ有効です。<br /><br /> に対して有効です。 `Menu`|  
|NoToolbarClose|ユーザーは、ツールバーを閉じることができません。 これは、ツール バー メニュー型に対してのみ有効です。<br /><br /> に対して有効です。 `Menu`|  
|pict|ツールバーはメニューのテキストのみアイコンのみを表示します。 アイコンが指定されていない場合は、ツールバーにある空のクリック可能領域に表示されます。<br /><br /> に対して有効です。 `Button`|  
|PostExec|では、コマンドのブロック不可。 開発環境は、処理前のすべてのクエリが完了するまで実行を延期します。<br /><br /> に対して有効です。 `Button`|  
|RouteToDocs|コマンドは、アクティブなドキュメントにルーティングされます。<br /><br /> に対して有効です。 `Button`|  
|StretchHorizontally|このフラグが設定されている場合、幅、コンボ ボックスの最小幅になり、コンボ ボックスが使用可能な領域を埋めるように拡大、ツールバーのスペースがある場合。 これは、ツールバーが水平方向にドッキングされているし、ツールバーの 1 つだけのコンボ ボックスが (最初のコンボ ボックス以外のすべてのフラグは無視されます) フラグを使用できる場合にのみ発生します。<br /><br /> に対して有効です。 `Combo`|  
|TextMenuUseButton|使用して、`ButtonText`メニュー フィールド。 既定のフィールドは`MenuText`指定されている場合。<br /><br /> に対して有効です。 `Button`|  
|テキスト|コマンドまたはメニューのテキストは実行時に、通常、`QueryStatus`メソッド。<br /><br /> に対して無効です: `Button`、 `Menu`|  
|TextChangesButton|に対して有効です。 `Button`|  
|TextIsAnchorCommand|メニュー コント ローラーの場合、メニューのテキストは、既定 (アンカー) のコマンドから取得されます。 アンカー コマンドは、選択、またはそのラッチの最後のコマンドです。 メニュー コント ローラーは、独自このフラグが設定されていない場合`MenuText`フィールド。 ただし、メニュー コント ローラーをクリックすると、そのコント ローラーから選択した最後のコマンドも、します。<br /><br /> このフラグと組み合わせることをお勧め、`TextChanges`フラグ。<br /><br /> このフラグは、MenuController または MenuControllerLatched 型のメニューにのみ適用されます。<br /><br /> に対して有効です。 `Menu`|  
|TextMenuCtrlUseMenu|使用して、`MenuText`フィールド メニュー コント ローラーにします。 既定のフィールドは`ButtonText`します。<br /><br /> に対して有効です。 `Button`|  
|TextMenuUseButton|使用して、`ButtonText`メニュー フィールド。 既定のフィールドは`MenuText`指定されている場合。<br /><br /> に対して有効です。 `Button`|  
|TextOnly|アイコンが指定した場合でも、ツールバーまたはメニュー アイコンなしでテキストのみを表示します。<br /><br /> に対して有効です。 `Button`|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)|グループを提供します。[ボタン要素](../extensibility/button-element.md)要素。|  
|[Menus 要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

