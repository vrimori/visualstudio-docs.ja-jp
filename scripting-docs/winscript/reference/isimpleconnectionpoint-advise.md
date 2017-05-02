---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
単純なコネクション ポイント オブジェクトとクライアント シンク間の接続を確立します。  
  
## 構文  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### パラメーター  
 `pdisp`  
 \[入力\]クライアントの `IDispatch` インターフェイスへのポインターがアドバイズ シンクします。  クライアント シンクは単純な接続ポイントのビープを受け取ります。  
  
 `pdwCookie`  
 \[出力\]この接続を区別する返されるトークンへのポインター。  呼び出し元は `ISimpleConnectionPoint::Unadvise` のメソッドに渡して接続を削除するには、このトークンを使用します。  接続が正常に確立されていない場合は、この値はゼロです。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 この方法は、単純なコネクション ポイント オブジェクトとクライアント シンク間の接続を確立します。  
  
## 参照  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)