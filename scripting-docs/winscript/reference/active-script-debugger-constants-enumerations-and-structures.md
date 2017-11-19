---
title: "アクティブ スクリプト デバッガーの定数、列挙型、および構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bd41fe91fdf030b957d800248343198f2617018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>アクティブ スクリプト デバッガーの定数、列挙型、および構造体
次の定数、列挙型、および構造体は、アクティブ デバッグ インターフェイスによって使用されます。  
  
## <a name="constants-enumerations-and-structures"></a>定数、列挙型、および構造体  
  
|定数|説明|  
|---------------|-----------------|  
|[APPBREAKFLAGS 定数](../../winscript/reference/appbreakflags-enumeration.md)|アプリケーションおよびスレッドの現在のデバッグ状態を示します。|  
|[DEBUG_TEXT 定数](../../winscript/reference/debug-text-constants.md)|オプション フラグの中に使用される[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)です。|  
|[TEXT_DOC_ATTR 定数](../../winscript/reference/text-doc-attr-constants.md)|ドキュメントの属性を記述します。|  
  
|列挙|説明|  
|------------------|-----------------|  
|[APPBREAKFLAGS 定数](../../winscript/reference/appbreakflags-enumeration.md)|アプリケーションおよびスレッドの現在のデバッグ状態を示します。|  
|[APPLICATION_NODE_EVENT_FILTER 列挙型](../../winscript/reference/application-node-event-filter-enumeration.md)|フィルターで除外するノードを示します。|  
|[BREAKPOINT_STATE 列挙型](../../winscript/reference/breakpoint-state-enumeration.md)|ブレークポイントの状態を示します。|  
|[BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)|中断の原因を示します。|  
|[BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)|ブレークポイントから継続する方法について記述します。|  
|[DOCUMENTNAMETYPE 列挙型](../../winscript/reference/documentnametype-enumeration.md)|ドキュメント用に取得する型を記述します。|  
|[ERRORRESUMEACTION 列挙型](../../winscript/reference/errorresumeaction-enumeration.md)|ランタイム エラーから継続する方法について記述します。|  
|[JS_PROPERTY_ATTRIBUTES 列挙型](../../winscript/reference/js-property-attributes-enumeration.md)|プロパティの属性を指定します。|  
|[JS_PROPERTY_MEMBERS 列挙型](../../winscript/reference/js-property-members-enumeration.md)|オブジェクトのメンバーの要求で返される情報の種類を指定するフラグ。|  
|[JsDebugReadMemoryFlags 列挙型](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|メモリの読み取り時の動作を指定するフラグ。|  
|[SCRIPT_DEBUGGER_OPTIONS 列挙型](../../winscript/reference/script-debugger-options-enumeration.md)|アタッチされたデバッガーに適用する一連のオプションまたは機能を示します。|  
|[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列挙型](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|スローされた例外の種類を示します。|  
|[SOURCE_TEXT_ATTR 定数](../../winscript/reference/source-text-attr-enumeration.md)|ソース テキストの単一文字の属性を記述します。|  
  
|構造体|説明|  
|----------------|-----------------|  
|[DebugStackFrameDescriptor 構造体](../../winscript/reference/debugstackframedescriptor-structure.md)|スタック フレームを列挙し、同じスレッドの複数の列挙型からの出力をマージします。|  
|[JS_NATIVE_FRAME 構造体](../../winscript/reference/js-native-frame-structure.md)|スタック フレームを表します。|  
|[JsDebugPropertyInfo 構造体](../../winscript/reference/jsdebugpropertyinfo-structure.md)|プロパティに関する情報を指定します。|  
|[TEXT_DOCUMENT_ARRAY 構造体](../../winscript/reference/text-document-array-structure.md)|一連のドキュメントを提供します。|