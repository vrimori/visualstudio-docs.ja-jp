---
title: "Menu 要素 | Microsoft Docs"
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
  - "メニュー、VSCT XML スキーマ要素"
  - "メニュー要素 (VSCT XML スキーマ)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Menu 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

1 つのメニュー項目を定義します。 これらは、メニューの 6 つの種類: コンテキスト、メニューの MenuController、MenuControllerLatched、ツールバー、および ToolWindowToolbar です。  
  
## 構文  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 GUID と ID コマンドの識別子の GUID です。|  
|ID|必須です。 GUID と ID コマンドの識別子の ID です。|  
|priority|省略可能です。 メニューのグループで、メニューの相対位置を示す数値。|  
|ToolbarPriorityInBand|省略可能です。 ウィンドウがドッキングされているときに、帯域外でツールバーの相対位置を指定する数値。|  
|型|省略可能です。 要素の種類を指定する列挙値。<br /><br /> 存在しない場合、既定の種類はメニューです。<br /><br /> コンテキスト<br /> ユーザーがウィンドウを右クリックしたときに表示されるショートカット メニュー。 ショートカット メニューでは、次の特性があります。<br /><br /> -   メニューのショートカット メニューとして表示される場合は、親と優先順位フィールドを使用しません。<br />-   サブメニューおよびショートカット メニューとしても使用できます。 この場合は、グループ ID と優先度の両方のフィールドが遵守されます。<br />-   常に使用できません。<br /><br /> ショートカット メニューには、次の条件に該当する場合にのみが表示されます。<br /><br /> -   ホストするウィンドウが表示されます。<br />-   VSPackage でマウス ハンドラーは、ウィンドウを右クリックを検出し、コマンドを処理するメソッドを呼び出して、します。<br />-   呼び出して、ショートカット メニューが表示される、 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> メソッド \(推奨\) または <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> メソッドです。<br /><br /> メニュー<br /> ドロップダウン メニューを提供します。 ドロップ ダウン メニューでは、次の特性があります。<br /><br /> -   その定義内の親に努めています。<br />-   親グループ、またはグループに CommandPlacement が必要です。<br />-   他のメニューのサブメニューを指定できます。<br />-   親メニューが表示されるたびに自動的に表示されます。<br />-   表示されるようにする VSPackage コードの実装は不要です。<br /><br /> MenuController<br /> 通常、ツールバーで使用する分割ボタンのドロップダウン メニューを提供します。 MenuController メニューには、次の特性があります。<br /><br /> -   親または CommandPlacement を通じて別のメニューにも含める必要があります。<br />-   その定義内の親に努めています。<br />-   親として任意の種類のメニューを設定できます。<br />-   自動的に使用できる親メニューが表示されるたびにします。<br />-   表示されるメニューにプログラムでのサポートは必要ありません。<br /><br /> 分割ボタン メニューからコマンドがメニュー ボタンに表示されます。 表示されるコマンドでは、次の特性の 1 つがあります。<br /><br /> -   まだコマンドが表示され、有効になっている場合に使用された最後のコマンドになります。<br />-   最初のコマンドの表示することをお勧めします。<br /><br /> MenuControllerLatched<br /> コマンドとして指定できます、既定の選択のコマンドは、ラッチとしてマークすることで分割ボタンのドロップダウン メニューを提供します。<br /><br /> ラッチのコマンドは、チェック マークを表示することで一般に、選択されたメニューでマークされているコマンドです。 コマンドは、ラッチ、OLECMDF\_LATCHED がある場合、マークできるフラグの実装での設定、 `QueryStatus` のメソッド、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスです。 MenuControllerLatched メニューには、次の特性があります。<br /><br /> -   親グループまたは CommandPlacement により別のメニューにも含める必要があります。<br />-   その定義内の親に努めています。<br />-   親として任意の種類のメニューを設定できます。<br />-   親メニューが表示されるたびに使用されます。<br />-   表示されるメニューにプログラムでのサポートは必要ありません。<br /><br /> 分割ボタン メニューからコマンドがメニュー ボタンに表示されます。 表示されるコマンドでは、次の特性の 1 つがあります。<br /><br /> -   ラッチは、最初の表示されているコマンドになります。<br />-   最初のコマンドの表示することをお勧めします。<br /><br /> ツール バー<br /> ツールバーを提供します。 ツールバーでは、次の特性があります。<br /><br /> -   その定義内の親は無視されます。<br />-   できません、グループのサブメニュー CommandPlacement を使用しても描画されません。<br />-   クリックすると常に表示される **ツールバー** 上、 **ビュー** メニュー。<br />-   使用して表示できる、 [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis)です。<br />-   作成するためのコードは必要ありません。 例のツールバーを作成する方法については、次を参照してください。 [ツールバーを追加します。](../extensibility/adding-a-toolbar.md)します。<br /><br /> ToolWindowToolbar<br /> ツールバーが開発環境に接続されていると同様に、特定のツール ウィンドウに関連付けられているツールバーを提供します。<br /><br /> -   その定義内の親は無視されます。<br />-   できません、グループのサブメニュー CommandPlacement を使用しても描画されません。<br />-   ツールバーをホストするツール ウィンドウが表示され、VSPackage では、ツール ウィンドウに、ツールバーを明示的に追加している場合にのみ表示されます。 これは、通常、ツールバーのホストのプロパティを取得することで、ツール ウィンドウが作成されるとき \(で表される、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> インターフェイス\)、ツール ウィンドウのフレームと、呼び出し元から、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> メソッドです。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|親|省略可能です。 メニュー項目の親要素です。|  
|CommandFlag|必須です。 「[コマンドのフラグ要素](../extensibility/command-flag-element.md)」を参照してください。 メニューの有効な CommandFlag 値は次のとおりです。<br /><br /> -   **通常**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-このフラグではツールバーの表示には影響しません。<br />-   **DontCache**<br />-   **DynamicVisibility** \-このフラグではツールバーの表示には影響しません。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **\[テキスト**<br />-   **TextIsAnchorCommand**|  
|文字列|必須です。 「[文字列の要素](../extensibility/strings-element.md)」を参照してください。 子 `ButtonText` 要素が定義されている必要があります。|  
|注釈|省略可能なコメントです。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[メニュー要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
  
## 使用例  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)