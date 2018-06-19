---
title: Menu 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5c44ca8a78a331d66d099b8d141c4b66c1144949
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143453"
---
# <a name="menu-element"></a>Menu 要素
1 つのメニュー項目を定義します。 これらは、メニューの 6 つの種類: コンテキスト、メニューの MenuController、MenuControllerLatched、ツールバー、および ToolWindowToolbar です。  
  
## <a name="syntax"></a>構文  
  
```  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 GUID と ID コマンド id の GUID です。|  
|ID|必須。 GUID と ID のコマンド識別子の ID です。|  
|priority|任意。 グループのメニューで、メニューの相対的な位置を示す数値。|  
|ToolbarPriorityInBand|任意。 ウィンドウがドッキングされているときに、帯域内で、ツールバーの相対的な位置を指定する数値。|  
|型|任意。 要素の種類を指定する列挙値。<br /><br /> 存在しない場合は既定の型は、メニューです。<br /><br /> コンテキスト<br /> ユーザーがウィンドウを右クリックしたときに表示されるショートカット メニューです。 ショートカット メニューには、次の特徴があります。<br /><br /> -メニューのショートカット メニューとして表示される場合は、親と優先度のフィールドを使用しません。<br />-サブメニューとしてし、ショートカット メニューとしても使用できます。 ここでは、グループの ID と優先度の両方のフィールドが守られています。<br />-は常に利用可能ではありません。<br /><br /> ショートカット メニューには、次の条件に当てはまる場合にのみが表示されます。<br /><br /> -ホスト ウィンドウが表示されます。<br />-、VSPackage でマウスのハンドラーは、ウィンドウを右クリックを検出し、コマンドを処理するメソッドを呼び出します。<br />、呼び出してショートカット メニューが表示される、<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A>メソッド (推奨) または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>メソッドです。<br /><br /> メニュー<br /> ドロップダウン メニューを提供します。 ドロップダウン メニューには、次の特徴があります。<br /><br /> -定義に親を尊重します。<br />-親グループ、またはグループに CommandPlacement いる必要があります。<br />-が、その他の種類のメニューにサブメニューがあります。<br />-が、親メニューが表示されるたびに自動的に表示します。<br />で表示されるように、VSPackage コードの実装は不要です。<br /><br /> MenuController<br /> ツールバーで通常使用される、分割ボタンのドロップダウン メニューを提供します。 MenuController メニューには、次の特性があります。<br /><br /> -親または CommandPlacement を介して別のメニューに含める必要があります。<br />-定義に親を尊重します。<br />-その親として任意の種類のメニューを持つことができます。<br />-は自動的に使用できる親メニューが表示されるたびにします。<br />にプログラムによるサポート メニューを表示するは不要です。<br /><br /> 分割ボタン メニューからコマンドがメニュー ボタンに表示されます。 表示されるコマンドでは、次の特性の 1 つがあります。<br /><br /> -これは、コマンドがまだ表示され、有効になっている場合に使用された最後のコマンドです。<br />-これは、最初のコマンドの表示です。<br /><br /> MenuControllerLatched<br /> コマンドとして指定できます、既定の選択ラッチとコマンドをマークすることによって分割ボタンのドロップダウン メニューを提供します。<br /><br /> ラッチのコマンドは、チェック マークを表示することによって一般的に、選択されたメニューでマークされているコマンドです。 コマンドは、ラッチ、OLECMDF_LATCHED がある場合としてマークできますフラグの実装での設定、`QueryStatus`のメソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。 MenuControllerLatched メニューには、次の特性があります。<br /><br /> -親グループまたは CommandPlacement を介して別のメニューに含める必要があります。<br />-定義に親を尊重します。<br />-その親として任意の種類のメニューを持つことができます。<br />-は、親メニューが表示されるときに提供されます。<br />にプログラムによるサポート メニューを表示するは不要です。<br /><br /> 分割ボタン メニューからコマンドがメニュー ボタンに表示されます。 表示されるコマンドでは、次の特性の 1 つがあります。<br /><br /> -これは、ラッチは、最初の表示されているコマンドです。<br />-これは、最初のコマンドの表示です。<br /><br /> ツール バー<br /> ツールバーを提供します。 ツールバーには、次の特徴があります。<br /><br /> -定義に親を無視します。<br />-させることができないを任意のグループのサブメニュー CommandPlacement を使用しても描画されません。<br />クリックすると常に表示される-**ツールバー**上、**ビュー**メニュー。<br />使用して表示可能な[VisibilityItem](../extensibility/visibilityitem-element.md)です。<br />-作成するためのコードは必要ありません。 ツールバーを作成する方法の例は、次を参照してください。[ツールバーを追加する](../extensibility/adding-a-toolbar.md)です。<br /><br /> ToolWindowToolbar<br /> ツールバーは、開発環境に接続されているのと同じように、特定のツール ウィンドウに関連付けられているツールバーを提供します。<br /><br /> -定義に親を無視します。<br />-させることができないを任意のグループのサブメニュー CommandPlacement を使用しても描画されません。<br />は、ツールバーをホストするツール ウィンドウが表示され、VSPackage は、ツール ウィンドウにツールバーを追加する明示的に場合にのみが表示されます。 これは、通常、ツール ウィンドウのツールバーのホストのプロパティを取得することによって作成時に (で表される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>インターフェイス) ツール ウィンドウの枠とし、呼び出し元から、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>メソッドです。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|任意。 メニュー項目の親要素です。|  
|CommandFlag|必須。 参照してください[コマンド フラグ要素](../extensibility/command-flag-element.md)です。 メニューの有効な CommandFlag 値は次のとおりです。<br /><br /> -   **通常**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -このフラグではツールバーの表示には影響しません。<br />-   **DontCache**<br />-   **DynamicVisibility** -このフラグではツールバーの表示には影響しません。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **テキスト**<br />-   **TextIsAnchorCommand**|  
|文字列|必須。 参照してください[要素の文字列](../extensibility/strings-element.md)です。 子`ButtonText`要素が定義されている必要があります。|  
|注釈|省略可能なコメント。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Menus 要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
  
## <a name="example"></a>例  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)