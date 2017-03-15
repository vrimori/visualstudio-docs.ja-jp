---
title: "C# および C++ の VSCT サンプル | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT ファイル、サンプル"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# C# および C++ の VSCT サンプル
VSCT はコマンドを定義する新しい方法になっています。  これが原因で変更は VSCT の例はC\# および C\+\+ におけるコンパイルに発生します。  コマンド外部ファイルで C\+\+ で .vsct ファイルのシンボル セクションではC\# で定義されています。  
  
## コマンドの定義  
  
### C\+\+ の外部ファイル  
 C\+\+ のサンプルではVSCT コンパイラはコマンドの定義内で使用される定数を定義する外部ファイルが含まれています。  このファイルはコマンドの定義で定数を定義する方法はにより .vsct ファイル内の `Extern` タグを追加し`href` の属性内の外部ファイル参照の名前を指定します。  これらのファイルは次のとおりです :  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 C. .vsct C\+\+ ファイルから次のスニペットではこれらのファイルを含める方法を示します :  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### C\# のシンボル  
 C\# サンプルでは.vsct ファイルはコマンドを定義するファイルのセクションで `Symbols` 自体があります。  方法から C\# の縦線の .vsct ファイルのシンボル定義はコマンドの表に要素 ID によって決まります。  次はに関連付けられたコマンドおよび定数を指定する C\# .vsct ファイルのスニペットです :  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## ビットマップを埋め込みます。  
  
### C\#  
 C\+\+ および C\# の CTO なバイナリのビットマップがディスク上の外部に格納されます。  ビットマップ ID はで定義にビットマップに GUID の属性ビットマップを含むビットマップを `resID` の属性の定義とボタン \(`usedList` の属性\) 内で使用される要素の数値 ID を指定するように定義されます。  この宣言の重要な側面は要素 ID がビットマップの実際のインデックスである \(1 から始まる\) があるビットマップを指定することです。  
  
 次の例ではビットマップを 1 個の要素だけが含まれていることがあります。  この要素の ID は guidMenuAndCommandsCmdSet として定義されています : bmpArrow ためbmpArrow は 1. で定義されている必要があります。  またビットマップの宣言です。  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)