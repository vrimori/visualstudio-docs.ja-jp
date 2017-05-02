---
title: "SOURCE_TEXT_ATTR 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR 定数"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# SOURCE_TEXT_ATTR 列挙型
ソース テキストに単一の文字の属性を記述します。  
  
## 構文  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|文字は、言語のキーワード、たとえば、VBScript のキーワード `While`の一部です。|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|文字はコメント ブロックの一部です。|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|文字は、コンパイルされた言語のソース テキストの一部ではありません。  たとえば、スクリプト ブロックを囲む HTML。|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|文字は、言語の演算子の一部です。  例: **\+**、算術演算子。|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|文字は、言語の数値定数の一部です。  たとえば、定数 3.14159。|  
|SOURCETEXT\_ATTR\_STRING|0x0020|文字は、言語の文字列定数の一部です。  たとえば、文字列「Hello World」。|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|文字は、関数のブロックの先頭を示します|  
  
## 解説  
 通常、`IDebugDocumentHost::GetScriptTextAttributes`、`IActiveScriptDebug::GetScriptletTextAttributes`と `IActiveScriptDebug::GetScriptTextAttributes` のメソッドは、文字ごとに 1 回のテキスト属性を返します:  
  
-   GETATTRTYPE\_DEPSCAN のフラグは、メソッドが SOURCETEXT\_ATTR\_IDENTIFIER と SOURCETEXT\_ATTR\_MEMBERLOOKUP のフラグを返す可能性がある場合、設定  
  
-   GETATTRFLAG\_THIS のフラグは、メソッドが SOURCETEXT\_ATTR\_THIS のフラグを返す可能性がある場合、設定  
  
-   GETATTRFLAG\_HUMANTEXT のフラグは、メソッドが SOURCETEXT\_ATTR\_HUMANTEXT のフラグを返す可能性がある場合、設定されます。  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)