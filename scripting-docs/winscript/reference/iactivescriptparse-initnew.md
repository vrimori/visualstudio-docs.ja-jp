---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
スクリプト エンジンが初期化されます。  
  
## 構文  
  
```  
HRESULT InitNew(void);  
```  
  
## 戻り値  
 エラーは、初期化時に発生する、または `E_FAIL` が成功した場合 `S_OK` 返します。  
  
## 解説  
 スクリプト エンジンが使用する前に、次のメソッドのうち 1 つがを呼び出す必要があります: `IPersist*::Load`、`IPersist*::InitNew`、または `IActiveScriptParse::InitNew`。  このメソッドのセマンティクスはこのメソッドは、スクリプト エンジンを自身を初期化するように指示 `IPersistStreamInit::InitNew`ことと同じです。  `IPersist*::InitNew` か `IActiveScriptParse::InitNew` と `IPersist*::Load`両方を呼び出す場合は、が有効でない有効な `IPersist*::InitNew`、`IActiveScriptParse::InitNew`、または `IPersist*::Load` を複数回呼び出すためにあることに注意してください。  
  
## 参照  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)