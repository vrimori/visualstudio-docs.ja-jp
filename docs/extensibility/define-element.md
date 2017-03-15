---
title: "要素を定義します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML スキーマ要素を定義します。"
  - "要素 (VSCT XML スキーマ) を定義します。"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 要素を定義します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

シンボルの名前と値のペアを定義します。 条件付きの属性では、このシンボルを評価できます。 詳細については、「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。 関連項目、 [シンボル要素](../extensibility/symbols-element.md)です。  
  
## 構文  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|必須です。 シンボルの名前。<br /><br /> 名前 \=「モード」|  
|値|必須です。 記号の値。<br /><br /> 値 \="Standard"|  
|状態|省略可能です。 詳細については、「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|統合開発環境 \(IDE\) に VSPackage を提供するコマンドを表すすべての要素を定義します。 たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックス。|  
  
## 使用例  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)