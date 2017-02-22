---
title: "コンボ要素 | Microsoft Docs"
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
  - "コンボ要素 (VSCT XML スキーマ)"
  - "コンボ、VSCT XML スキーマ要素"
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# コンボ要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コンボ ボックスに表示されるコマンドを定義します。 次のようには、コンボ ボックスの 4 つの種類があります: DropDownCombo、DynamicCombo、IndexCombo、および MRUCombo です。  
  
## <a name="syntax"></a>構文  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須です。 GUID と ID コマンドの識別子の GUID です。|  
|ID|必須です。 GUID と ID コマンドの識別子の ID です。|  
|デフォルト|必須です。 コンボ ボックスのピクセルの幅を指定する整数。|  
|idCommandList|必須です。 コンボ ボックスに表示される項目の一覧を取得するアクティブなコマンドのターゲットに送信される ID です。 ID は、コントロールと同じ GUID スコープになります。|  
|priority|省略可能です。 優先順位を指定する数値。|  
|型|省略可能です。 ボタンの種類を指定する列挙値。<br /><br /> 指定されていない場合は、ボタンを使用します。<br /><br /> DropDownCombo<br /> VSPackage は、このコンボ ボックスの内容を入力します。 ユーザーは、このドロップダウン リストのテキスト ボックスに何かを入力できません。<br /><br /> DynamicCombo<br /> VSPackage は、このコンボ ボックスの内容を入力します。 ユーザーは、このコンボを編集し、またその内の項目を選択します。<br /><br /> IndexCombo<br /> 点が異なります DynamicCombo と同じには、そのテキストではなく、項目のインデックスを発生させます。<br /><br /> MRUCombo<br /> VSPackage の代わりには、統合開発環境 (IDE) が設定されます。  ユーザーは、このコンボ ボックスで編集できます。 IDE は、コンボ ボックスごとの最後に行った 16 件まで記憶します。<br /><br /> ユーザーは、コンボ ボックスで、何かを選択したり、何か新しいものを入力、IDE は、適切な VSPackage を通知します。|  
|条件|省略可能です。 参照してください [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|省略可能です。 ボタンの親要素です。|  
|CommandFlag|必須です。 参照してください [フラグ要素をコマンド](../extensibility/command-flag-element.md)します。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> フィルター キー機能<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|文字列|必須です。 参照してください [要素を文字列](../extensibility/strings-element.md)します。 アドインの子要素を定義する必要があります。|  
|注釈|省略可能なコメントです。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーでコマンドのコレクションを表します。|  
  
## <a name="example"></a>例  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)