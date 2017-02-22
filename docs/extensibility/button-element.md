---
title: "Button 要素 | Microsoft Docs"
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
  - "ボタン要素 (VSCT XML スキーマ)"
  - "ボタン、VSCT XML スキーマ要素"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Button 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ユーザーが対話できる要素を定義します。 さまざまな種類のボタンは、:] ボタン、メニュー ボタン、および SplitDropDown です。  
  
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
|guid|必須です。 GUID と ID コマンドの識別子の GUID です。|  
|ID|必須です。 GUID と ID コマンドの識別子の ID です。|  
|priority|省略可能です。 優先順位を指定する数値。|  
|型|省略可能です。 ボタンの種類を指定する列挙値。<br /><br /> 指定されていない場合は、ボタンを使用します。<br /><br /> ボタン<br /> メニューのおよびコンテキスト メニュー (通常はアイコンのボタンとして)、ツールバーに表示される標準的なコマンドです。<br /><br /> メニュー ボタン<br /> メニュー項目をコマンドを実行できませんが、別のメニューが生成されます。<br /><br /> SplitDropDown<br /> Microsoft Word の [標準] ツールバーを元に戻す/やり直すボタンなどのコントロールです。|  
|条件|省略可能です。 参照してください [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[親要素](../extensibility/parent-element.md)|省略可能です。 ボタンの親要素です。|  
|[Icon 要素](../extensibility/icon-element.md)|省略可能です。 ボタンに関連付けられているアイコン。|  
|[コマンドのフラグ要素](../extensibility/command-flag-element.md)|必須です。 ボタンの有効な CommandFlag 値は次のとおりです。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -[テキスト<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[文字列の要素](../extensibility/strings-element.md)|必須です。 子 [ButtonText 要素](../extensibility/buttontext-element.md) 定義する必要があります。|  
|注釈|省略可能なコメントです。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ボタン要素](../extensibility/buttons-element.md)|ボタン要素をグループ化します。|  
  
## <a name="example"></a>例  
 次の例では、.vsct ファイル内のボタンを定義します。  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>参照  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)