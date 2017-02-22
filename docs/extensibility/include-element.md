---
title: "要素が含まれます | Microsoft Docs"
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
  - "Include"
helpviewer_keywords: 
  - "Include 要素 (VSCT XML スキーマ)"
  - "VSCT XML スキーマ要素を含める"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 要素が含まれます
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Include 要素に存在するファイルの指定に、指定された現在のファイルに挿入するためのパスを含めます。  すべてのシンボルと定義されている型はコンパイルの結果の一部になります。  
  
## 構文  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|href|必須です。 ヘッダー ファイルのパス:<br /><br /> href\="stdidcmd.h"|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
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
<Include href="PackagePlacements.vsct"/>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)