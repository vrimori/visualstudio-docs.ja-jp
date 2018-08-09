---
title: Menu 要素 |Microsoft Docs
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
ms.openlocfilehash: d69a6951cdae84ba2abc06bcdfde19fffa665c03
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637511"
---
# <a name="menu-element"></a>Menu 要素
1 つのメニュー項目を定義します。 これらは、メニューの 6 つの種類: コンテキスト、メニューの MenuController、MenuControllerLatched、ツールバー、および ToolWindowToolbar します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 コマンド id を GUID と ID の GUID です。|  
|ID|必須。 コマンド id を GUID と ID の ID。|  
|priority|任意。 グループのメニューで、メニューの相対位置を示す数値。|  
|ToolbarPriorityInBand|任意。 ウィンドウがドッキングされているときに、バンドで、ツールバーの相対位置を指定する数値。|  
|型|任意。 要素の種類を指定する列挙値。<br /><br /> 存在しない場合、既定の種類はメニューです。<br /><br /> コンテキスト<br /> ユーザーがウィンドウを右クリックしたときに表示されるショートカット メニュー。 ショートカット メニューには、次の特徴があります。<br /><br /> -使用しません、**親**と**優先度**メニューのショートカット メニューとして表示される場合のフィールドします。<br />-サブメニューとしてし、ショートカット メニューと使用できます。 この場合、両方**グループ ID**と**優先度**フィールドが順守されます。<br />-は常に利用可能ではありません。<br /><br /> ショートカット メニューには、次の条件に該当する場合にのみが表示されます。<br /><br /> -これをホストするウィンドウが表示されます。<br />VSPackage で-マウス ハンドラーは、ウィンドウの右クリックを検出し、コマンドを処理するメソッドを呼び出して、します。<br />、呼び出してショートカット メニューが表示される、<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A>メソッド (推奨) または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>メソッド。<br /><br /> メニュー<br /> ドロップダウン メニューを提供します。 ドロップダウン メニューには、次の特徴があります。<br /><br /> 定義に親保護に努めています。<br />-親グループ、またはグループの CommandPlacement いる必要があります。<br />-その他の種類 メニューのサブメニューをすることができます。<br />-が、親メニューが表示されるたびに自動的に表示します。<br />表示されるようにする VSPackage のコードの実装は必要ありません。<br /><br /> MenuController<br /> ツールバーで通常使用される、分割ボタンのドロップダウン メニューを提供します。 MenuController メニューには、次の特徴があります。<br /><br /> -は、親または CommandPlacement を介して別のメニューに含まれます。<br />定義に親保護に努めています。<br />-任意の種類 メニューをその親として設定するできます。<br />-自動的に利用可能になってたびに、親メニューが表示されます。<br />-プログラムのサポートを表示されるメニューは必要ありません。<br /><br /> 分割ボタン メニューからコマンドがメニュー ボタンに表示されます。 表示されるコマンドでは、次の特性の 1 つがあります。<br /><br /> -これは、コマンドがまだ表示され、有効になっている場合に使用された最後のコマンドです。<br />-これは、最初のコマンドの表示です。<br /><br /> MenuControllerLatched<br /> コマンドとして指定できます、既定の選択コマンドのマーク ラッチで分割ボタンのドロップダウン メニューを提供します。<br /><br /> ラッチのコマンドは、通常は、チェック マークを表示することによって、として選択した場合は、メニューでマークされているコマンドです。 コマンドは、OLECMDF_LATCHED がある場合にそのラッチとマークできますフラグの実装での設定、`QueryStatus`のメソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。 MenuControllerLatched メニューには、次の特徴があります。<br /><br /> -は、親グループまたは CommandPlacement を介して別のメニューに含まれます。<br />定義に親保護に努めています。<br />-任意の種類 メニューをその親として設定するできます。<br />-親メニューが表示されるたびには、使用可能な実行されます。<br />-プログラムのサポートを表示されるメニューは必要ありません。<br /><br /> 分割ボタン メニューからコマンドがメニュー ボタンに表示されます。 表示されるコマンドでは、次の特性の 1 つがあります。<br /><br /> -これは、ラッチは、表示されている最初のコマンドです。<br />-これは、最初のコマンドの表示です。<br /><br /> ツール バー<br /> ツールバーを提供します。 ツールバーには、次の特徴があります。<br /><br /> -親の定義では無視されます。<br />-できません CommandPlacement を使用しても、任意のグループのサブメニューできます。<br />クリックして常に表示される-**ツールバー**上、**ビュー**メニュー。<br />使用して表示可能な[VisibilityItem](../extensibility/visibilityitem-element.md)します。<br />で作成するためのコードは不要です。 例のツールバーを作成する方法については、次を参照してください。[ツールバーを追加](../extensibility/adding-a-toolbar.md)します。<br /><br /> ToolWindowToolbar<br /> ツールバーが開発環境に接続されているのと同じように、特定のツール ウィンドウに関連付けられているツールバーを提供します。<br /><br /> -親の定義では無視されます。<br />-できません CommandPlacement を使用しても、任意のグループのサブメニューできます。<br />は、ツールバーをホストしているツール ウィンドウが表示され、VSPackage では、ツール ウィンドウに、ツールバーを明示的に追加している場合にのみが表示されます。 これは、通常、ツールバーのホストのプロパティを取得することにより、ツール ウィンドウが作成されたときに (によって表される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>インターフェイス) ツール ウィンドウ フレームと、呼び出しから、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>メソッド。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|任意。 メニュー項目の親要素。|  
|CommandFlag|必須。 参照してください[Command flag 要素](../extensibility/command-flag-element.md)します。 メニューの有効な CommandFlag 値は次のとおりです。<br /><br /> -   **通常**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -このフラグでは、ツールバーの表示には影響しません。<br />-   **DontCache**<br />-   **DynamicVisibility** -このフラグでは、ツールバーの表示には影響しません。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **テキスト**<br />-   **TextIsAnchorCommand**|  
|文字列|必須。 参照してください[文字列要素](../extensibility/strings-element.md)します。 子`ButtonText`要素を定義する必要があります。|  
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
 [Visual Studio コマンド テーブル (.vsct) ファイルします。](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)