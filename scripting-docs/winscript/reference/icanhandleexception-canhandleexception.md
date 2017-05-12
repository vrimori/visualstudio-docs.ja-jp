---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
スクリプト エンジンの呼び出し元が指定された例外を処理できるかどうかを判定します。  
  
## 構文  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### パラメーター  
 `pExcepInfo`  
 \[入力\]例外ハンドラーがない報告される情報を含む `EXCEPINFO` の構造体へのポインター。  
  
 `pvar`  
 \[入力\]値は `throw` のステートメントによってスローされた値などの例外を除き、関連付けられた  このパラメーターは、`NULL` の場合もあります。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|呼び出し元は例外を処理できます|  
|`E_FAIL`|呼び出し元がその例外を処理できません。|  
  
## 解説  
 `IDispatchEx::InvokeEx`の呼び出し、または同様のメソッドが例外で、なった場合は、スクリプト エンジンは `ICanHandleException` のインターフェイスをサポートすることを確認し、例外を処理できることを示しますスクリプトの呼び出し元のチェーンの呼び出し元が。  呼び出し元が例外を処理できない場合、スクリプト エンジンが停止します。  
  
## 参照  
 [ICanHandleException インターフェイス](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)