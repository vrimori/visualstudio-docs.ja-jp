---
title: "SOURCE_TEXT_ATTR 列挙 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR 列挙型
ソース テキストの単一文字の属性を記述します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|値|説明|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|言語キーワード、VBScript キーワードなどの一部である文字`While`です。|  
|SOURCETEXT_ATTR_COMMENT|0x0002|文字は、コメント ブロックの一部です。|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|文字は、コンパイル済みの言語のソース テキストの一部ではありません。 たとえば、スクリプト ブロックを囲む HTML。|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|文字は、言語の演算子の一部です。 例: 算術演算子 **+**です。|  
|SOURCETEXT_ATTR_NUMBER|0x0010|文字は、言語の数値定数の一部です。  たとえば、定数 3.14159 です。|  
|SOURCETEXT_ATTR_STRING|0x0020|文字は、言語の文字列定数の一部です。 たとえば、文字列"Hello World"。|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|文字が関数ブロックの開始を示します|  
  
## <a name="remarks"></a>コメント  
 通常、 `IDebugDocumentHost::GetScriptTextAttributes`、 `IActiveScriptDebug::GetScriptletTextAttributes`、および`IActiveScriptDebug::GetScriptTextAttributes`しない限り、メソッドが 1 文字の 1 つのテキスト属性を返します。  
  
-   GETATTRTYPE_DEPSCAN フラグを設定すると、メソッドが、SOURCETEXT_ATTR_IDENTIFIER と SOURCETEXT_ATTR_MEMBERLOOKUP フラグに戻る場合  
  
-   GETATTRFLAG_THIS フラグが設定されている場合、メソッドが SOURCETEXT_ATTR_THIS フラグを返す可能性があります。  
  
-   GETATTRFLAG_HUMANTEXT フラグが設定されている場合、メソッドが SOURCETEXT_ATTR_HUMANTEXT フラグを返す可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)