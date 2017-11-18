---
title: "複合要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f170efc945f92d13eda61830ef682ab4cd8fc755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="combo-element"></a>複合要素
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
|guid|必須です。 GUID と ID コマンド id の GUID です。|  
|ID|必須です。 GUID と ID のコマンド識別子の ID です。|  
|デフォルト|必須です。 コンボ ボックスのピクセル幅を指定する整数。|  
|idCommandList|必須です。 コンボ ボックスに表示される項目の一覧を取得するアクティブなコマンドのターゲットに送信される ID です。 ID は、コントロールと同じ GUID スコープになります。|  
|priority|省略可能です。 優先順位を指定する数値。|  
|型|省略可能です。 ボタンの種類を指定する列挙値。<br /><br /> 指定されていない場合は、ボタンを使用します。<br /><br /> DropDownCombo<br /> VSPackage は、このコンボ ボックスの内容に情報を入力します。 ユーザーは、このドロップダウン リストのテキスト ボックスに何かを入力できません。<br /><br /> DynamicCombo<br /> VSPackage は、このコンボ ボックスの内容に情報を入力します。 ユーザーは、このコンボを編集しても、内の項目を選択できます。<br /><br /> IndexCombo<br /> 点を除けば DynamicCombo と同じには、そのテキストではなく、項目のインデックスを発生させます。<br /><br /> MRUCombo<br /> VSPackage の代理として、統合開発環境 (IDE) が設定されます。  ユーザーは、このコンボ ボックスで編集できます。 IDE は、コンボ ボックスあたり 16 最後のエントリまで記憶します。<br /><br /> ユーザーは、コンボ ボックスで、何かを選択したり、新しいものを入力、ときに、IDE は、適切な VSPackage に通知します。|  
|状態|省略可能です。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|省略可能です。 ボタンの親要素です。|  
|CommandFlag|必須です。 参照してください[コマンド フラグ要素](../extensibility/command-flag-element.md)です。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -フィルター キー機能<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|文字列|必須です。 参照してください[要素の文字列](../extensibility/strings-element.md)です。 ButtonText の子要素を定義する必要があります。|  
|注釈|省略可能なコメント。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーのコマンドのコレクションを表します。|  
  
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
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)