---
title: "要素のボタンをクリックして |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd630a2fed94604cb91dc3af7e46f96269f75ad0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="button-element"></a>Button 要素
ユーザーが対話する要素を定義します。 さまざまな種類のボタンを指定できます: ボタン、メニュー ボタン、および SplitDropDown です。  
  
## <a name="syntax"></a>構文  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須です。 GUID と ID コマンド id の GUID です。|  
|ID|必須です。 GUID と ID のコマンド識別子の ID です。|  
|priority|省略可能です。 優先順位を指定する数値。|  
|型|省略可能です。 ボタンの種類を指定する列挙値。<br /><br /> 指定されていない場合は、ボタンを使用します。<br /><br /> ボタン<br /> メニューのおよびコンテキスト メニュー (通常、アイコンのボタンとして)、ツールバーに表示される標準的なコマンド。<br /><br /> メニュー ボタン<br /> メニュー項目をコマンドは実行されませんが、別のメニューが生成されます。<br /><br /> SplitDropDown<br /> Microsoft Word で、標準ツールバーの取り消しとやり直しボタンなどのコントロールです。|  
|状態|省略可能です。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Parent 要素](../extensibility/parent-element.md)|省略可能です。 ボタンの親要素です。|  
|[Icon 要素](../extensibility/icon-element.md)|省略可能です。 ボタンに関連付けられているアイコン。|  
|[Command Flag 要素](../extensibility/command-flag-element.md)|必須です。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -テキスト<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[ 要素](../extensibility/strings-element.md)|必須です。 子[ButtonText 要素](../extensibility/buttontext-element.md)定義する必要があります。|  
|注釈|省略可能なコメント。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)|ボタンの要素をグループ化します。|  
  
## <a name="example"></a>例  
 次の例では、.vsct ファイル内のボタンを定義します。  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)