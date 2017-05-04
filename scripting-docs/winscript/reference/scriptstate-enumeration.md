---
title: "SCRIPTSTATE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE 列挙型"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTSTATE 列挙型
スクリプト エンジンの状態を指定します。  この列挙体は [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)、[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) と [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) メソッドで使用されます。  
  
## 構文  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## 列挙値  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|スクリプトは `IPersist*` インターフェイスと [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) を使用して、作成されましたが、初期化されていません。|  
|SCRIPTSTATE\_INITIALIZED|スクリプトが初期化されますが、\(他のオブジェクトまたは沈降のイベントに接続します\) 実行またはコードを実行しません。  コードは [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) のメソッドを呼び出して実行を照会できます。|  
|SCRIPTSTATE\_STARTED|スクリプトは、コードを実行できますが、[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) のメソッドによって追加されたオブジェクトのイベントを沈めていません。|  
|SCRIPTSTATE\_CONNECTED|スクリプトは沈降のイベントに読み込まれ、接続されます。|  
|SCRIPTSTATE\_DISCONNECTED|読み込まれ、ありますが、ランタイム実行状態を沈降のイベントから一時的にドロップ スクリプトを作成します。|  
|SCRIPTSTATE\_CLOSED|スクリプトが閉じられました。  スクリプト エンジンは、ほとんどのメソッドのエラーを使用して返します。|  
  
## 参照  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)