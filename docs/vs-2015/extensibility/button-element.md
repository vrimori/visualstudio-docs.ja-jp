---
title: 要素をボタン |Microsoft Docs
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
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20673b87972c51a6cc0e3ce07553a0a721d7cca3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733310"
---
# <a name="button-element"></a>Button 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="attributes-and-elements"></a>属性および要素  
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
|[Parent 要素](../extensibility/parent-element.md)|任意。 ボタンの親要素。|  
|[Icon 要素](../extensibility/icon-element.md)|任意。 ボタンに関連付けられているアイコン。|  
|[Command Flag 要素](../extensibility/command-flag-element.md)|必須。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -テキスト<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[ 要素](../extensibility/strings-element.md)|必須。 子[ButtonText 要素](../extensibility/buttontext-element.md)定義する必要があります。|  
|注釈|省略可能なコメント。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Buttons 要素](../extensibility/buttons-element.md)|ボタン要素をグループ化します。|  
  
## <a name="example"></a>例  
 次の例では、.vsct ファイルで、ボタンを定義します。  
   
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

