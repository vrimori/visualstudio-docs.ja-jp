---
title: 要素をボタン |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 128016b892206db64a5295c8c15b26b87637b530
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154272"
---
# <a name="button-element"></a>Button 要素
ユーザーが対話できる要素を定義します。 さまざまな種類のボタンを指定できます: ボタン、メニュー ボタン、および SplitDropDown します。  
  
## <a name="syntax"></a>構文  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 コマンド id を GUID と ID の GUID です。|  
|ID|必須。 コマンド id を GUID と ID の ID。|  
|priority|任意。 優先度を示す数値。|  
|型|任意。 ボタンの種類を指定する列挙値。<br /><br /> 指定しなかった場合は、ボタンを使用します。<br /><br /> ボタン<br /> メニューのおよびコンテキスト メニュー (通常はアイコンのボタンとして)、ツールバーに表示される標準コマンド。<br /><br /> メニュー ボタン<br /> メニュー項目をコマンドは実行されませんが、別のメニューが生成されます。<br /><br /> SplitDropDown<br /> Microsoft Word で標準ツールバーの取り消しとやり直しボタンなどのコントロール。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[親要素](../extensibility/parent-element.md)|任意。 ボタンの親要素。|  
|[Icon 要素](../extensibility/icon-element.md)|任意。 ボタンに関連付けられているアイコン。|  
|[Command flag 要素](../extensibility/command-flag-element.md)|必須。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -テキスト<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[文字列の要素](../extensibility/strings-element.md)|必須。 子[ButtonText 要素](../extensibility/buttontext-element.md)定義する必要があります。|  
|注釈|省略可能なコメント。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)|ボタン要素をグループ化します。|  
  
## <a name="example"></a>例  
 次の例のボタンの定義、 *.vsct*ファイル。  

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
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)