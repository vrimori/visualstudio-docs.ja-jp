---
title: Combo 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00ecabcf90e63b18961a828c12ae300be359b5a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839987"
---
# <a name="combo-element"></a>Combo 要素
コンボ ボックスに表示されるコマンドを定義します。 次のようには、コンボ ボックスの 4 つの種類があります: DropDownCombo、DynamicCombo、IndexCombo、および MRUCombo します。  
  
## <a name="syntax"></a>構文  
  
```xml 
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 コマンド id を GUID と ID の GUID です。|  
|ID|必須。 コマンド id を GUID と ID の ID。|  
|デフォルト|必須。 コンボ ボックスのピクセル幅を指定する整数。|  
|idCommandList|必須。 コンボ ボックスに表示される項目の一覧を取得するアクティブなコマンドのターゲットに送信される ID です。 ID は、コントロールと同じ GUID スコープ内になります。|  
|priority|任意。 優先度を示す数値。|  
|型|任意。 ボタンの種類を指定する列挙値。<br /><br /> 指定しなかった場合は、ボタンを使用します。<br /><br /> DropDownCombo<br /> VSPackage は、このコンボ ボックスの内容を入力します。 ユーザーは、このドロップダウン リストのテキスト ボックスに何かを入力できません。<br /><br /> DynamicCombo<br /> VSPackage は、このコンボ ボックスの内容を入力します。 ユーザーは、このコンボを編集し、またその項目を選択します。<br /><br /> IndexCombo<br /> その点 DynamicCombo と同じテキストではなく、項目のインデックスを発生させます。<br /><br /> MRUCombo<br /> VSPackage の代わりには、統合開発環境 (IDE) が設定されます。  ユーザーは、このコンボ ボックスで編集できます。 IDE は、コンボ ボックスあたり 16 の最後のエントリまで記憶します。<br /><br /> ユーザーは、コンボ ボックスで、何かを選択したり、新しいものを入力、IDE は、適切な VSPackage を通知します。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|親|任意。 ボタンの親要素。|  
|CommandFlag|必須。 参照してください[Command flag 要素](../extensibility/command-flag-element.md)します。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -フィルター キー機能<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|文字列|必須。 参照してください[文字列要素](../extensibility/strings-element.md)します。 子 ButtonText 要素を定義する必要があります。|  
|注釈|省略可能なコメント。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーのコマンドのコレクションを表します。|  
  
## <a name="example"></a>例  
  
```xml  
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
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
