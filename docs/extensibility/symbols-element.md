---
title: "シンボル要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "シンボル要素 (VSCT XML スキーマ)"
  - "VSCT XML スキーマの要素、シンボル"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# シンボル要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Guid およびその他の VSCT 要素によって使用されている Id を定義します。 アンマネージ コードは、この情報通常は、ヘッダー ファイルで指定されている [Extern 要素](../extensibility/extern-element.md)します。 マネージ コードがこの情報を定義する記号要素の子要素です。  
  
 既存の .cto ファイルから .vsct ファイルを作成する場合、シンボルはシンボル要素の子として生成されます。 詳細については、「[方法: 既存の .Cto ファイルから .Vsct ファイルを作成する](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)」を参照してください。  
  
 シンボル要素混同しないようにと、 [要素を定義します。](../extensibility/define-element.md), 、プリプロセッサで使用するための名前と値のペアを定義します。  
  
## 構文  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|なし||  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|GuidSymbol|GUID 記号を定義します。 GuidSymbol が 2 つの必須属性: 名前と値。 名前は、シンボルの名前と、値を文字列として GUID の値です。<br /><br /> 例: \< GuidSymbol 名前 \="guidVsPackage1Pkg"値 \="{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}"\/\>|  
|IDSymbol|シンボルを定義します。 IDSymbol が 2 つの必須属性: 名前と値。 名前は、シンボルの名前と値は、文字列としての記号の値。<br /><br /> 例: \< IDSymbol 名前 \="MyMenuGroup"値"0x1020"\=\/\>|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|.Vsct ファイルのルート要素です。|  
  
## 使用例  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)