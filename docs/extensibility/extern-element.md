---
title: "Extern 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Extern"
helpviewer_keywords: 
  - "Extern、VSCT XML スキーマ要素"
  - "Extern 要素 (VSCT XML スキーマ)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Extern 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Extern 要素は、コンパイル時に .vsct ファイルとマージする外部ヘッダー \(.h\) ファイルを参照します。 VSCT コンパイラに削除するかによって参照されるインクルード パスにファイルをマージする必要があります、 [要素が含まれます](../extensibility/include-element.md)です。 ファイルには、その他の .vsct ファイルまたは C\+\+ ヘッダー ファイルを指定できます。  
  
 形式のヘッダー ファイルの定義にする必要があります"\# \[シンボル\] \[Value\] define"、値は、以前に定義されている場合に別のシンボルを指定できます。 コマンドの項目の条件付きステートメントでは、定義を使用することがあります。 実際に使用される任意の記号は破棄されます。  
  
 CommandTable Element  
Extern Element  
  
## 構文  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|href|必須です。 ヘッダー ファイルのパス:<br /><br /> href\="stdidcmd.h"|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
|language|省略可能です。 すべての既定の言語 [\< 文字列 \>](../extensibility/strings-element.md) コマンド テーブル内の要素。<br /><br /> 言語 \="英語\-us"|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|なし。|なし。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|すべてのコマンドを表す要素の定義: メニュー項目、メニューのツールバー、およびコンボ ボックスは、\-VSPackage を IDE に提供します。|  
  
## 使用例  
  
```  
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)