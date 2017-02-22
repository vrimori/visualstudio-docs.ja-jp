---
title: "Commands 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Commands 要素 (VSCT XML スキーマ)"
  - "コマンド、VSCT XML スキーマ要素"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Commands 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage のツールバーでコマンドのコレクションを表します。 コレクションでは、最大で 5 つのサブセクションを次のように必要: メニューのグループ、ボタン、コンボ、およびビットマップです。  
  
 各サブセクションの子要素、たとえば、\< メニュー \> は、GUID と数値識別子のペアである一意のコマンド ID によって識別されます。 GUID は、「コマンド セット」を識別し、論理的に関連するコマンドをグループ化するために使用します。 VSPackage では、他の Vspackage で定義されているコマンド Id との衝突を避けるために設定独自のコマンドを定義する必要があります。  
  
## 構文  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|package|コマンドは、VSPackage を識別する GUID。<br /><br /> たとえば、パッケージ化 \="guidVsPackage1Pkg"です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[メニュー要素](../extensibility/menus-element.md)|VSPackage を実装するすべてのメニューを定義します。|  
|[Groups 要素](../extensibility/groups-element.md)|VSPackage でのコマンド グループを定義するエントリが含まれています。|  
|[ボタン要素](../extensibility/buttons-element.md)|ボタン要素をグループ化します。|  
|[ビットマップ要素](../extensibility/bitmaps-element.md)|ビットマップの要素をグループ化します。|  
|[コンボ要素](../extensibility/combos-element.md)|コンボ要素をグループ化します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|VSPackage を IDE に提供するコマンドを表すすべての要素を定義します。 使用可能な要素は、メニュー項目、メニューのツールバー、およびコンボ ボックスにです。|  
  
## 使用例  
 次の例では、使用する方法、 [Commands Element](../extensibility/commands-element.md)です。  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)